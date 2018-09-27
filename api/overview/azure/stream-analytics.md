---
title: .NET용 Azure Stream Analytics 라이브러리
description: .NET용 Azure Stream Analytics 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: stream-analytics
ms.openlocfilehash: c04a5c8a7b1d7e0f283d4fb81bd772de24f195eb
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190456"
---
# <a name="azure-stream-analytics-libraries-for-net"></a><span data-ttu-id="f94d6-103">.NET용 Azure Stream Analytics 라이브러리</span><span class="sxs-lookup"><span data-stu-id="f94d6-103">Azure Stream Analytics libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="f94d6-104">개요</span><span class="sxs-lookup"><span data-stu-id="f94d6-104">Overview</span></span>

<span data-ttu-id="f94d6-105">[Azure Stream Analytics](/azure/stream-analytics/stream-analytics-introduction)는 스트리밍 데이터에 대한 실시간 분석 계산 작업을 설정할 수 있는 완전히 관리되는 이벤트 처리 엔진입니다.</span><span class="sxs-lookup"><span data-stu-id="f94d6-105">[Azure Stream Analytics](/azure/stream-analytics/stream-analytics-introduction) is a fully managed event-processing engine that lets you set up real-time analytic computations on streaming data.</span></span> <span data-ttu-id="f94d6-106">데이터는 장치, 센서, 웹 사이트, 소셜 미디어 피드, 응용 프로그램, 인프라 시스템 등에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f94d6-106">The data can come from devices, sensors, web sites, social media feeds, applications, infrastructure systems, and more.</span></span> 

<span data-ttu-id="f94d6-107">Azure Stream Analytics에 대한 자세한 내용은 [Azure Stream Analytics 실시간 사기 감지 시작](/azure/stream-analytics/stream-analytics-real-time-fraud-detection)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f94d6-107">To learn more about Azure Stream Analytics, see [Get started with Azure Stream Analytics Real-time fraud detection](/azure/stream-analytics/stream-analytics-real-time-fraud-detection).</span></span>


## <a name="management-library"></a><span data-ttu-id="f94d6-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="f94d6-108">Management library</span></span>

<span data-ttu-id="f94d6-109">Azure Stream Analytics 관리 라이브러리를 사용하여 Azure Stream Analytics 작업을 만들고 시작 및 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f94d6-109">Use the Azure Stream Analytics management library to create, start, and stop Azure Stream Analytics jobs.</span></span>

<span data-ttu-id="f94d6-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.StreamAnalytics)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f94d6-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.StreamAnalytics) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f94d6-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="f94d6-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.StreamAnalytics
```

```bash
dotnet add package Microsoft.Azure.Management.StreamAnalytics
```

### <a name="code-example"></a><span data-ttu-id="f94d6-112">코드 예제</span><span class="sxs-lookup"><span data-stu-id="f94d6-112">Code Example</span></span>

<span data-ttu-id="f94d6-113">이 예제에서는 Stream Analytics 클라이언트를 인스턴스화하고 스트리밍 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f94d6-113">This example instantiates a Stream Analytics client and creates a streaming job.</span></span>

```csharp
/* Include these 'using' directives:
using Microsoft.Azure.Management.StreamAnalytics;
*/
SynchronizationContext.SetSynchronizationContext(new SynchronizationContext());

// Get credentials
ServiceClientCredentials credentials = GetCredentials().Result;

// Create Stream Analytics management client
StreamAnalyticsManagementClient streamAnalyticsManagementClient = new StreamAnalyticsManagementClient(credentials)
{
    SubscriptionId = subscriptionId
};

// Create a streaming job
StreamingJob streamingJob = new StreamingJob()
{
    Tags = new Dictionary<string, string>()
    {
        { "Origin", ".NET SDK" },
        { "ReasonCreated", "Getting started tutorial" }
    },
    Location = "West US",
    EventsOutOfOrderPolicy = EventsOutOfOrderPolicy.Drop,
    EventsOutOfOrderMaxDelayInSeconds = 5,
    EventsLateArrivalMaxDelayInSeconds = 16,
    OutputErrorPolicy = OutputErrorPolicy.Drop,
    DataLocale = "en-US",
    CompatibilityLevel = CompatibilityLevel.OneFullStopZero,
    Sku = new Sku()
    {
        Name = SkuName.Standard
    }
};
StreamingJob createStreamingJobResult = streamAnalyticsManagementClient.StreamingJobs.CreateOrReplace(streamingJob, resourceGroupName, streamingJobName);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f94d6-114">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="f94d6-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/streamanalytics/management)


## <a name="samples"></a><span data-ttu-id="f94d6-115">샘플</span><span class="sxs-lookup"><span data-stu-id="f94d6-115">Samples</span></span>

- [<span data-ttu-id="f94d6-116">관리 .NET SDK: .NET용 Azure Stream Analytics API를 사용하여 분석 작업 설정 및 실행</span><span class="sxs-lookup"><span data-stu-id="f94d6-116">Management .NET SDK: Set up and run analytics jobs using the Azure Stream Analytics API for .NET</span></span>](/azure/stream-analytics/stream-analytics-dotnet-management-sdk)

<span data-ttu-id="f94d6-117">Azure Stream Analytics 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=stream-analytics)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="f94d6-117">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=stream-analytics) of Azure Stream Analytics samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
