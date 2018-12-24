---
title: .NET Core를 사용하여 명령줄에서 Azure에 배포
description: 이 문서에서는 명령줄 도구를 사용하여 Azure App Service에 ASP.NET Core 애플리케이션을 배포하는 방법을 설명합니다.
ms.date: 06/20/2017
ms.openlocfilehash: a29f5474dcfedc6f8d044f09ad4d54c5be6a371f
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190496"
---
# <a name="deploy-to-azure-from-the-command-line-with-net-core"></a><span data-ttu-id="95d5e-103">.NET Core를 사용하여 명령줄에서 Azure에 배포</span><span class="sxs-lookup"><span data-stu-id="95d5e-103">Deploy to Azure from the command line with .NET Core</span></span>

<span data-ttu-id="95d5e-104">이 자습서에서는 .NET Core를 사용하여 Microsoft Azure 응용 프로그램을 빌드하고 배포하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-104">This tutorial will walk you through building and deploying a Microsoft Azure application using .NET Core.</span></span>  <span data-ttu-id="95d5e-105">완료되면 웹 기반 할 일 응용 프로그램이 ASP.NET MVC Core로 빌드되고, Azure 웹앱으로 호스팅되고, Azure Cosmos DB를 사용하여 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-105">When finished, you'll have a web-based to-do application built in ASP.NET MVC Core, hosted as an Azure Web App, and using Azure Cosmos DB for data storage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95d5e-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="95d5e-106">Prerequisites</span></span>

