---
title: ".NET용 Azure Service Fabric 라이브러리"
description: ".NET용 Azure Service Fabric 라이브러리에 대한 참조"
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
---
# <a name="azure-service-fabric-libraries-for-net"></a>.NET용 Azure Service Fabric 라이브러리

## <a name="overview"></a>개요

Azure Service Fabric은 손쉽게 패키지하고 배포하며 확장 가능하고 안정성이 뛰어난 마이크로 서비스 및 컨테이너를 관리하도록 배포된 시스템 플랫폼입니다.  자세한 내용은 [Azure Service Fabric 설명서](/azure/service-fabric/)를 참조하세요.

## <a name="client-library"></a>클라이언트 라이브러리

Service Fabric 클라이언트 라이브러리를 사용하여 기존 Service Fabric 클러스터와 상호 작용합니다.  라이브러리에는 세 가지 범주의 API가 포함되어 있습니다.

* **클라이언트** API는 클러스터를 관리하고, 크기를 조정하고 재활용할 뿐만 아니라 응용 프로그램 패키지를 배포하는 데 사용됩니다.
* **런타임** API는 실행 중인 응용 프로그램에서 해당 호스팅 클러스터와 상호 작용하는 데 사용됩니다.
* **공통** API는 **클라이언트** 및 **런타임** API 모두에 사용되는 형식을 포함합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.ServiceFabric)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.ServiceFabric
```

```bash
dotnet add package Microsoft.ServiceFabric
```

### <a name="code-examples"></a>코드 예제

다음 예제에서는 Service Fabric **클라이언트** API를 사용하여 응용 프로그램 패키지를 이미지 저장소에 복사하고 응용 프로그램 형식을 프로비전하며 응용 프로그램 인스턴스를 만듭니다.

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
> [클라이언트 API 탐색](/dotnet/api/overview/azure/servicefabric/client)

이 예제에서는 Service Fabric **런타임** 및 **공통** API를 사용하여 런타임 시 [신뢰할 수 있는 컬렉션](/azure/service-fabric/service-fabric-reliable-services-reliable-collections)을 업데이트합니다.

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
> [런타임 API 탐색](/dotnet/api/overview/azure/servicefabric/runtime)

> [!div class="nextstepaction"]
> [공통 API 탐색](/dotnet/api/overview/azure/servicefabric/common)

## <a name="management-library"></a>관리 라이브러리

관리 라이브러리는 Service Fabric 클러스터를 만들고, 업데이트하고, 삭제하는 데 사용됩니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceFabric)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.ServiceFabric
```

```bash
dotnet add package Microsoft.Azure.Management.ServiceFabric
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/servicefabric/management)

## <a name="samples"></a>샘플

* [FabricClient를 사용하여 응용 프로그램 배포 및 제거](/azure/service-fabric/service-fabric-deploy-remove-applications-fabricclient)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
