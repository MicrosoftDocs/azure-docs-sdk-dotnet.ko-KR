---
title: ".NET용 Azure HDInsight 라이브러리"
description: ".NET용 Azure HDInsight 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, HDInsight
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/21/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 3f0b6f48d89d582180193f52ce85c328e6bdf8e0
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-hdinsight-libraries-for-net"></a><span data-ttu-id="3f42c-104">.NET용 Azure HDInsight 라이브러리</span><span class="sxs-lookup"><span data-stu-id="3f42c-104">Azure HDInsight libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="3f42c-105">개요</span><span class="sxs-lookup"><span data-stu-id="3f42c-105">Overview</span></span>

<span data-ttu-id="3f42c-106">HDInsight Service .NET SDK는 Azure HDInsight Service에서 관리하는 Hadoop 작업의 생성, 구성, 전송 및 모니터링과 관련된 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3f42c-106">The HDInsight Service .NET SDK provides classes that relate to the creation, configuration, submission, and monitoring of Hadoop jobs managed by an Azure HDInsight Service.</span></span> <span data-ttu-id="3f42c-107">또한 HDInsight Service를 사용하여 Azure 구독을 관리하고, Azure 구독에서 관리하는 HDInsight 클러스터와 관련된 기타 자산, 저장소 계정 및 클러스터를 구성하는 클래스도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3f42c-107">In addition, it provides classes to manage Azure subscriptions using the HDInsight Service and to configure the clusters, storage accounts, and other assets associated with the HDInsight clusters that are managed by an Azure subscription.</span></span>

## <a name="management-libraries"></a><span data-ttu-id="3f42c-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="3f42c-108">Management libraries</span></span>

### <a name="jobs"></a><span data-ttu-id="3f42c-109">작업</span><span class="sxs-lookup"><span data-stu-id="3f42c-109">Jobs</span></span>

<span data-ttu-id="3f42c-110">Azure HDInsight 클라이언트 SDK를 사용하여 Hadoop 클러스터에서 작업을 만들고 관리하며 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="3f42c-110">Use the Azure HDInsight client SDK to create, manage, and monitor jobs on a Hadoop cluster.</span></span> 

<span data-ttu-id="3f42c-111">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3f42c-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="3f42c-112">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="3f42c-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight.Job
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight.Job
```

#### <a name="code-example"></a><span data-ttu-id="3f42c-113">코드 예제</span><span class="sxs-lookup"><span data-stu-id="3f42c-113">Code Example</span></span>

<span data-ttu-id="3f42c-114">이 예제는 Hadoop 클러스터에서 Hive 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f42c-114">This example runs a Hive job in a Hadoop cluster.</span></span>

```csharp
HDInsightJobManagementClient managementClient = new HDInsightJobManagementClient(clusterUri, credentials);

Dictionary<string, string> defines = new Dictionary<string, string> {
    { "hive.execution.engine", "tez" },
    { "hive.exec.reducers.max", "1" }
};
List<string> arguments = new List<string> { { "argA" }, { "argB" } };
HiveJobSubmissionParameters parameters = new HiveJobSubmissionParameters
{
    Query = "SHOW TABLES",
    Defines = defines,
    Arguments = arguments
};

JobSubmissionResponse jobResponse = managementClient.JobManagement.SubmitHiveJob(parameters);
```

### <a name="hdinsight"></a><span data-ttu-id="3f42c-115">HDInsight</span><span class="sxs-lookup"><span data-stu-id="3f42c-115">HDInsight</span></span>

<span data-ttu-id="3f42c-116">Azure HDInsight 관리 SDK를 사용하여 Hadoop 클러스터를 만들고, 관리하며, 시작 및 중지하고 크기를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f42c-116">Use the Azure HDInsight management SDK to create, manage, start, stop, and scale Hadoop clusters.</span></span>

<span data-ttu-id="3f42c-117">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3f42c-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="3f42c-118">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="3f42c-118">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight
```

#### <a name="code-example"></a><span data-ttu-id="3f42c-119">코드 예제</span><span class="sxs-lookup"><span data-stu-id="3f42c-119">Code Example</span></span>

<span data-ttu-id="3f42c-120">이 예에서는 기존 Azure Blob Storage와 함께 HDInsight 2노드 Linux Hadoop 클러스터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3f42c-120">This example creates an HDInsight two node Linux Hadoop cluster with an existing Azure Blob Storage.</span></span>

```csharp
HDInsightManagementClient managementClient = new HDInsightManagementClient(authToken);
// Set parameters for the new cluster
ClusterCreateParameters parameters = new ClusterCreateParameters
{
    ClusterSizeInNodes = 2,
    UserName = "admin",
    Password = "<Enter HTTP User Password>",
    ClusterType = "Hadoop",
    OSType = OSType.Linux,
    Version = "3.5",
    // Use an Azure storage account as the default storage
    DefaultStorageInfo = new AzureStorageInfo("<StorageAccount>", "<StorageKey>", "<BlobContainerName>"),
    Location = "EAST US 2",
    SshUserName = "sshuser",
    SshPassword = "<Enter SSH User Password>",
};

// Create the cluster
managementClient.Clusters.Create("<ExistingResourceGroupName>", "<NewClusterName>", parameters);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f42c-121">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="3f42c-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/hdinsights/management)


## <a name="samples"></a><span data-ttu-id="3f42c-122">샘플</span><span class="sxs-lookup"><span data-stu-id="3f42c-122">Samples</span></span>

- [<span data-ttu-id="3f42c-123">클러스터 만들기</span><span class="sxs-lookup"><span data-stu-id="3f42c-123">Cluster creation</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-create-linux-clusters-dotnet-sdk)
- [<span data-ttu-id="3f42c-124">클러스터 관리</span><span class="sxs-lookup"><span data-stu-id="3f42c-124">Cluster management</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-administer-use-dotnet-sdk)
- [<span data-ttu-id="3f42c-125">Hive 작업 실행</span><span class="sxs-lookup"><span data-stu-id="3f42c-125">Run Hive jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-hive-dotnet-sdk)
- [<span data-ttu-id="3f42c-126">Pig 작업 실행</span><span class="sxs-lookup"><span data-stu-id="3f42c-126">Run Pig jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-pig-dotnet-sdk)
- [<span data-ttu-id="3f42c-127">더 많은 작업</span><span class="sxs-lookup"><span data-stu-id="3f42c-127">More jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-submit-hadoop-jobs-programmatically)

<span data-ttu-id="3f42c-128">Azure SQL Database 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3f42c-128">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) of Azure SQL Database samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
