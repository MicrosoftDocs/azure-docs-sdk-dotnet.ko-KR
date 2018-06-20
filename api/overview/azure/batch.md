---
title: .NET용 Azure Batch 라이브러리
description: .NET용 Azure Batch 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Batch
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: batch
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 79ca70e5d0f3d5555c8a691da6dbcc1e6a55ab0b
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2017
ms.locfileid: "23487266"
---
# <a name="azure-batch-libraries-for-net"></a><span data-ttu-id="c84e6-104">.NET용 Azure Batch 라이브러리</span><span class="sxs-lookup"><span data-stu-id="c84e6-104">Azure Batch libraries for .NET</span></span>

<span data-ttu-id="c84e6-105">Azure 배치는 클라우드에서 대규모 병렬 및 HPC(고성능 컴퓨팅) 응용 프로그램을 효율적으로 실행하기 위한 플랫폼 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-105">Azure Batch is a platform service for running large-scale parallel and high-performance computing (HPC) applications efficiently in the cloud.</span></span> <span data-ttu-id="c84e6-106">Azure 배치는 가상 컴퓨터의 관리되는 컬렉션에서 실행되는 계산 집약적 작업을 예약하고, 작업 요구에 맞게 계산 리소스의 규모를 자동으로 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-106">Azure Batch schedules compute-intensive work to run on a managed collection of virtual machines, and can automatically scale compute resources to meet the needs of your jobs.</span></span>

<span data-ttu-id="c84e6-107">Azure 배치를 사용하면 Azure 계산 리소스를 쉽게 정의하여 응용 프로그램을 병렬로 규모에 맞게 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-107">With Azure Batch, you can easily define Azure compute resources to execute your applications in parallel, and at scale.</span></span> <span data-ttu-id="c84e6-108">HPC 클러스터, 개별 가상 컴퓨터, 가상 네트워크 또는 복잡한 작업 및 태스크 예약 인프라를 수동으로 만들거나 구성하거나 관리할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-108">There's no need to manually create, configure, and manage an HPC cluster, individual virtual machines, virtual networks, or a complex job and task scheduling infrastructure.</span></span> <span data-ttu-id="c84e6-109">Azure 배치는 이러한 태스크를 자동화하거나 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-109">Azure Batch automates or simplifies these tasks for you.</span></span>

<span data-ttu-id="c84e6-110">[Batch를 사용하여 본질적인 병렬 워크로드를 실행](/azure/batch/batch-technical-overview)하는 방법에 대해 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="c84e6-110">Read more about how to [run intrinsically parallel workloads with Batch](/azure/batch/batch-technical-overview).</span></span> <span data-ttu-id="c84e6-111">[.NET용 Batch 클라이언트 라이브러리를 사용한 솔루션 빌드를 시작](/azure/batch/batch-dotnet-get-started)하는 방법에 대해 알아볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-111">You can also learn how to [get started building solutions with the Batch client library for .NET](/azure/batch/batch-dotnet-get-started).</span></span> <span data-ttu-id="c84e6-112">[.NET용 Batch 관리 라이브러리를 사용하여 Batch 계정 및 할당량을 관리](/azure/batch/batch-management-dotnet)하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-112">Discover how to [manage Batch accounts and quotas with the Batch Management library for .NET](/azure/batch/batch-management-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="c84e6-113">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="c84e6-113">Client library</span></span>

<span data-ttu-id="c84e6-114">클라이언트 라이브러리를 사용하여 Batch로 병렬 워크로드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-114">Use the client library to run parallel workloads with Batch.</span></span>

<span data-ttu-id="c84e6-115">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Azure.Batch)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-115">Install the [NuGet package](https://www.nuget.org/packages/Azure.Batch) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="c84e6-116">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="c84e6-116">Visual Studio Package Manager</span></span>

```powershell
Install-Package Azure.Batch
```

#### <a name="net-core-cli"></a><span data-ttu-id="c84e6-117">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="c84e6-117">.NET Core CLI</span></span>

```bash
dotnet add package Azure.Batch
```

### <a name="example"></a><span data-ttu-id="c84e6-118">예제</span><span class="sxs-lookup"><span data-stu-id="c84e6-118">Example</span></span>

