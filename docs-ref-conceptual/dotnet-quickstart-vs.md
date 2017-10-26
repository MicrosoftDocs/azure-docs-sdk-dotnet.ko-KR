---
title: "Azure 개발자용 .NET"
description: "Azure 개발자용 .NET"
keywords: "Azure .NET, SDK, Azure .NET API 참조, Azure .NET 클래스 라이브러리"
author: camsoper
manager: douge
ms.author: casoper
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.assetid: 
ms.openlocfilehash: eb7aa364cae9deea4ed2052eefdbd51c85379afa
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
---
# <a name="get-started-with-net-for-azure-developers"></a>Azure 개발자용 .NET 시작

이 자습서에서는 Visual Studio 및 .NET을 사용하여 Microsoft Azure 응용 프로그램을 빌드하고 배포하는 과정을 안내합니다.  완료되면 웹 기반 할 일 응용 프로그램이 ASP.NET MVC Core로 빌드되고, Azure 웹앱으로 호스팅되고, Azure CosmosDB를 사용하여 데이터를 저장합니다.

## <a name="prerequisites"></a>필수 조건

* [Visual Studio 2017](https://www.visualstudio.com/downloads/)
* [Microsoft Azure 구독](https://azure.microsoft.com/free/)

## <a name="create-a-cosmosdb-account"></a>CosmosDB 계정 만들기

CosmosDB는 이 자습서의 데이터 저장에 사용되므로 계정을 만들어야 합니다.  이 스크립트를 로컬 또는 Cloud Shell에서 실행하여 Azure CosmosDB DocumentDB API 계정을 만듭니다.  아래 코드 블록에서 **실습** 단추를 클릭하여 [Azure Cloud Shell](/azure/cloud-shell/)을 시작하고 스크립트 블록을 셸로 복사/붙여넣습니다.

```azurecli-interactive
# Create the DotNetAzureTutorial resource group
az group create --name DotNetAzureTutorial --location EastUS

# Generate a unique name for the account
let randomNum=$RANDOM*$RANDOM
cosmosdbname=dotnettutorial$randomNum

# Create the CosmosDB account
az cosmosdb create --name $cosmosdbname --resource-group DotNetAzureTutorial

# Retrieve the endpoint and key (you'll need these later)
cosmosEndpoint=$(az cosmosdb show -n $cosmosdbname -g DotNetAzureTutorial --query [documentEndpoint] -o tsv)
cosmosAuthKey=$(az cosmosdb list-keys -n $cosmosdbname -g DotNetAzureTutorial --query [primaryMasterKey] -o tsv)
printf "\n\nauthKey: $cosmosAuthKey\nendpoint: $cosmosEndpoint\n\n"

# Done!

```

표시된 **authKey** 및 **끝점**을 적어둡니다. 

## <a name="downloading-and-running-the-application"></a>응용 프로그램 다운로드 및 실행

이 연습에 대한 샘플 코드를 다운로드하고 CosmosDB 계정을 살펴보겠습니다.

1. 샘플 코드를 다운로드합니다.  [GitHub에서 가져](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/)오거나 [git 명령줄 클라이언트](https://git-scm.com/)가 있는 경우 다음 명령을 사용하여 로컬 컴퓨터에 복제합니다.

    ```cmd
    git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart
    ```

2. Visual Studio에서 **todo.csproj**를 엽니다.

3. 웹 프로젝트에서 **appsettings.json**을 엽니다.  다음 줄을 찾습니다.

    ```json
    "authKey": "AUTHKEYVALUE",
    "endpoint": "ENDPOINTVALUE",
    ```
    **AUTHKEYVALUE** 및 **ENDPOINTVALUE**를 앞에서 기록한 값으로 바꿉니다.

4. **F5** 키를 눌러 프로젝트의 NuGet 패키지를 복원하고, 프로젝트를 빌드하고, 로컬로 실행합니다.

웹 응용 프로그램은 브라우저에서 로컬로 실행해야 합니다.  이제 **새로 만들기**를 클릭하여 할 일 목록에 새 항목을 추가할 수 있습니다.  응용 프로그램에 입력하는 데이터는 CosmosDB 계정에 저장됩니다.  [Azure Portal에서 데이터를 볼](/azure/documentdb/documentdb-view-json-document-explorer) 수 있습니다.

## <a name="deploying-the-application-as-an-azure-web-app"></a>Azure 웹앱으로 응용 프로그램 배포

DocumentDB와 같은 Azure 서비스를 사용하는 응용 프로그램을 성공적으로 빌드했습니다.  다음으로, 웹 응용 프로그램을 클라우드에 배포합니다.

> [!IMPORTANT]
> Azure 구독이 연결된 동일한 계정으로 Visual Studio에 로그인해야 합니다.

1. Visual Studio 솔루션 탐색기에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭하고 **게시...**를 선택합니다.

2. 게시 대화 상자를 사용하여 **Microsoft Azure App Service**, **새로 만들기**를 차례로 선택한 다음 **게시**를 클릭합니다.

3. 다음과 같이 App Service 만들기 대화 상자를 완료합니다.

    * 고유한 **웹앱 이름**을 입력합니다.  이는 앱에 대한 URL의 일부가 될 수 있습니다.
    * 배포하는 Azure **구독**을 선택합니다.  이전에 Cloud Shell에 로그인할 때 사용한 동일한 구독을 사용합니다.
    * 웹 응용 프로그램의 **리소스 그룹**에 대한 *DotNetAzureTutorial*을 선택합니다.
    * **App Service 계획**을 선택하거나 만들어 응용 프로그램의 가격을 책정합니다.  다음은 [App Service 계획에 대한 자세한 내용](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)입니다.

4. **만들기**를 클릭하여 응용 프로그램을 배포합니다.  배포가 완료되면 배포된 응용 프로그램과 함께 브라우저가 열립니다.

![완성된 앱](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a>정리

앱을 테스트하고 코드 및 리소스를 검사한 후에는 리소스 그룹을 삭제하여 웹앱 및 CosmosDB 계정을 삭제할 수 있습니다. Cloud Shell에서

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a>다음 단계

* [Azure Active Directory를 사용하여 ASP.NET 웹 응용 프로그램에서 인증](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [Azure SQL Database를 사용하여 Azure 웹앱 빌드](/azure/app-service-web/web-sites-dotnet-get-started)
* [Azure Storage를 통해 .NET 샘플 응용 프로그램 사용해보기](/azure/storage/storage-samples-dotnet)


