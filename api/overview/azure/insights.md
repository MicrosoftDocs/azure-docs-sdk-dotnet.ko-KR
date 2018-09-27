---
title: .NET용 Azure Application Insights 라이브러리
description: .NET용 Azure Application Insights 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: application-insights
ms.openlocfilehash: 10b65f536c6461959b0be9b8f9bd3ec56a307bea
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190842"
---
# <a name="azure-application-insights-libraries-for-net"></a><span data-ttu-id="9a9bd-103">.NET용 Azure Application Insights 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9a9bd-103">Azure Application Insights libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="9a9bd-104">개요</span><span class="sxs-lookup"><span data-stu-id="9a9bd-104">Overview</span></span>

<span data-ttu-id="9a9bd-105">Application Insights는 웹 개발자를 위해 강력한 임시 분석 기능을 갖춘 확장 가능한 모니터링 및 진단 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="9a9bd-105">Application Insights is an extensible monitoring & diagnostics service for web developers with powerful ad-hoc analytics capabilities.</span></span> <span data-ttu-id="9a9bd-106">Application Insights 네임스페이스의 클래스를 사용하여 원격 분석 수집을 구성하고, 모니터링하려는 응용 프로그램에서 모든 사용자 지정 원격 분석을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9bd-106">You can use the classes in the ApplicationInsights namespace to configure telemetry collection and send any custom telemetry from your applications that you want to monitor.</span></span>

## <a name="client-library"></a><span data-ttu-id="9a9bd-107">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9a9bd-107">Client library</span></span>

<span data-ttu-id="9a9bd-108">.NET용 Application Insight Client SDK를 사용하면 나중의 분석을 위해 이벤트, 집계 데이터, 예외, 종속성 및 메트릭을 Azure에 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a9bd-108">The Application Insights client SDK for .NET allows you to log event, aggregated data, exceptions, dependency, and metrics to Azure for future analysis.</span></span>

<span data-ttu-id="9a9bd-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.ApplicationInsights )를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9bd-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9a9bd-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="9a9bd-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ApplicationInsights 
```

```bash
dotnet add package Microsoft.ApplicationInsights 
```

### <a name="example"></a><span data-ttu-id="9a9bd-111">예</span><span class="sxs-lookup"><span data-stu-id="9a9bd-111">Example</span></span>

<span data-ttu-id="9a9bd-112">이 예제에서는 사용자 지정 이벤트를 Application Insights로 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="9a9bd-112">This example tracks a custom event to Application Insights.</span></span>

```csharp
TelemetryClient client = new TelemetryClient();
client.TrackEvent("MyCustomEvent");
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9a9bd-113">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="9a9bd-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/insights/client)



## <a name="samples"></a><span data-ttu-id="9a9bd-114">샘플</span><span class="sxs-lookup"><span data-stu-id="9a9bd-114">Samples</span></span>

- [<span data-ttu-id="9a9bd-115">OpenSchema를 사용한 Application Insight Analytics(영문)</span><span class="sxs-lookup"><span data-stu-id="9a9bd-115">Application Insights Analytics with OpenSchema</span></span>](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/)

<span data-ttu-id="9a9bd-116">Azure Application Insights 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9a9bd-116">View the [complete list](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) of Azure Application Insights samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
