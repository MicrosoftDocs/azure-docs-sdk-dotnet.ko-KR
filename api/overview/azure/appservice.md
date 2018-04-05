---
title: .NET용 Azure App Service 라이브러리
description: .NET용 Azure App Service 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Web Apps, App Service, 모바일, ASP.NET
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: app-service
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 356a86e8fa70512b6f31c6e237173a74d1c6f60a
ms.sourcegitcommit: dbec35008347b581dd238b882354300e427bec70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2018
---
# <a name="azure-app-service-libraries-for-net"></a><span data-ttu-id="309c0-104">.NET용 Azure App Service 라이브러리</span><span class="sxs-lookup"><span data-stu-id="309c0-104">Azure App Service libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="309c0-105">개요</span><span class="sxs-lookup"><span data-stu-id="309c0-105">Overview</span></span>

<span data-ttu-id="309c0-106">[Azure App Service](/azure/app-service/app-service-value-prop-what-is)를 사용하면 웹 사이트, 웹 응용 프로그램, 서비스 및 REST API를 배포하고 크기 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="309c0-106">[Azure App Service](/azure/app-service/app-service-value-prop-what-is) allows you to deploy and scale websites, web applications, services, and REST APIs.</span></span>

## <a name="management-api"></a><span data-ttu-id="309c0-107">관리 API</span><span class="sxs-lookup"><span data-stu-id="309c0-107">Management API</span></span>

<span data-ttu-id="309c0-108">관리 API를 사용하여 Azure App Service에서 호스팅되는 요소를 배포, 관리 및 크기 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="309c0-108">Deploy, manage, and scale elements hosted in Azure App Service with the management API.</span></span>

<span data-ttu-id="309c0-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="309c0-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>


#### <a name="visual-studio-package-manager"></a><span data-ttu-id="309c0-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="309c0-110">Visual Studio package manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.AppService.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="309c0-111">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="309c0-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.AppService.Fluent
```

### <a name="code-example"></a><span data-ttu-id="309c0-112">코드 예제</span><span class="sxs-lookup"><span data-stu-id="309c0-112">Code Example</span></span>

<span data-ttu-id="309c0-113">새 웹앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="309c0-113">Create a new web app.</span></span>

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.Azure.Management.AppService.Fluent;
*/

IWebApp app1 = azure.WebApps
    .Define("MyUniqueWebAddress")
    .WithRegion(Region.USWest)
    .WithNewResourceGroup("MyResourceGroup")
    .WithNewWindowsPlan(PricingTier.StandardS1)
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="309c0-114">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="309c0-114">Explore the Management APIs</span></span>](/dotnet/api/overview/azure/appservice/management)

### <a name="samples"></a><span data-ttu-id="309c0-115">샘플</span><span class="sxs-lookup"><span data-stu-id="309c0-115">Samples</span></span>

* [<span data-ttu-id="309c0-116">Azure용 .NET SDK를 사용하여 웹앱 관리(영문)</span><span class="sxs-lookup"><span data-stu-id="309c0-116">Manage your web apps with the .NET SDK for Azure</span></span>](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-manage/)
* [<span data-ttu-id="309c0-117">Azure App Service용 ASP.NET 샘플(영문)</span><span class="sxs-lookup"><span data-stu-id="309c0-117">ASP.NET sample for Azure App Service</span></span>](https://azure.microsoft.com/resources/samples/app-service-web-dotnet-get-started/)

<span data-ttu-id="309c0-118">Azure App Service 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=app%20service)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="309c0-118">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=app%20service) of Azure App Service samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package