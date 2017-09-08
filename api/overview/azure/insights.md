---
title: ".NET용 Azure Application Insights 라이브러리"
description: ".NET용 Azure Application Insights 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Application AppInsights
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/24/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 2eef8d322d905679e8aceaed77ba44726c14dd94
ms.sourcegitcommit: fa02d34afbf981f809661ab842b3b93242a38f68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2017
---
# <a name="azure-application-insights-libraries-for-net"></a><span data-ttu-id="2c8b0-104">.NET용 Azure Application Insights 라이브러리</span><span class="sxs-lookup"><span data-stu-id="2c8b0-104">Azure Application Insights libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="2c8b0-105">개요</span><span class="sxs-lookup"><span data-stu-id="2c8b0-105">Overview</span></span>

<span data-ttu-id="2c8b0-106">Application Insights는 웹 개발자를 위해 강력한 임시 분석 기능을 갖춘 확장 가능한 모니터링 및 진단 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="2c8b0-106">Application Insights is an extensible monitoring & diagnostics service for web developers with powerful ad-hoc analytics capabilities.</span></span> <span data-ttu-id="2c8b0-107">Application Insights 네임스페이스의 클래스를 사용하여 원격 분석 수집을 구성하고, 모니터링하려는 응용 프로그램에서 모든 사용자 지정 원격 분석을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c8b0-107">You can use the classes in the ApplicationInsights namespace to configure telemetry collection and send any custom telemetry from your applications that you want to monitor.</span></span>

## <a name="client-library"></a><span data-ttu-id="2c8b0-108">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="2c8b0-108">Client library</span></span>

<span data-ttu-id="2c8b0-109">.NET용 Application Insight Client SDK를 사용하면 나중의 분석을 위해 이벤트, 집계 데이터, 예외, 종속성 및 메트릭을 Azure에 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c8b0-109">The Application Insights client SDK for .NET allows you to log event, aggregated data, exceptions, dependency, and metrics to Azure for future analysis.</span></span>

<span data-ttu-id="2c8b0-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.ApplicationInsights )를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2c8b0-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ApplicationInsights ) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="2c8b0-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="2c8b0-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ApplicationInsights 
```

```bash
dotnet add package Microsoft.ApplicationInsights 
```

### <a name="example"></a><span data-ttu-id="2c8b0-112">예제</span><span class="sxs-lookup"><span data-stu-id="2c8b0-112">Example</span></span>

<span data-ttu-id="2c8b0-113">이 예제에서는 사용자 지정 이벤트를 Application Insights로 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="2c8b0-113">This example tracks a custom event to Application Insights.</span></span>

```csharp
TelemetryClient client = new TelemetryClient();
client.TrackEvent("MyCustomEvent");
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="2c8b0-114">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="2c8b0-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/insights/client)



## <a name="samples"></a><span data-ttu-id="2c8b0-115">샘플</span><span class="sxs-lookup"><span data-stu-id="2c8b0-115">Samples</span></span>

- [<span data-ttu-id="2c8b0-116">OpenSchema를 사용한 Application Insight Analytics(영문)</span><span class="sxs-lookup"><span data-stu-id="2c8b0-116">Application Insights Analytics with OpenSchema</span></span>](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/)

<span data-ttu-id="2c8b0-117">Azure Application Insights 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="2c8b0-117">View the [complete list](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet) of Azure Application Insights samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
