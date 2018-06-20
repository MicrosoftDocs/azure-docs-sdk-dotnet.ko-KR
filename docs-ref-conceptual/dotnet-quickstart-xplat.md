---
title: .NET Core를 사용하여 명령줄에서 Azure에 배포
description: 이 문서에서는 명령줄 도구를 사용하여 Azure App Service에 ASP.NET Core 응용 프로그램을 배포하는 방법을 설명합니다.
keywords: Azure .NET, SDK, Azure .NET API 참조, Azure .NET 클래스 라이브러리
author: camsoper
manager: douge
ms.author: casoper
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.openlocfilehash: 8371c304681ff88cba6f1cc3ba0d1caef836d609
ms.sourcegitcommit: e1a0e91988bb849c75e9583a80e3e6d712083785
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2018
ms.locfileid: "31005880"
---
# <a name="deploy-to-azure-from-the-command-line-with-net-core"></a>.NET Core를 사용하여 명령줄에서 Azure에 배포

이 자습서에서는 .NET Core를 사용하여 Microsoft Azure 응용 프로그램을 빌드하고 배포하는 과정을 안내합니다.  완료되면 웹 기반 할 일 응용 프로그램이 ASP.NET MVC Core로 빌드되고, Azure 웹앱으로 호스팅되고, Azure Cosmos DB를 사용하여 데이터를 저장합니다.

## <a name="prerequisites"></a>필수 조건

* [Microsoft Azure 구독](https://azure.microsoft.com/free/)
* [.NET Core](https://www.microsoft.com/net/download/core)(선택 사항)
* [Azure CLI 2.0](/cli/azure/install-az-cli2)(선택 사항)
* [Git](https://www.git-scm.com/) 명령줄 클라이언트(선택 사항)

[Azure Cloud Shell](/azure/cloud-shell/)에는 이 자습서에 대한 선택적 필수 구성 요소가 모두 사전 설치되어 있습니다.  자습서를 로컬로 실행하려면 위의 선택적 구성 요소만 설치하면 됩니다.  Cloud Shell을 빠르게 시작하려면 아래 코드 블록의 오른쪽 위에 있는 **사용해 보세요** 단추를 클릭합니다.

## <a name="create-an-azure-cosmos-db-account"></a>Azure Cosmos DB 계정 만들기

Azure Cosmos DB는 이 자습서의 데이터 저장에 사용되므로 계정을 만들어야 합니다.  이 스크립트를 로컬 또는 Cloud Shell에서 실행하여 Azure Cosmos DB SQL API 계정을 만듭니다.

```azurecli-interactive
# Create the DotNetAzureTutorial resource group
az group create --name DotNetAzureTutorial --location EastUS

# Generate a unique name for the account
let randomNum=$RANDOM*$RANDOM
cosmosdbname=dotnettutorial$randomNum

# Create the Azure Cosmos DB account
az cosmosdb create --name $cosmosdbname --resource-group DotNetAzureTutorial

# Retrieve the endpoint and key (you'll need these later)
cosmosEndpoint=$(az cosmosdb show -n $cosmosdbname -g DotNetAzureTutorial --query [documentEndpoint] -o tsv)
cosmosAuthKey=$(az cosmosdb list-keys -n $cosmosdbname -g DotNetAzureTutorial --query [primaryMasterKey] -o tsv)

```

## <a name="download-and-configure-the-application"></a>응용 프로그램 다운로드 및 구성

배포하려는 응용 프로그램은 Azure Cosmos DB 클라이언트 라이브러리를 사용하는 ASP.NET MVC Core를 사용하여 작성된 [간단한 할 일 앱(영문)](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/)입니다.  이제 이 자습서의 코드를 가져오고 Azure Cosmos DB 정보로 이 코드를 구성합니다.

```azurecli-interactive
# Get the code from GitHub
git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart

# Change the working directory
cd dotnet-cosmosdb-quickstart

# Replace authKey and endpoint values in appsettings.json
sed -i "s|AUTHKEYVALUE|$cosmosAuthKey|g" appsettings.json
sed -i "s|ENDPOINTVALUE|$cosmosEndpoint|g" appsettings.json

# Now commit your changes to the local Git repository.
git commit -a -m "Modified settings"

```

> [!NOTE]
> 이전에 이 환경에서 `git commit`을 실행한 적이 없으면 ID를 설정하라는 메시지가 표시될 수 있습니다. 이 경우 화면의 지침에 따라 `git commit` 명령을 다시 실행하세요.

NuGet 패키지를 복원하고 응용 프로그램을 빌드합니다.

```azurecli-interactive
dotnet restore
dotnet build
```

> [!TIP]
> 자신의 컴퓨터에서 도구를 사용하는 경우 `dotnet run`을 실행하고 표시된 `localhost` 주소로 이동하여 응용 프로그램을 테스트할 수 있습니다.  그러나 Cloud Shell에서는 이 주소로 이동할 수 없습니다.  

## <a name="configure-azure-app-service-and-deploy-the-web-app"></a>Azure App Service를 구성하고 웹앱을 배포합니다.

웹 응용 프로그램을 성공적으로 다운로드하고 빌드했고, Azure Web App으로 배포할 준비가 되었습니다.  이제 Web App 리소스를 만들어 보겠습니다.

```azurecli-interactive
# Generate a unique Web App name
let randomNum=$RANDOM*$RANDOM
webappname=todoApp$randomNum

# Create an App Service plan.
az appservice plan create --name $webappname --resource-group DotNetAzureTutorial --sku FREE

# Create the Web App
az webapp create --name $webappname --resource-group DotNetAzureTutorial --plan $webappname

```

배포하려면 먼저 계정 수준 배포 자격 증명을 설정해야 합니다.  아래 스크립트를 사용하여 사용자 이름과 암호에 대한 고유 값을 포함합니다.

```azurecli-interactive
az webapp deployment user set --user-name <desired user name> --password <desired password>
```

마지막으로 Azure에 응용 프로그램을 배포합니다.  위에서 만든 암호를 입력하라는 메시지가 표시됩니다.

```azurecli-interactive
# Get the Git deployment URL
giturl=$(az webapp deployment source config-local-git -n $webappname -g DotNetAzureTutorial --query [url] -o tsv)

# Add the URL as a Git remote repository
git remote add azure $giturl

# Push the local repository to the remote
git push azure master
```

응용 프로그램이 원격으로 빌드되어 배포됩니다.  `https://<web app name>.azurewebsites.net`으로 이동하여 응용 프로그램을 테스트합니다.  콘솔에 주소를 표시하려면 다음 예제를 사용합니다.

```azurecli-interactive
az webapp show -n $webappname -g DotNetAzureTutorial --query defaultHostName -o tsv
```

이제 **새로 만들기**를 클릭하여 할 일 목록에 새 항목을 추가할 수 있습니다.

![완성된 앱](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a>정리

앱을 테스트하고 코드 및 리소스를 검사한 후에는 리소스 그룹을 삭제하여 웹앱 및 Azure Cosmos DB 계정을 삭제할 수 있습니다.

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a>다음 단계

* [Azure Active Directory를 사용하여 ASP.NET 웹 응용 프로그램에서 인증](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [Azure SQL Database를 사용하여 Azure 웹앱 빌드](/azure/app-service-web/web-sites-dotnet-get-started)
* [Azure Storage를 통해 .NET 샘플 응용 프로그램 사용해보기](/azure/storage/storage-samples-dotnet)


