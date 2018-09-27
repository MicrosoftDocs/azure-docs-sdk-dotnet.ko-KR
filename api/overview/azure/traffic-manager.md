---
title: .NET용 Azure Traffic Manager 라이브러리
description: .NET용 Azure Traffic Manager 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: traffic-manager
ms.openlocfilehash: a75b5c566496f73475d24d62288a00c7d5775168
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190826"
---
# <a name="azure-traffic-manager-libraries-for-net"></a><span data-ttu-id="af6f8-103">.NET용 Azure Traffic Manager 라이브러리</span><span class="sxs-lookup"><span data-stu-id="af6f8-103">Azure Traffic Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="af6f8-104">개요</span><span class="sxs-lookup"><span data-stu-id="af6f8-104">Overview</span></span>

<span data-ttu-id="af6f8-105">Microsoft Azure Traffic Manager를 사용하면 다양한 데이터 센터에서 서비스 엔드포인트에 대한 사용자 트래픽의 배포를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af6f8-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="af6f8-106">Traffic Manager에서 지원되는 서비스 엔드포인트는 Azure VM, Web Apps 및 클라우드 서비스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="af6f8-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="af6f8-107">또한 외부, Azure가 아닌 엔드포인트로 Traffic Manager를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af6f8-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="af6f8-108">[Azure Traffic Manager](/azure/traffic-manager/traffic-manager-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="af6f8-108">Learn more about [Azure Traffic Manager](/azure/traffic-manager/traffic-manager-overview).</span></span>  

## <a name="management-library"></a><span data-ttu-id="af6f8-109">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="af6f8-109">Management library</span></span>

<span data-ttu-id="af6f8-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="af6f8-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="af6f8-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="af6f8-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.TrafficManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.TrafficManager.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="af6f8-112">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="af6f8-112">Explore the management APIs</span></span>](/dotnet/api/overview/azure/trafficmanager/management)

## <a name="samples"></a><span data-ttu-id="af6f8-113">샘플</span><span class="sxs-lookup"><span data-stu-id="af6f8-113">Samples</span></span>

<span data-ttu-id="af6f8-114">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="af6f8-114">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package