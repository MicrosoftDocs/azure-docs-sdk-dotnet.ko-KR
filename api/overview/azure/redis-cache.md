---
title: .NET용 Azure Redis Cache 라이브러리
description: .NET용 Azure Redis Cache 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: redis-cache
ms.openlocfilehash: cc043bbc6ea5915f7b6c2265b606210efb72d9d0
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190526"
---
# <a name="azure-redis-cache-libraries-for-net"></a><span data-ttu-id="0ffca-103">.NET용 Azure Redis Cache 라이브러리</span><span class="sxs-lookup"><span data-stu-id="0ffca-103">Azure Redis Cache libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="0ffca-104">개요</span><span class="sxs-lookup"><span data-stu-id="0ffca-104">Overview</span></span>

<span data-ttu-id="0ffca-105">Azure Redis Cache는 응용 프로그램의 데이터에 대한 많은 처리량을 짧은 대기 시간 동안 처리할 수 있도록 하는 보안 데이터 캐시 및 메시징 broker입니다.</span><span class="sxs-lookup"><span data-stu-id="0ffca-105">Azure Redis Cache is a secure data cache and messaging broker that provides high throughput and low-latency access to data for applications.</span></span>  <span data-ttu-id="0ffca-106">자세한 내용은 [Redis Cache 사용 방법](https://docs.microsoft.com/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0ffca-106">For more information, see [How to Use Redis Cache](https://docs.microsoft.com/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache).</span></span>

## <a name="client-library"></a><span data-ttu-id="0ffca-107">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="0ffca-107">Client library</span></span>

<span data-ttu-id="0ffca-108">Azure Redis Cache는 `StackExchange.Redis`를 포함하여 모든 Redis 클라이언트 API와 호환 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="0ffca-108">Azure Redis Cache is compatible with any Redis client API, including `StackExchange.Redis`.</span></span>

<span data-ttu-id="0ffca-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/StackExchange.Redis)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0ffca-109">Install the [NuGet package](https://www.nuget.org/packages/StackExchange.Redis) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="0ffca-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="0ffca-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package StackExchange.Redis
```

```bash
dotnet add package StackExchange.Redis
```

### <a name="example"></a><span data-ttu-id="0ffca-111">예</span><span class="sxs-lookup"><span data-stu-id="0ffca-111">Example</span></span>

<span data-ttu-id="0ffca-112">이 예제에서는 Redis Cache 데이터베이스 인스턴스에 연결하고 이름으로 캐시에 일부 문자열을 추가한 후 다시 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0ffca-112">This example connects to a Redis Cache database instance, adds some strings to the cache by name, and then retrieves them again.</span></span>

```csharp
/* Include this "using" directive.
using StackExchange.Redis;
*/

ConnectionMultiplexer connection = 
    ConnectionMultiplexer.Connect("contoso.redis.cache.windows.net,abortConnect=false,ssl=true,password=...");
    IDatabase cache = connection.GetDatabase();

// Perform cache operations using the cache object...
// Simple put of integral data types into the cache
cache.StringSet("key1", "value");
cache.StringSet("key2", 25);

// Simple get of data types from the cache
string key1 = cache.StringGet("key1");
int key2 = (int)cache.StringGet("key2");
```

## <a name="management-library"></a><span data-ttu-id="0ffca-113">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="0ffca-113">Management library</span></span>

<span data-ttu-id="0ffca-114">Redis Cache 관리 라이브러리를 사용하면 Redis Cache 리소스를 관리하고 키에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ffca-114">The Redis Cache management library allows you to manage Redis Cache resources and access keys.</span></span>

<span data-ttu-id="0ffca-115">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Redis.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0ffca-115">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Redis.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="0ffca-116">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="0ffca-116">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Redis.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Redis.Fluent
```

### <a name="example"></a><span data-ttu-id="0ffca-117">예</span><span class="sxs-lookup"><span data-stu-id="0ffca-117">Example</span></span>

<span data-ttu-id="0ffca-118">이 예제에서는 새 Redis Cache를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0ffca-118">This example creates a new Redis Cache.</span></span>

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.Azure.Management.Redis.Fluent;
*/

IRedisCache redisCache1 = azure.RedisCaches.Define("RedisCacheName")
    .WithRegion(Region.USCentral)
    .WithNewResourceGroup("ResourceGroupName")
    .WithBasicSku()
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="0ffca-119">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="0ffca-119">Explore the management APIs</span></span>](/dotnet/api/overview/azure/rediscache/management)


## <a name="samples"></a><span data-ttu-id="0ffca-120">샘플</span><span class="sxs-lookup"><span data-stu-id="0ffca-120">Samples</span></span>

* [<span data-ttu-id="0ffca-121">Redis 시작 - .NET에서 Redis 관리</span><span class="sxs-lookup"><span data-stu-id="0ffca-121">Getting Started with Redis - Manage Redis - in .NET</span></span>](https://github.com/Azure-Samples/redis-cache-dotnet-manage-cache)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
