---
title: ".NET용 Azure Data Factory 라이브러리"
description: ".NET용 Azure Data Factory 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Data Factory
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: data-factory
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 20e94fa687a3008ac7112d1a6511f8cec92b544c
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2017
---
# <a name="azure-data-factory-libraries-for-net"></a><span data-ttu-id="0fd0d-104">.NET용 Azure Data Factory 라이브러리</span><span class="sxs-lookup"><span data-stu-id="0fd0d-104">Azure Data Factory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="0fd0d-105">개요</span><span class="sxs-lookup"><span data-stu-id="0fd0d-105">Overview</span></span>

<span data-ttu-id="0fd0d-106">Azure Data Factory는 클라우드 기반 데이터 통합 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-106">Azure Data Factory is a cloud-based data integration service.</span></span> <span data-ttu-id="0fd0d-107">이를 통해 클라우드에서 데이터 기반 워크플로를 만들어 데이터 이동 및 데이터 변환을 오케스트레이션하고 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-107">It enables you to create data-driven workflows in the cloud to orchestrate and automate data movement and data transformation.</span></span>

<span data-ttu-id="0fd0d-108">자세히 알아보려면 [Azure Data Factory 소개](/azure/data-factory/data-factory-introduction)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-108">To learn more, read the [Introduction to Azure Data Factory](/azure/data-factory/data-factory-introduction).</span></span>

## <a name="management-library---data-factory-v2-preview"></a><span data-ttu-id="0fd0d-109">관리 라이브러리 - Data Factory V2(미리 보기)</span><span class="sxs-lookup"><span data-stu-id="0fd0d-109">Management library - Data Factory V2 (Preview)</span></span>

<span data-ttu-id="0fd0d-110">관리 라이브러리를 사용하여 Data Factory V2(미리 보기)에서 데이터 기반 워크플로(파이프라인)를 만들고 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-110">Use the management library to create and schedule data-driven workflows (pipelines) in Data Factory V2 (Preview).</span></span>  <span data-ttu-id="0fd0d-111">자세한 내용은 [.NET SDK를 사용하여 데이터 팩터리 및 파이프라인 만들기](/azure/data-factory/quickstart-create-data-factory-dot-net)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-111">For more information, see [Create a data factory and pipeline using .NET SDK](/azure/data-factory/quickstart-create-data-factory-dot-net).</span></span>

<span data-ttu-id="0fd0d-112">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactory)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactory) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="0fd0d-113">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="0fd0d-113">Visual Studio Package Manager</span></span>

```powershell
# Get the most recent prerelease package
Install-Package Microsoft.Azure.Management.DataFactory -Prerelease
```

```bash
# Be sure to include the most recent version from the NuGet package page
dotnet add package Microsoft.Azure.Management.DataFactory --version 0.2.0-preview
```

### <a name="code-example"></a><span data-ttu-id="0fd0d-114">코드 예제</span><span class="sxs-lookup"><span data-stu-id="0fd0d-114">Code Example</span></span>

<span data-ttu-id="0fd0d-115">다음 예제에서는 관리 라이브러리를 사용하여 데이터 팩터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-115">The following example uses the management library to create a data factory.</span></span>

```csharp
/*
using Microsoft.Azure.Management.ResourceManager;
using Microsoft.Azure.Management.DataFactory;
using Microsoft.Azure.Management.DataFactory.Models;
*/

DataFactoryManagementClient client = new DataFactoryManagementClient(tokenCredentials) { SubscriptionId = subscriptionId };
Factory dataFactory = new Factory
{
    Location = region,
    Identity = new FactoryIdentity()
};
client.Factories.CreateOrUpdate(resourceGroup, dataFactoryName, dataFactory);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="0fd0d-116">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="0fd0d-116">Explore the management APIs</span></span>](/dotnet/api/microsoft.azure.management.datafactory)

## <a name="management-library---data-factory-v1"></a><span data-ttu-id="0fd0d-117">관리 라이브러리 - Data Factory V1</span><span class="sxs-lookup"><span data-stu-id="0fd0d-117">Management library - Data Factory V1</span></span>

<span data-ttu-id="0fd0d-118">관리 라이브러리를 사용하여 Data Factory 버전 1에서 데이터 기반 워크플로(파이프라인)를 만들고 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-118">Use the management library to create and schedule data-driven workflows (pipelines) in Data Factory Version 1.</span></span>  <span data-ttu-id="0fd0d-119">자세한 내용은 [Data Factory 버전 1](/azure/data-factory/v1/data-factory-introduction)의 설명서를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-119">For more information, review the documentation for [Data Factory Version 1](/azure/data-factory/v1/data-factory-introduction).</span></span>

<span data-ttu-id="0fd0d-120">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-120">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="0fd0d-121">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="0fd0d-121">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataFactories
```

```bash
dotnet add package Microsoft.Azure.Management.DataFactories
```

### <a name="code-example"></a><span data-ttu-id="0fd0d-122">코드 예제</span><span class="sxs-lookup"><span data-stu-id="0fd0d-122">Code Example</span></span>

<span data-ttu-id="0fd0d-123">다음 예제에서는 관리 라이브러리를 사용하여 데이터 팩터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-123">The following example uses the management library to create a data factory.</span></span>

```csharp
DataFactoryManagementClient client = new DataFactoryManagementClient(aadTokenCredentials, resourceManagerUri);
client.DataFactories.CreateOrUpdate(resourceGroupName,
    new DataFactoryCreateOrUpdateParameters()
    {
        DataFactory = new DataFactory()
        {
            Name = dataFactoryName,
            Location = "westus",
            Properties = new DataFactoryProperties()
        }
    }
);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="0fd0d-124">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="0fd0d-124">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datafactories/management)

## <a name="samples"></a><span data-ttu-id="0fd0d-125">샘플</span><span class="sxs-lookup"><span data-stu-id="0fd0d-125">Samples</span></span>

* <span data-ttu-id="0fd0d-126">[MyDriving - Azure IOT 및 모바일 응용 프로그램 예제](https://azure.microsoft.com/resources/samples/mydriving/): 데이터 팩터리를 사용하여 자세한 정보를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-126">[MyDriving - An Azure IOT and Mobile Sample Application](https://azure.microsoft.com/resources/samples/mydriving/) that uses Data Factory to drive insights.</span></span>

<span data-ttu-id="0fd0d-127">앱에서 사용할 수 있는 [.NET 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd0d-127">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
