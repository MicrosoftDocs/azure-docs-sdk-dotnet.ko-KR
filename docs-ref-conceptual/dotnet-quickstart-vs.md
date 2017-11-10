---
title: "Visual Studio에서 Azure에 배포"
description: "이 자습서에서는 Visual Studio 및 .NET을 사용하여 Microsoft Azure 응용 프로그램을 빌드하고 배포하는 과정을 안내합니다."
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
ms.openlocfilehash: 0f8e3e5ea1ef5cde239b2d8ebbc9fe75dd978cb1
ms.sourcegitcommit: c630918c9e17f5e3c6d4f28fe740c041f60b1e66
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2017
---
# <a name="deploy-to-azure-from-visual-studio"></a><span data-ttu-id="26385-104">Visual Studio에서 Azure에 배포</span><span class="sxs-lookup"><span data-stu-id="26385-104">Deploy to Azure from Visual Studio</span></span>

<span data-ttu-id="26385-105">이 자습서에서는 Visual Studio 및 .NET을 사용하여 Microsoft Azure 응용 프로그램을 빌드하고 배포하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-105">This tutorial will walk you through building and deploying a Microsoft Azure application using Visual Studio and .NET.</span></span>  <span data-ttu-id="26385-106">완료되면 웹 기반 할 일 응용 프로그램이 ASP.NET MVC Core로 빌드되고, Azure 웹앱으로 호스팅되고, Azure CosmosDB를 사용하여 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-106">When finished, you'll have a web-based to-do application built in ASP.NET MVC Core, hosted as an Azure Web App, and using Azure CosmosDB for data storage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26385-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="26385-107">Prerequisites</span></span>