<span data-ttu-id="c84e6-119">다음 예제에서는 클라이언트 SDK를 사용하여 Azure Batch에서 실행되도록 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-119">The following example uses the client SDK to create a job to run in Azure Batch.</span></span>

```csharp
/*
using Microsoft.Azure.Batch.Auth;
using Microsoft.Azure.Batch;
*/
BatchSharedKeyCredentials credentials = new BatchSharedKeyCredentials(batchUrl, accountName, accountKey);
using (BatchClient batchClient = await BatchClient.OpenAsync(credentials))
{
    //set up pool specification and information along with resource files here
    JobManagerTask jobManagerTask = new JobManagerTask()
    {
        ResourceFiles = jobManagerResourceFiles,
        CommandLine = Constants.JobManagerExecutable,

        //Determines if the job should terminate when the job manager process exits.
        KillJobOnCompletion = true,
        Id = jobManagerTaskId
    };

    string jobId = Environment.GetEnvironmentVariable("USERNAME") + DateTime.UtcNow.ToString("yyyyMMdd-HHmmss");

    CloudJob unboundJob = batchClient.JobOperations.CreateJob(jobId, poolInformation);
    unboundJob.JobManagerTask = jobManagerTask;

    // now interact with the job ...
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="c84e6-120">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="c84e6-120">Explore the client APIs</span></span>](/dotnet/api/overview/azure/batch/client)

## <a name="management-library"></a><span data-ttu-id="c84e6-121">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="c84e6-121">Management library</span></span>

<span data-ttu-id="c84e6-122">관리 라이브러리를 사용하여 Batch 계정, 할당량 및 응용 프로그램 패키지를 프로그래밍 방식으로 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-122">Use the management library to programmatically manage Batch accounts, quotas, and application packages.</span></span>

<span data-ttu-id="c84e6-123">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-123">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="c84e6-124">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="c84e6-124">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Batch
```

#### <a name="net-core-cli"></a><span data-ttu-id="c84e6-125">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="c84e6-125">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Batch
```

### <a name="example"></a><span data-ttu-id="c84e6-126">예제</span><span class="sxs-lookup"><span data-stu-id="c84e6-126">Example</span></span>

<span data-ttu-id="c84e6-127">다음 예제에서는 구독에 대한 할당량을 검색하고, 계정을 만들고, 기본 계정 키를 다시 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-127">The following example retrieves the quota for the subscription, creates an account, and regenerates the primary account key.</span></span>

```csharp
/*
using Microsoft.Azure.Management.Batch;
using Microsoft.Azure.Management.Batch.Models;
using Microsoft.Rest;
*/
using (BatchManagementClient batchManagementClient = new BatchManagementClient(new TokenCredentials(accessToken)))
{
    batchManagementClient.SubscriptionId = subscriptionId;

    // Get the account quota for the subscription
    BatchLocationQuota quotaResponse = await batchManagementClient.Location.GetQuotasAsync(location);
    Console.WriteLine("Your subscription can create {0} account(s) in the {1} region.", quotaResponse.AccountQuota, location);

    // Create account
    await batchManagementClient.BatchAccount.CreateAsync(ResourceGroupName, accountName, 
        new BatchAccountCreateParameters() { Location = location });

    // Regenerate primary account key
    BatchAccountKeys newKeys = await batchManagementClient.BatchAccount.RegenerateKeyAsync(
        ResourceGroupName, account.Name, AccountKeyType.Primary);
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="c84e6-128">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="c84e6-128">Explore the management APIs</span></span>](/dotnet/api/overview/azure/batch/management)

## <a name="samples"></a><span data-ttu-id="c84e6-129">샘플</span><span class="sxs-lookup"><span data-stu-id="c84e6-129">Samples</span></span>

* [<span data-ttu-id="c84e6-130">.NET용 Azure Batch 클라이언트 및 관리 SDK 샘플</span><span class="sxs-lookup"><span data-stu-id="c84e6-130">Azure Batch Client and Management SDK for .NET Samples</span></span>](https://github.com/Azure/azure-batch-samples/tree/master/CSharp)

<span data-ttu-id="c84e6-131">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c84e6-131">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
