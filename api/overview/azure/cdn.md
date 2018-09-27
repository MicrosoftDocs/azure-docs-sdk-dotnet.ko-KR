---
title: .NET용 Azure CDN 라이브러리
description: .NET용 Azure CDN 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: cdn
ms.openlocfilehash: 6475edbe4fa0d01739de5cff76038aa6e7fd2cf9
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190126"
---
# <a name="azure-cdn-libraries-for-net"></a><span data-ttu-id="d1070-103">.NET용 Azure CDN 라이브러리</span><span class="sxs-lookup"><span data-stu-id="d1070-103">Azure CDN libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="d1070-104">개요</span><span class="sxs-lookup"><span data-stu-id="d1070-104">Overview</span></span>

<span data-ttu-id="d1070-105">Azure CDN(Content Delivery Network)은 전략적으로 배치된 위치에서 정적 웹 콘텐츠를 캐싱하여 사용자에게 콘텐츠를 배달하기 위한 최대 처리량을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d1070-105">The Azure Content Delivery Network (CDN) caches static web content at strategically placed locations to provide maximum throughput for delivering content to users.</span></span> <span data-ttu-id="d1070-106">CDN은 전 세계 물리적 노드에 콘텐츠를 캐시하여 고대역폭 콘텐츠를 배달하기 위한 글로벌 솔루션을 개발자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d1070-106">The CDN offers developers a global solution for delivering high-bandwidth content by caching the content at physical nodes across the world.</span></span>

<span data-ttu-id="d1070-107">Azure CDN에 대한 자세한 내용은 [Azure CDN(Content Delivery Network) 개요](https://docs.microsoft.com/azure/cdn/cdn-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1070-107">To learn more about Azure CDN, see [Overview of the Azure Content Delivery Network](https://docs.microsoft.com/azure/cdn/cdn-overview).</span></span>


## <a name="management-library"></a><span data-ttu-id="d1070-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="d1070-108">Management library</span></span>

<span data-ttu-id="d1070-109">.NET용 Azure CDN 라이브러리를 사용하여 CDN 프로필 및 엔드포인트의 생성과 관리를 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1070-109">You can use the Azure CDN Library for .NET to automate creation and management of CDN profiles and endpoints.</span></span> 

<span data-ttu-id="d1070-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d1070-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="d1070-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="d1070-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Cdn.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Cdn.Fluent
```

### <a name="example"></a><span data-ttu-id="d1070-112">예</span><span class="sxs-lookup"><span data-stu-id="d1070-112">Example</span></span>

<span data-ttu-id="d1070-113">이 예제에서는 `www.contoso.com`을 가리키는 새 엔드포인트를 사용하여 새 CDN 프로필을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1070-113">This example creates a new CDN profile with a new endpoint pointed to `www.contoso.com`.</span></span>

```csharp
/* Include these "using" directives.
using Microsoft.Azure.Management.Cdn.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

ICdnProfile profileDefinition = azure.CdnProfiles.Define("CdnProfileName")
    .WithRegion(Region.USCentral)
    .WithExistingResourceGroup("ResourceGroupName")
    .WithStandardVerizonSku()
    .WithNewEndpoint("www.contoso.com")
    .Create();

```

> [!div class="nextstepaction"]
> [<span data-ttu-id="d1070-114">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="d1070-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/cdn/management)


## <a name="samples"></a><span data-ttu-id="d1070-115">샘플</span><span class="sxs-lookup"><span data-stu-id="d1070-115">Samples</span></span>

* [<span data-ttu-id="d1070-116">CDN 시작 - CDN 관리 - .NET에서(영문)</span><span class="sxs-lookup"><span data-stu-id="d1070-116">Getting started with CDN - Manage CDN - in .NET</span></span>](https://github.com/Azure-Samples/cdn-dotnet-manage-cdn)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
