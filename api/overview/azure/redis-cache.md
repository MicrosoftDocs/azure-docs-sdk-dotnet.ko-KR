---
title: .NET용 Azure Redis Cache 라이브러리
description: .NET용 Azure Redis Cache 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Redis Cache
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: redis-cache
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 64bb5a43cec8c82412b3dc7b60fea1e8566ab399
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
ms.locfileid: "23566344"
---
# <a name="azure-redis-cache-libraries-for-net"></a>.NET용 Azure Redis Cache 라이브러리

## <a name="overview"></a>개요

Azure Redis Cache는 응용 프로그램의 데이터에 대한 많은 처리량을 짧은 대기 시간 동안 처리할 수 있도록 하는 보안 데이터 캐시 및 메시징 broker입니다.  자세한 내용은 [Redis Cache 사용 방법](https://docs.microsoft.com/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache)을 참조하세요.

## <a name="client-library"></a>클라이언트 라이브러리

Azure Redis Cache는 `StackExchange.Redis`를 포함하여 모든 Redis 클라이언트 API와 호환 가능합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/StackExchange.Redis)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package StackExchange.Redis
```

```bash
dotnet add package StackExchange.Redis
```

### <a name="example"></a>예제

이 예제에서는 Redis Cache 데이터베이스 인스턴스에 연결하고 이름으로 캐시에 일부 문자열을 추가한 후 다시 검색합니다.

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

## <a name="management-library"></a>관리 라이브러리

Redis Cache 관리 라이브러리를 사용하면 Redis Cache 리소스를 관리하고 키에 액세스할 수 있습니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Redis.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Redis.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Redis.Fluent
```

### <a name="example"></a>예제

이 예제에서는 새 Redis Cache를 만듭니다.

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
> [관리 API 탐색](/dotnet/api/overview/azure/rediscache/management)


## <a name="samples"></a>샘플

* [Redis 시작 - .NET에서 Redis 관리](https://github.com/Azure-Samples/redis-cache-dotnet-manage-cache)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
