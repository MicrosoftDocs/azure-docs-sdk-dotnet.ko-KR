---
title: ".NET용 Azure Service Fabric 라이브러리"
description: ".NET용 Azure Service Fabric 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Service Fabric
author: spboyer
ms.author: casoper
manager: douge
ms.date: 07/07/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: c708ae06fa4b5165e3f615abf636b11bfd95cd3b
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-service-fabric-libraries-for-net"></a><span data-ttu-id="b32d6-104">.NET용 Azure Service Fabric 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b32d6-104">Azure Service Fabric libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b32d6-105">개요</span><span class="sxs-lookup"><span data-stu-id="b32d6-105">Overview</span></span>

<span data-ttu-id="b32d6-106">Azure Service Fabric은 손쉽게 패키지하고 배포하며 확장 가능하고 안정성이 뛰어난 마이크로 서비스 및 컨테이너를 관리하도록 배포된 시스템 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="b32d6-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

## <a name="client-library"></a><span data-ttu-id="b32d6-107">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b32d6-107">Client library</span></span>

<span data-ttu-id="b32d6-108">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.ServiceFabric)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b32d6-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.ServiceFabric) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b32d6-109">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="b32d6-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.ServiceFabric
```

```bash
dotnet add package Microsoft.ServiceFabric
```

### <a name="code-example"></a><span data-ttu-id="b32d6-110">코드 예제</span><span class="sxs-lookup"><span data-stu-id="b32d6-110">Code Example</span></span>

<span data-ttu-id="b32d6-111">다음 예제에서는 응용 프로그램 패키지를 이미지 저장소에 복사하고 응용 프로그램 유형을 프로비전하며 응용 프로그램 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32d6-111">The following example copies an application package to the image store, provisions the application type, and creates an application instance.</span></span>

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
> [<span data-ttu-id="b32d6-112">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="b32d6-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicefabric/client)

## <a name="samples"></a><span data-ttu-id="b32d6-113">샘플</span><span class="sxs-lookup"><span data-stu-id="b32d6-113">Samples</span></span>

* [<span data-ttu-id="b32d6-114">FabricClient를 사용하여 응용 프로그램 배포 및 제거</span><span class="sxs-lookup"><span data-stu-id="b32d6-114">Deploy and remove applications using FabricClient</span></span>](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-deploy-remove-applications-fabricclient)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