* [<span data-ttu-id="26385-108">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="26385-108">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)
* <span data-ttu-id="26385-109">[Microsoft Azure 구독](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="26385-109">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>

## <a name="create-a-cosmosdb-account"></a><span data-ttu-id="26385-110">CosmosDB 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="26385-110">Create a CosmosDB account</span></span>

<span data-ttu-id="26385-111">CosmosDB는 이 자습서의 데이터 저장에 사용되므로 계정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-111">CosmosDB is used for data storage in this tutorial, so you'll need to create an account.</span></span>  <span data-ttu-id="26385-112">이 스크립트를 로컬 또는 Cloud Shell에서 실행하여 Azure CosmosDB DocumentDB API 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26385-112">Run this script locally or in the Cloud Shell to create an Azure CosmosDB DocumentDB API account.</span></span>  <span data-ttu-id="26385-113">아래 코드 블록에서 **실습** 단추를 클릭하여 [Azure Cloud Shell](/azure/cloud-shell/)을 시작하고 스크립트 블록을 셸로 복사/붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="26385-113">Click the **Try it** button on the code block below to launch the [Azure Cloud Shell](/azure/cloud-shell/) and copy/paste the script block into the shell.</span></span>

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

<span data-ttu-id="26385-114">표시된 **authKey** 및 **끝점**을 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="26385-114">Make a note of the displayed **authKey** and **endpoint**</span></span> 

## <a name="downloading-and-running-the-application"></a><span data-ttu-id="26385-115">응용 프로그램 다운로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="26385-115">Downloading and running the application</span></span>

<span data-ttu-id="26385-116">이 연습에 대한 샘플 코드를 다운로드하고 CosmosDB 계정을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="26385-116">Let's get the sample code for this walkthrough and hook it up to your CosmosDB account.</span></span>

1. <span data-ttu-id="26385-117">샘플 코드를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-117">Download the sample code.</span></span>  <span data-ttu-id="26385-118">[GitHub에서 가져](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/)오거나 [git 명령줄 클라이언트](https://git-scm.com/)가 있는 경우 다음 명령을 사용하여 로컬 컴퓨터에 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-118">You can [get it from GitHub](https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart/), or if you have the [git command line client](https://git-scm.com/), clone it to your local machine with the following command:</span></span>

    ```cmd
    git clone https://github.com/Azure-Samples/dotnet-cosmosdb-quickstart
    ```

2. <span data-ttu-id="26385-119">Visual Studio에서 **todo.csproj**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26385-119">Open **todo.csproj** in Visual Studio.</span></span>

3. <span data-ttu-id="26385-120">웹 프로젝트에서 **appsettings.json**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26385-120">Open **appsettings.json** in the web project.</span></span>  <span data-ttu-id="26385-121">다음 줄을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="26385-121">Look for the following lines:</span></span>

    ```json
    "authKey": "AUTHKEYVALUE",
    "endpoint": "ENDPOINTVALUE",
    ```
    <span data-ttu-id="26385-122">**AUTHKEYVALUE** 및 **ENDPOINTVALUE**를 앞에서 기록한 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="26385-122">Replace **AUTHKEYVALUE** and **ENDPOINTVALUE** with the values you noted earlier.</span></span>

4. <span data-ttu-id="26385-123">**F5** 키를 눌러 프로젝트의 NuGet 패키지를 복원하고, 프로젝트를 빌드하고, 로컬로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-123">Press **F5** to restore the project's NuGet packages, build the project, and run it locally.</span></span>

<span data-ttu-id="26385-124">웹 응용 프로그램은 브라우저에서 로컬로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-124">The web application should run locally in your browser.</span></span>  <span data-ttu-id="26385-125">이제 **새로 만들기**를 클릭하여 할 일 목록에 새 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26385-125">You can add new items to the to-do list by clicking **Create New**.</span></span>  <span data-ttu-id="26385-126">응용 프로그램에 입력하는 데이터는 CosmosDB 계정에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="26385-126">Note the data you enter in the application is being stored in your CosmosDB account.</span></span>  <span data-ttu-id="26385-127">[Azure Portal에서 데이터를 볼](/azure/documentdb/documentdb-view-json-document-explorer) 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26385-127">You can [view your data in the Azure portal](/azure/documentdb/documentdb-view-json-document-explorer).</span></span>

## <a name="deploying-the-application-as-an-azure-web-app"></a><span data-ttu-id="26385-128">Azure 웹앱으로 응용 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="26385-128">Deploying the application as an Azure Web App</span></span>

<span data-ttu-id="26385-129">DocumentDB와 같은 Azure 서비스를 사용하는 응용 프로그램을 성공적으로 빌드했습니다.</span><span class="sxs-lookup"><span data-stu-id="26385-129">You've successfully built an application that uses Azure services like DocumentDB.</span></span>  <span data-ttu-id="26385-130">다음으로, 웹 응용 프로그램을 클라우드에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-130">Next, we'll deploy our web application to the cloud.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26385-131">Azure 구독이 연결된 동일한 계정으로 Visual Studio에 로그인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-131">Be sure you're signed into Visual Studio with the same account your Azure subscription is associated with.</span></span>

1. <span data-ttu-id="26385-132">Visual Studio 솔루션 탐색기에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭하고 **게시...**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-132">In Visual Studio Solution Explorer, right-click on the project name and select **Publish...**</span></span>

2. <span data-ttu-id="26385-133">게시 대화 상자를 사용하여 **Microsoft Azure App Service**, **새로 만들기**를 차례로 선택한 다음 **게시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-133">Using the Publish dialog, select **Microsoft Azure App Service**, select **Create New**, and then click **Publish**</span></span>

3. <span data-ttu-id="26385-134">다음과 같이 App Service 만들기 대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-134">Complete the Create App Service dialog as follows:</span></span>

    * <span data-ttu-id="26385-135">고유한 **웹앱 이름**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-135">Enter a unique **Web App Name**.</span></span>  <span data-ttu-id="26385-136">이는 앱에 대한 URL의 일부가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26385-136">This will be part of the URL for your app.</span></span>
    * <span data-ttu-id="26385-137">배포하는 Azure **구독**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-137">Select the Azure **Subscription** you're deploying to.</span></span>  <span data-ttu-id="26385-138">이전에 Cloud Shell에 로그인할 때 사용한 동일한 구독을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-138">Use same subscription with which you were logged into Cloud Shell earlier.</span></span>
    * <span data-ttu-id="26385-139">웹 응용 프로그램의 **리소스 그룹**에 대한 *DotNetAzureTutorial*을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-139">Select *DotNetAzureTutorial* for the **Resource Group** for your web application.</span></span>
    * <span data-ttu-id="26385-140">**App Service 계획**을 선택하거나 만들어 응용 프로그램의 가격을 책정합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-140">Select or create an **App Service Plan** to determine the pricing your your application.</span></span>  <span data-ttu-id="26385-141">다음은 [App Service 계획에 대한 자세한 내용](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)입니다.</span><span class="sxs-lookup"><span data-stu-id="26385-141">Here's [more information about App Service Plans](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

4. <span data-ttu-id="26385-142">**만들기**를 클릭하여 응용 프로그램을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="26385-142">Click **Create** to deploy the application.</span></span>  <span data-ttu-id="26385-143">배포가 완료되면 배포된 응용 프로그램과 함께 브라우저가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="26385-143">When deployment is complete, a browser will open with your deployed application.</span></span>

![완성된 앱](./media/dotnet-quickstart/todo.png)

## <a name="clean-up"></a><span data-ttu-id="26385-145">정리</span><span class="sxs-lookup"><span data-stu-id="26385-145">Clean up</span></span>

<span data-ttu-id="26385-146">앱을 테스트하고 코드 및 리소스를 검사한 후에는 리소스 그룹을 삭제하여 웹앱 및 CosmosDB 계정을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26385-146">When you're done testing the app and inspecting the code and resources, you can delete the Web App and CosmosDB account by deleting the resource group.</span></span> <span data-ttu-id="26385-147">Cloud Shell에서</span><span class="sxs-lookup"><span data-stu-id="26385-147">in the Cloud Shell.</span></span>

```azurecli-interactive
az group delete -n DotNetAzureTutorial
```

## <a name="next-steps"></a><span data-ttu-id="26385-148">다음 단계</span><span class="sxs-lookup"><span data-stu-id="26385-148">Next steps</span></span>

* [<span data-ttu-id="26385-149">Azure Active Directory를 사용하여 ASP.NET 웹 응용 프로그램에서 인증</span><span class="sxs-lookup"><span data-stu-id="26385-149">Use Azure Active Directory for authentication in an ASP.NET web application</span></span>](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)
* [<span data-ttu-id="26385-150">Azure SQL Database를 사용하여 Azure 웹앱 빌드</span><span class="sxs-lookup"><span data-stu-id="26385-150">Build an Azure Web App using Azure SQL Database</span></span>](/azure/app-service-web/web-sites-dotnet-get-started)
* [<span data-ttu-id="26385-151">Azure Storage를 통해 .NET 샘플 응용 프로그램 사용해보기</span><span class="sxs-lookup"><span data-stu-id="26385-151">Try a .NET sample application with Azure Storage</span></span>](/azure/storage/storage-samples-dotnet)


