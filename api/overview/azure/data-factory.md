---
title: ".NET용 Azure Data Factory 라이브러리"
description: ".NET용 Azure Data Factory 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Data Factory
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/20/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: e0b85d7d3988febca6dce7f4038825d74e4b8d2e
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-data-factory-libraries-for-net"></a><span data-ttu-id="5d60e-104">.NET용 Azure Data Factory 라이브러리</span><span class="sxs-lookup"><span data-stu-id="5d60e-104">Azure Data Factory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="5d60e-105">개요</span><span class="sxs-lookup"><span data-stu-id="5d60e-105">Overview</span></span>

<span data-ttu-id="5d60e-106">Azure Data Factory는 클라우드 기반 데이터 통합 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="5d60e-106">Azure Data Factory is a cloud-based data integration service.</span></span> <span data-ttu-id="5d60e-107">이를 통해 클라우드에서 데이터 기반 워크플로를 만들어 데이터 이동 및 데이터 변환을 오케스트레이션하고 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d60e-107">It enables you to create data-driven workflows in the cloud to orchestrate and automate data movement and data transformation.</span></span>

<span data-ttu-id="5d60e-108">자세히 알아보려면 [Azure Data Factory 소개](/azure/data-factory/data-factory-introduction)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d60e-108">To learn more, read the [Introduction to Azure Data Factory](/azure/data-factory/data-factory-introduction).</span></span>

## <a name="management-library"></a><span data-ttu-id="5d60e-109">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="5d60e-109">Management library</span></span>

<span data-ttu-id="5d60e-110">관리 라이브러리를 사용하여 데이터 기반 워크플로(파이프라인)를 만들고 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="5d60e-110">Use the management library to create and schedule data-driven workflows (pipelines).</span></span>

<span data-ttu-id="5d60e-111">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5d60e-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="5d60e-112">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="5d60e-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataFactories
```

```bash
dotnet add package Microsoft.Azure.Management.DataFactories
```

### <a name="code-example"></a><span data-ttu-id="5d60e-113">코드 예제</span><span class="sxs-lookup"><span data-stu-id="5d60e-113">Code Example</span></span>

<span data-ttu-id="5d60e-114">다음 예제에서는 관리 라이브러리를 사용하여 데이터 팩터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5d60e-114">The following example uses the management library to create a data factory.</span></span>

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
> [<span data-ttu-id="5d60e-115">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="5d60e-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datafactories/management)

## <a name="samples"></a><span data-ttu-id="5d60e-116">샘플</span><span class="sxs-lookup"><span data-stu-id="5d60e-116">Samples</span></span>

* <span data-ttu-id="5d60e-117">[MyDriving - Azure IOT 및 모바일 응용 프로그램 예제](https://azure.microsoft.com/resources/samples/mydriving/): 데이터 팩터리를 사용하여 자세한 정보를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="5d60e-117">[MyDriving - An Azure IOT and Mobile Sample Application](https://azure.microsoft.com/resources/samples/mydriving/) that uses Data Factory to drive insights.</span></span>

<span data-ttu-id="5d60e-118">앱에서 사용할 수 있는 [.NET 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="5d60e-118">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
