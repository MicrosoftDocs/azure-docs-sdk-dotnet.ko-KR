---
title: .NET용 Azure Batch 라이브러리
description: .NET용 Azure Batch 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: batch
ms.openlocfilehash: 4220faacc9b8cbe394f98eaccd1e71aaf4ab8f0d
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190116"
---
# <a name="azure-batch-libraries-for-net"></a>.NET용 Azure Batch 라이브러리

Azure Batch는 클라우드에서 대규모 병렬 및 HPC(고성능 컴퓨팅) 응용 프로그램을 효율적으로 실행하기 위한 플랫폼 서비스입니다. Azure Batch는 가상 머신의 관리되는 컬렉션에서 실행되는 계산 집약적 작업을 예약하고, 작업 요구에 맞게 계산 리소스의 규모를 자동으로 조정할 수 있습니다.

Azure Batch를 사용하면 Azure 계산 리소스를 쉽게 정의하여 응용 프로그램을 병렬로 규모에 맞게 실행할 수 있습니다. HPC 클러스터, 개별 가상 머신, 가상 네트워크 또는 복잡한 작업 및 태스크 예약 인프라를 수동으로 만들거나 구성하거나 관리할 필요가 없습니다. Azure Batch는 이러한 태스크를 자동화하거나 단순화합니다.

[Batch를 사용하여 본질적인 병렬 워크로드를 실행](/azure/batch/batch-technical-overview)하는 방법에 대해 알아보세요. [.NET용 Batch 클라이언트 라이브러리를 사용한 솔루션 빌드를 시작](/azure/batch/batch-dotnet-get-started)하는 방법에 대해 알아볼 수도 있습니다. [.NET용 Batch 관리 라이브러리를 사용하여 Batch 계정 및 할당량을 관리](/azure/batch/batch-management-dotnet)하는 방법을 알아봅니다.

## <a name="client-library"></a>클라이언트 라이브러리

클라이언트 라이브러리를 사용하여 Batch로 병렬 워크로드를 실행합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Azure.Batch)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Azure.Batch
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Azure.Batch
```

### <a name="example"></a>예

다음 예제에서는 클라이언트 SDK를 사용하여 Azure Batch에서 실행되도록 작업을 만듭니다.

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
> [클라이언트 API 탐색](/dotnet/api/overview/azure/batch/client)

## <a name="management-library"></a>관리 라이브러리

관리 라이브러리를 사용하여 Batch 계정, 할당량 및 애플리케이션 패키지를 프로그래밍 방식으로 관리합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Batch)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Batch
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Management.Batch
```

### <a name="example"></a>예

다음 예제에서는 구독에 대한 할당량을 검색하고, 계정을 만들고, 기본 계정 키를 다시 생성합니다.

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
> [관리 API 탐색](/dotnet/api/overview/azure/batch/management)

## <a name="samples"></a>샘플

* [.NET용 Azure Batch 클라이언트 및 관리 SDK 샘플](https://github.com/Azure/azure-batch-samples/tree/master/CSharp)

앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
