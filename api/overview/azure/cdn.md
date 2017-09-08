---
title: ".NET용 Azure CDN 라이브러리"
description: ".NET용 Azure CDN 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, CDN
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/31/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: cdn
ms.openlocfilehash: 1582f85c6e25a973fdf0294afb4393e6622e92a0
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-cdn-libraries-for-net"></a><span data-ttu-id="00552-104">.NET용 Azure CDN 라이브러리</span><span class="sxs-lookup"><span data-stu-id="00552-104">Azure CDN libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="00552-105">개요</span><span class="sxs-lookup"><span data-stu-id="00552-105">Overview</span></span>

<span data-ttu-id="00552-106">Azure CDN(Content Delivery Network)은 전략적으로 배치된 위치에서 정적 웹 콘텐츠를 캐싱하여 사용자에게 콘텐츠를 배달하기 위한 최대 처리량을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="00552-106">The Azure Content Delivery Network (CDN) caches static web content at strategically placed locations to provide maximum throughput for delivering content to users.</span></span> <span data-ttu-id="00552-107">CDN은 전 세계 물리적 노드에 콘텐츠를 캐시하여 고대역폭 콘텐츠를 배달하기 위한 글로벌 솔루션을 개발자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="00552-107">The CDN offers developers a global solution for delivering high-bandwidth content by caching the content at physical nodes across the world.</span></span>

<span data-ttu-id="00552-108">Azure CDN에 대한 자세한 내용은 [Azure CDN(Content Delivery Network) 개요](https://docs.microsoft.com/azure/cdn/cdn-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00552-108">To learn more about Azure CDN, see [Overview of the Azure Content Delivery Network](https://docs.microsoft.com/azure/cdn/cdn-overview).</span></span>


## <a name="management-library"></a><span data-ttu-id="00552-109">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="00552-109">Management library</span></span>

<span data-ttu-id="00552-110">.NET용 Azure CDN 라이브러리를 사용하여 CDN 프로필 및 끝점의 생성과 관리를 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00552-110">You can use the Azure CDN Library for .NET to automate creation and management of CDN profiles and endpoints.</span></span> 

<span data-ttu-id="00552-111">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="00552-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="00552-112">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="00552-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Cdn.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Cdn.Fluent
```

### <a name="example"></a><span data-ttu-id="00552-113">예제</span><span class="sxs-lookup"><span data-stu-id="00552-113">Example</span></span>

<span data-ttu-id="00552-114">이 예제에서는 `www.contoso.com`을 가리키는 새 끝점을 사용하여 새 CDN 프로필을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00552-114">This example creates a new CDN profile with a new endpoint pointed to `www.contoso.com`.</span></span>

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
> [<span data-ttu-id="00552-115">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="00552-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/cdn/management)


## <a name="samples"></a><span data-ttu-id="00552-116">샘플</span><span class="sxs-lookup"><span data-stu-id="00552-116">Samples</span></span>

* [<span data-ttu-id="00552-117">CDN 시작 - CDN 관리 - .NET에서(영문)</span><span class="sxs-lookup"><span data-stu-id="00552-117">Getting started with CDN - Manage CDN - in .NET</span></span>](https://github.com/Azure-Samples/cdn-dotnet-manage-cdn)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