* <span data-ttu-id="95d5e-107">[Microsoft Azure 구독](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="95d5e-107">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>
* <span data-ttu-id="95d5e-108">[.NET Core](https://www.microsoft.com/net/download/core)(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="95d5e-108">[.NET Core](https://www.microsoft.com/net/download/core) (optional)</span></span>
* <span data-ttu-id="95d5e-109">[Azure CLI 2.0](/cli/azure/install-az-cli2)(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="95d5e-109">[Azure CLI 2.0](/cli/azure/install-az-cli2) (optional)</span></span>
* <span data-ttu-id="95d5e-110">[Git](https://www.git-scm.com/) 명령줄 클라이언트(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="95d5e-110">[Git](https://www.git-scm.com/) command line client (optional)</span></span>

<span data-ttu-id="95d5e-111">[Azure Cloud Shell](/azure/cloud-shell/)에는 이 자습서에 대한 선택적 필수 구성 요소가 모두 사전 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-111">The [Azure Cloud Shell](/azure/cloud-shell/) has all of the optional prerequisites for this tutorial preinstalled.</span></span>  <span data-ttu-id="95d5e-112">자습서를 로컬로 실행하려면 위의 선택적 구성 요소만 설치하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-112">You only need to install the optional components above if you wish to run the tutorial locally.</span></span>  <span data-ttu-id="95d5e-113">Cloud Shell을 빠르게 시작하려면 아래 코드 블록의 오른쪽 위에 있는 **사용해 보세요** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-113">To quickly launch the Cloud Shell, just click the **Try it** button in the top-right of any of the below code blocks.</span></span>

## <a name="create-an-azure-cosmos-db-account"></a><span data-ttu-id="95d5e-114">Azure Cosmos DB 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="95d5e-114">Create an Azure Cosmos DB account</span></span>

<span data-ttu-id="95d5e-115">Azure Cosmos DB는 이 자습서의 데이터 저장에 사용되므로 계정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-115">Azure Cosmos DB is used for data storage in this tutorial, so you'll need to create an account.</span></span>  <span data-ttu-id="95d5e-116">이 스크립트를 로컬 또는 Cloud Shell에서 실행하여 Azure Cosmos DB SQL API 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-116">Run this script locally or in the Cloud Shell to create an Azure Cosmos DB SQL API account.</span></span>

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

## <a name="download-and-configure-the-application"></a><span data-ttu-id="95d5e-117">응용 프로그램 다운로드 및 구성</span><span class="sxs-lookup"><span data-stu-id="95d5e-117">Download and configure the application</span></span>

<span data-ttu-id="95d5e-118">배포하려는 응용 프로그램은 Azure Cosmos DB 클라이언트 라이브러리를 사용하는 ASP.NET MVC Core를 사용하여 작성된 [간단한 할 일 앱(영문)](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/)입니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-118">The application you're going to deploy is a [simple to-do app](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/) written using ASP.NET MVC Core using the Azure Cosmos DB client libraries.</span></span>  <span data-ttu-id="95d5e-119">이제 이 자습서의 코드를 가져오고 Azure Cosmos DB 정보로 이 코드를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-119">Now you'll get the code for this tutorial and configure it with your Azure Cosmos DB information.</span></span>

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
> <span data-ttu-id="95d5e-120">이전에 이 환경에서 `git commit`을 실행한 적이 없으면 ID를 설정하라는 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-120">If you've never run `git commit` in this environment before, you may be prompted to set your identity.</span></span> <span data-ttu-id="95d5e-121">이 경우 화면의 지침에 따라 `git commit` 명령을 다시 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="95d5e-121">Follow the on-screen instructions and then re-run the `git commit` command.</span></span>

<span data-ttu-id="95d5e-122">NuGet 패키지를 복원하고 응용 프로그램을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-122">Restore the NuGet packages and build the application.</span></span>

```azurecli-interactive
dotnet restore
dotnet build
```

> [!TIP]
> <span data-ttu-id="95d5e-123">자신의 컴퓨터에서 도구를 사용하는 경우 `dotnet run`을 실행하고 표시된 `localhost` 주소로 이동하여 응용 프로그램을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-123">If you are using the tools on your own machine, you can test the application by running `dotnet run` and browsing to the displayed `localhost` address.</span></span>  <span data-ttu-id="95d5e-124">그러나 Cloud Shell에서는 이 주소로 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-124">You are not able to browse to this address in the Cloud Shell, however.</span></span>  

## <a name="configure-azure-app-service-and-deploy-the-web-app"></a><span data-ttu-id="95d5e-125">Azure App Service를 구성하고 웹앱을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-125">Configure Azure App Service and deploy the web app</span></span>

<span data-ttu-id="95d5e-126">웹 응용 프로그램을 성공적으로 다운로드하고 빌드했고, Azure Web App으로 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-126">You've successfully downloaded and built the web application, and you're ready to deploy it as an Azure Web App.</span></span>  <span data-ttu-id="95d5e-127">이제 Web App 리소스를 만들어 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-127">You'll start by creating the Web App resource.</span></span>

```azurecli-interactive
# Generate a unique Web App name
let randomNum=$RANDOM*$RANDOM
webappname=todoApp$randomNum

# Create an App Service plan.
az appservice plan create --name $webappname --resource-group DotNetAzureTutorial --sku FREE

# Create the Web App
az webapp create --name $webappname --resource-group DotNetAzureTutorial --plan $webappname

```

<span data-ttu-id="95d5e-128">배포하려면 먼저 계정 수준 배포 자격 증명을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-128">Before you deploy, you need to set the account-level deployment credentials.</span></span>  <span data-ttu-id="95d5e-129">아래 스크립트를 사용하여 사용자 이름과 암호에 대한 고유 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-129">Use the script below, making sure to include your own values for the user name and password.</span></span>

```azurecli-interactive
az webapp deployment user set --user-name <desired user name> --password <desired password>
```

<span data-ttu-id="95d5e-130">마지막으로 Azure에 응용 프로그램을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-130">Finally, deploy the application to Azure.</span></span>  <span data-ttu-id="95d5e-131">위에서 만든 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-131">You will be prompted for the password you created above.</span></span>

```azurecli-interactive
# Get the Git deployment URL
giturl=$(az webapp deployment source config-local-git -n $webappname -g DotNetAzureTutorial --query [url] -o tsv)

# Add the URL as a Git remote repository
git remote add azure $giturl

# Push the local repository to the remote
git push azure master
```

<span data-ttu-id="95d5e-132">응용 프로그램이 원격으로 빌드되어 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-132">The application will be built remotely and deployed.</span></span>  <span data-ttu-id="95d5e-133">`https://<web app name>.azurewebsites.net`으로 이동하여 응용 프로그램을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-133">Test the application by browsing to `https://<web app name>.azurewebsites.net`.</span></span>  <span data-ttu-id="95d5e-134">콘솔에 주소를 표시하려면 다음 예제를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-134">To display the address in the console, use the following:</span></span>

```azurecli-interactive
az webapp show -n $webappname -g DotNetAzureTutorial --query defaultHostName -o tsv
```

<span data-ttu-id="95d5e-135">이제 **새로 만들기**를 클릭하여 할 일 목록에 새 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-135">You can add new items to the to-do list by clicking **Create New**.</span></span>

![완성된 앱](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a><span data-ttu-id="95d5e-137">정리</span><span class="sxs-lookup"><span data-stu-id="95d5e-137">Clean up</span></span>

<span data-ttu-id="95d5e-138">앱을 테스트하고 코드 및 리소스를 검사한 후에는 리소스 그룹을 삭제하여 웹앱 및 Azure Cosmos DB 계정을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95d5e-138">When you're done testing the app and inspecting the code and resources, you can delete the Web App and Azure Cosmos DB account by deleting the resource group.</span></span>

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a><span data-ttu-id="95d5e-139">다음 단계</span><span class="sxs-lookup"><span data-stu-id="95d5e-139">Next steps</span></span>

* [<span data-ttu-id="95d5e-140">Azure Active Directory를 사용하여 ASP.NET 웹 응용 프로그램에서 인증</span><span class="sxs-lookup"><span data-stu-id="95d5e-140">Use Azure Active Directory for authentication in an ASP.NET web application</span></span>](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [<span data-ttu-id="95d5e-141">Azure SQL Database를 사용하여 Azure 웹앱 빌드</span><span class="sxs-lookup"><span data-stu-id="95d5e-141">Build an Azure Web App using Azure SQL Database</span></span>](/azure/app-service-web/web-sites-dotnet-get-started)
* [<span data-ttu-id="95d5e-142">Azure Storage를 통해 .NET 샘플 응용 프로그램 사용해보기</span><span class="sxs-lookup"><span data-stu-id="95d5e-142">Try a .NET sample application with Azure Storage</span></span>](/azure/storage/storage-samples-dotnet)


