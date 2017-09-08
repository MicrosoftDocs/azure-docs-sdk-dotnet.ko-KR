---
title: ".NET용 Azure Traffic Manager 라이브러리"
description: ".NET용 Azure Traffic Manager 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Traffic Manager
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 0fc747c25fe368b5d67f70af1e2b9afc5e07f615
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-traffic-manager-libraries-for-net"></a><span data-ttu-id="a1ac8-104">.NET용 Azure Traffic Manager 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a1ac8-104">Azure Traffic Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="a1ac8-105">개요</span><span class="sxs-lookup"><span data-stu-id="a1ac8-105">Overview</span></span>

<span data-ttu-id="a1ac8-106">Microsoft Azure Traffic Manager를 사용하면 다양한 데이터 센터에서 서비스 끝점에 대한 사용자 트래픽의 배포를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ac8-106">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="a1ac8-107">Traffic Manager에서 지원되는 서비스 끝점은 Azure VM, Web Apps 및 클라우드 서비스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ac8-107">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="a1ac8-108">또한 외부, Azure가 아닌 끝점으로 Traffic Manager를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ac8-108">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="a1ac8-109">[Azure Traffic Manager](https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="a1ac8-109">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).</span></span>  

## <a name="management-library"></a><span data-ttu-id="a1ac8-110">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a1ac8-110">Management library</span></span>

<span data-ttu-id="a1ac8-111">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ac8-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="a1ac8-112">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="a1ac8-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.TrafficManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.TrafficManager.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="a1ac8-113">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="a1ac8-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/trafficmanager/management)

## <a name="samples"></a><span data-ttu-id="a1ac8-114">샘플</span><span class="sxs-lookup"><span data-stu-id="a1ac8-114">Samples</span></span>

<span data-ttu-id="a1ac8-115">앱에서 사용할 수 있는 [.NET 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ac8-115">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package