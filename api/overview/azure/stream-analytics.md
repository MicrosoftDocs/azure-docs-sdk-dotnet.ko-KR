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
# <a name="azure-stream-analytics-libraries-for-net"></a>.NET용 Azure Stream Analytics 라이브러리

## <a name="overview"></a>개요

[Azure Stream Analytics](/azure/stream-analytics/stream-analytics-introduction)는 스트리밍 데이터에 대한 실시간 분석 계산 작업을 설정할 수 있는 완전히 관리되는 이벤트 처리 엔진입니다. 데이터는 장치, 센서, 웹 사이트, 소셜 미디어 피드, 응용 프로그램, 인프라 시스템 등에서 가져올 수 있습니다. 

Azure Stream Analytics에 대한 자세한 내용은 [Azure Stream Analytics 실시간 사기 감지 시작](/azure/stream-analytics/stream-analytics-real-time-fraud-detection)을 참조하세요.


## <a name="management-library"></a>관리 라이브러리

Azure Stream Analytics 관리 라이브러리를 사용하여 Azure Stream Analytics 작업을 만들고 시작 및 중지합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.StreamAnalytics)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.StreamAnalytics
```

```bash
dotnet add package Microsoft.Azure.Management.StreamAnalytics
```

### <a name="code-example"></a>코드 예제

이 예제에서는 Stream Analytics 클라이언트를 인스턴스화하고 스트리밍 작업을 만듭니다.

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
> [관리 API 탐색](/dotnet/api/overview/azure/streamanalytics/management)


## <a name="samples"></a>샘플

- [관리 .NET SDK: .NET용 Azure Stream Analytics API를 사용하여 분석 작업 설정 및 실행](/azure/stream-analytics/stream-analytics-dotnet-management-sdk)

Azure Stream Analytics 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=stream-analytics)을 봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
