---
title: .NET용 Azure Service Fabric 라이브러리
description: .NET용 Azure Service Fabric 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Service Fabric
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: service-fabric
ms.custom: devcenter, svc-overview
ms.openlocfilehash: f4b54933d31a4e1fc4c390baa57469cc1c02783a
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
ms.locfileid: "23566100"
---
# <a name="azure-service-fabric-libraries-for-net"></a><span data-ttu-id="b89e5-104">.NET용 Azure Service Fabric 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b89e5-104">Azure Service Fabric libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b89e5-105">개요</span><span class="sxs-lookup"><span data-stu-id="b89e5-105">Overview</span></span>

<span data-ttu-id="b89e5-106">Azure Service Fabric은 손쉽게 패키지하고 배포하며 확장 가능하고 안정성이 뛰어난 마이크로 서비스 및 컨테이너를 관리하도록 배포된 시스템 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>  <span data-ttu-id="b89e5-107">자세한 내용은 [Azure Service Fabric 설명서](/azure/service-fabric/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b89e5-107">For more information, see the [Azure Service Fabric Documentation](/azure/service-fabric/).</span></span>

## <a name="client-library"></a><span data-ttu-id="b89e5-108">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b89e5-108">Client library</span></span>

<span data-ttu-id="b89e5-109">Service Fabric 클라이언트 라이브러리를 사용하여 기존 Service Fabric 클러스터와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-109">Use the Service Fabric client library to interact with an existing Service Fabric cluster.</span></span>  <span data-ttu-id="b89e5-110">라이브러리에는 세 가지 범주의 API가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-110">The library contains three categories of APIs:</span></span>

* <span data-ttu-id="b89e5-111">**클라이언트** API는 클러스터를 관리하고, 크기를 조정하고 재활용할 뿐만 아니라 응용 프로그램 패키지를 배포하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-111">**Client** APIs are used to manage, scale, and recycle the cluster, as well as deploy application packages.</span></span>
* <span data-ttu-id="b89e5-112">**런타임** API는 실행 중인 응용 프로그램에서 해당 호스팅 클러스터와 상호 작용하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-112">**Runtime** APIs are used for the running application to interact with its hosting cluster.</span></span>
* <span data-ttu-id="b89e5-113">**공통** API는 **클라이언트** 및 **런타임** API 모두에 사용되는 형식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-113">**Common** APIs contain types used in both **client** and **runtime** APIs.</span></span>

<span data-ttu-id="b89e5-114">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.ServiceFabric)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-114">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ServiceFabric) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b89e5-115">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="b89e5-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ServiceFabric
```

```bash
dotnet add package Microsoft.ServiceFabric
```

### <a name="code-examples"></a><span data-ttu-id="b89e5-116">코드 예제</span><span class="sxs-lookup"><span data-stu-id="b89e5-116">Code Examples</span></span>

<span data-ttu-id="b89e5-117">다음 예제에서는 Service Fabric **클라이언트** API를 사용하여 응용 프로그램 패키지를 이미지 저장소에 복사하고 응용 프로그램 형식을 프로비전하며 응용 프로그램 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-117">The following example uses the Service Fabric **client** APIs to copy an application package to the image store, provisions the application type, and create an application instance.</span></span>

```csharp
/* Include these dependencies
using System.Fabric;
using System.Fabric.Description;
*/

// Connect to the cluster.
FabricClient fabricClient = new FabricClient(clusterConnection);

// Copy the application package to a location in the image store
fabricClient.ApplicationManager.CopyApplicationPackage(imageStoreConnectionString, packagePath, packagePathInImageStore);

// Provision the application.
fabricClient.ApplicationManager.ProvisionApplicationAsync(packagePathInImageStore).Wait();

//  Create the application instance.
ApplicationDescription appDesc = new ApplicationDescription(new Uri(appName), appType, appVersion);
fabricClient.ApplicationManager.CreateApplicationAsync(appDesc).Wait();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b89e5-118">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="b89e5-118">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicefabric/client)

<span data-ttu-id="b89e5-119">이 예제에서는 Service Fabric **런타임** 및 **공통** API를 사용하여 런타임 시 [신뢰할 수 있는 컬렉션](/azure/service-fabric/service-fabric-reliable-services-reliable-collections)을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-119">This example uses the Service Fabric **runtime** and **common** APIs from within a hosted application to update a [Reliable Collection](/azure/service-fabric/service-fabric-reliable-services-reliable-collections) at runtime.</span></span>

```csharp
using System.Fabric;
using Microsoft.ServiceFabric.Data.Collections;
using Microsoft.ServiceFabric.Services.Communication.Runtime;
using Microsoft.ServiceFabric.Services.Runtime;

/// <summary>
/// This is the main entry point for your service replica.
/// This method executes when this replica of your service becomes primary and has write status.
/// </summary>
/// <param name="cancellationToken">Canceled when Service Fabric needs to shut down this service replica.</param>
protected override async Task RunAsync(CancellationToken cancellationToken)
{
    var myDictionary = await this.StateManager.GetOrAddAsync<IReliableDictionary<string, long>>("myDictionary");
    while (true)
    {
        cancellationToken.ThrowIfCancellationRequested();
        using (var tx = this.StateManager.CreateTransaction())
        {
            var result = await myDictionary.TryGetValueAsync(tx, "Counter");
            await myDictionary.AddOrUpdateAsync(tx, "Counter", 0, (key, value) => ++value);

            // If an exception is thrown before calling CommitAsync, the transaction aborts, all changes are
            // discarded, and nothing is saved to the secondary replicas.
            await tx.CommitAsync();
        }
        await Task.Delay(TimeSpan.FromSeconds(1), cancellationToken);
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b89e5-120">런타임 API 탐색</span><span class="sxs-lookup"><span data-stu-id="b89e5-120">Explore the runtime APIs</span></span>](/dotnet/api/overview/azure/servicefabric/runtime)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b89e5-121">공통 API 탐색</span><span class="sxs-lookup"><span data-stu-id="b89e5-121">Explore the common APIs</span></span>](/dotnet/api/overview/azure/servicefabric/common)

## <a name="management-library"></a><span data-ttu-id="b89e5-122">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b89e5-122">Management Library</span></span>

<span data-ttu-id="b89e5-123">관리 라이브러리는 Service Fabric 클러스터를 만들고, 업데이트하고, 삭제하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-123">The management library is used to create, update, and delete Service Fabric clusters.</span></span>

<span data-ttu-id="b89e5-124">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceFabric)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b89e5-124">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceFabric) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b89e5-125">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="b89e5-125">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ServiceFabric
```

```bash
dotnet add package Microsoft.Azure.Management.ServiceFabric
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b89e5-126">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="b89e5-126">Explore the management APIs</span></span>](/dotnet/api/overview/azure/servicefabric/management)

## <a name="samples"></a><span data-ttu-id="b89e5-127">샘플</span><span class="sxs-lookup"><span data-stu-id="b89e5-127">Samples</span></span>

* [<span data-ttu-id="b89e5-128">FabricClient를 사용하여 응용 프로그램 배포 및 제거</span><span class="sxs-lookup"><span data-stu-id="b89e5-128">Deploy and remove applications using FabricClient</span></span>](/azure/service-fabric/service-fabric-deploy-remove-applications-fabricclient)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
