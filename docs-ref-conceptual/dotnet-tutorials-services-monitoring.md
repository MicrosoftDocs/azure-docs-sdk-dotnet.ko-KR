---
title: Azure에서 .NET 앱 관리 및 모니터링에 대한 자습서
description: Azure에서 실행되는 .NET 응용 프로그램의 상태 및 성능을 모니터링하고 원격 분석을 계측하여 사용자의 앱 사용 방식에 대한 정보를 저장합니다.
ms.date: 10/19/2017
ms.openlocfilehash: 289fa4468be6e76f0ca98d844237638a86c4d148
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190656"
---
# <a name="tutorials-for-monitoring-and-managing-your-net-apps-in-azure"></a><span data-ttu-id="e1b06-103">Azure에서 .NET 앱 모니터링 및 관리에 대한 자습서</span><span class="sxs-lookup"><span data-stu-id="e1b06-103">Tutorials for monitoring and managing your .NET apps in Azure</span></span>

<span data-ttu-id="e1b06-104">다음 테이블은 Azure에서 실행되는 .NET 응용 프로그램 관리 및 모니터링에 대한 자세한 자습서에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b06-104">The following table links to in-depth tutorials for managing and monitoring your .NET applications running on Azure.</span></span> 

<span data-ttu-id="e1b06-105">샘플 소스 코드는 [Azure 서비스 샘플](https://azure.microsoft.com/resources/samples/?platform=dotnet) 목록을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e1b06-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>

| | |
|---|---|
| <span data-ttu-id="e1b06-106">**Application Insights**</span><span class="sxs-lookup"><span data-stu-id="e1b06-106">**Application Insights**</span></span> ||
| <span data-ttu-id="e1b06-107">[ASP.NET 웹 사이트용 Application Insights 설정][1]</span><span class="sxs-lookup"><span data-stu-id="e1b06-107">[Set up Application Insights for your ASP.NET website][1]</span></span> | <span data-ttu-id="e1b06-108">ASP.NET 웹앱에서 Azure Application Insights 서비스로 원격 분석을 보내도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b06-108">Configure your ASP.NET web app to send telemetry to the Azure Application Insights service.</span></span> | 
| <span data-ttu-id="e1b06-109">[Application Insights를 사용한 런타임 시 웹앱 계측][2]</span><span class="sxs-lookup"><span data-stu-id="e1b06-109">[Instrument web apps at runtime with Application Insights][2]</span></span> | <span data-ttu-id="e1b06-110">코드를 수정하거나 다시 배포할 필요 없이 라이브 웹앱을 계측합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b06-110">Instrument a live web app without having to modify or redeploy your code..</span></span> | 
| <span data-ttu-id="e1b06-111">[.NET 응용 프로그램에 대한 Application Insights를 수동으로 구성][3]</span><span class="sxs-lookup"><span data-stu-id="e1b06-111">[Manually configure Application Insights for .NET applications][3]</span></span> | <span data-ttu-id="e1b06-112">Application Insights를 구성하여 다양한 응용 프로그램이나 응용 프로그램 역할, 구성 요소 또는 마이크로 서비스를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b06-112">Configure Application Insights to monitor a wide variety of applications or application roles, components, or microservices.</span></span> | 
| <span data-ttu-id="e1b06-113">[Windows 데스크톱 앱에서 사용량 및 성능 모니터링][4]</span><span class="sxs-lookup"><span data-stu-id="e1b06-113">[Monitoring usage and performance in Windows Desktop apps][4]</span></span> | <span data-ttu-id="e1b06-114">Application Insights 및 HockeyApp을 사용하여 배포된 응용 프로그램의 사용량 및 성능을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b06-114">Use Application Insights and HockeyApp to monitor your deployed application for usage and performance.</span></span> | 
| <span data-ttu-id="e1b06-115">[ASP.NET Core용 Application Insights][5]</span><span class="sxs-lookup"><span data-stu-id="e1b06-115">[Application Insights for ASP.NET Core][5]</span></span> | <span data-ttu-id="e1b06-116">ASP.NET Core 응용 프로그램의 가용성, 성능 및 사용 현황을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b06-116">Monitor your ASP.NET Core application for availability, performance and usage.</span></span> | 
| <span data-ttu-id="e1b06-117">[사용자 지정 이벤트 및 메트릭용 Application Insights API][6]</span><span class="sxs-lookup"><span data-stu-id="e1b06-117">[Application Insights API for custom events and metrics][6]</span></span> | <span data-ttu-id="e1b06-118">응용 프로그램에 몇 줄의 코드를 삽입하여 사용자가 해당 응용 프로그램으로 어떤 작업을 하는지 살펴보거나 진단 문제를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e1b06-118">Insert a few lines of code in your application to find out what users are doing with it or help diagnose issues.</span></span> | 


[1]: /azure/application-insights/app-insights-asp-net
[2]: /azure/application-insights/app-insights-monitor-performance-live-website-now
[3]: /azure/application-insights/app-insights-windows-services
[4]: /azure/application-insights/app-insights-windows-desktop
[5]: /azure/application-insights/app-insights-asp-net-core
[6]: /azure/application-insights/app-insights-api-custom-events-metrics
