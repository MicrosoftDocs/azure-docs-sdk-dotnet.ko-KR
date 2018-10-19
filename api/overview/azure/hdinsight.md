---
title: Azure HDInsight .NET SDK
description: Azure HDInsight .NET SDK 참조
ms.date: 9/19/2018
ms.topic: reference
ms.service: hdinsight
ms.openlocfilehash: 35e2c8c07fb2b86b2d0ae9be4f855e369c1aa86d
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348205"
---
# <a name="azure-hdinsight-net-sdk"></a><span data-ttu-id="38496-103">Azure HDInsight .NET SDK</span><span class="sxs-lookup"><span data-stu-id="38496-103">Azure HDInsight .NET SDK</span></span>

## <a name="azure-hdinsight-libraries-for-net-2x"></a><span data-ttu-id="38496-104">.NET 2.X용 Azure HDInsight 라이브러리</span><span class="sxs-lookup"><span data-stu-id="38496-104">Azure HDInsight libraries for .NET 2.X</span></span>

## <a name="overview"></a><span data-ttu-id="38496-105">개요</span><span class="sxs-lookup"><span data-stu-id="38496-105">Overview</span></span>

<span data-ttu-id="38496-106">HDInsight Service .NET SDK는 Azure HDInsight Service에서 관리하는 Hadoop 작업의 생성, 구성, 전송 및 모니터링과 관련된 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-106">The HDInsight Service .NET SDK provides classes that relate to the creation, configuration, submission, and monitoring of Hadoop jobs managed by an Azure HDInsight Service.</span></span> <span data-ttu-id="38496-107">또한 HDInsight Service를 사용하여 Azure 구독을 관리하고, Azure 구독에서 관리하는 HDInsight 클러스터와 관련된 기타 자산, 저장소 계정 및 클러스터를 구성하는 클래스도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-107">In addition, it provides classes to manage Azure subscriptions using the HDInsight Service and to configure the clusters, storage accounts, and other assets associated with the HDInsight clusters that are managed by an Azure subscription.</span></span>

## <a name="management-libraries"></a><span data-ttu-id="38496-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="38496-108">Management libraries</span></span>

### <a name="jobs"></a><span data-ttu-id="38496-109">교육</span><span class="sxs-lookup"><span data-stu-id="38496-109">Jobs</span></span>

<span data-ttu-id="38496-110">Azure HDInsight 클라이언트 SDK를 사용하여 Hadoop 클러스터에서 작업을 만들고 관리하며 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-110">Use the Azure HDInsight client SDK to create, manage, and monitor jobs on a Hadoop cluster.</span></span> 

<span data-ttu-id="38496-111">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="38496-112">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="38496-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight.Job
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight.Job
```

#### <a name="code-example"></a><span data-ttu-id="38496-113">코드 예제</span><span class="sxs-lookup"><span data-stu-id="38496-113">Code Example</span></span>

<span data-ttu-id="38496-114">이 예제는 Hadoop 클러스터에서 Hive 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-114">This example runs a Hive job in a Hadoop cluster.</span></span>

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

### <a name="hdinsight"></a><span data-ttu-id="38496-115">HDInsight</span><span class="sxs-lookup"><span data-stu-id="38496-115">HDInsight</span></span>

<span data-ttu-id="38496-116">Azure HDInsight 관리 SDK를 사용하여 Hadoop 클러스터를 만들고, 관리하며, 시작 및 중지하고 크기를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-116">Use the Azure HDInsight management SDK to create, manage, start, stop, and scale Hadoop clusters.</span></span>

<span data-ttu-id="38496-117">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="38496-118">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="38496-118">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.HDInsight
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight
```

#### <a name="code-example"></a><span data-ttu-id="38496-119">코드 예제</span><span class="sxs-lookup"><span data-stu-id="38496-119">Code Example</span></span>

<span data-ttu-id="38496-120">이 예에서는 기존 Azure Blob Storage와 함께 HDInsight 2노드 Linux Hadoop 클러스터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38496-120">This example creates an HDInsight two node Linux Hadoop cluster with an existing Azure Blob Storage.</span></span>

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
> [<span data-ttu-id="38496-121">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="38496-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/hdinsights/management)


## <a name="samples"></a><span data-ttu-id="38496-122">샘플</span><span class="sxs-lookup"><span data-stu-id="38496-122">Samples</span></span>

- [<span data-ttu-id="38496-123">클러스터 만들기</span><span class="sxs-lookup"><span data-stu-id="38496-123">Cluster creation</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-create-linux-clusters-dotnet-sdk)
- [<span data-ttu-id="38496-124">클러스터 관리</span><span class="sxs-lookup"><span data-stu-id="38496-124">Cluster management</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-administer-use-dotnet-sdk)
- [<span data-ttu-id="38496-125">Hive 작업 실행</span><span class="sxs-lookup"><span data-stu-id="38496-125">Run Hive jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-hive-dotnet-sdk)
- [<span data-ttu-id="38496-126">Pig 작업 실행</span><span class="sxs-lookup"><span data-stu-id="38496-126">Run Pig jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-pig-dotnet-sdk)
- [<span data-ttu-id="38496-127">더 많은 작업</span><span class="sxs-lookup"><span data-stu-id="38496-127">More jobs</span></span>](https://docs.microsoft.com/azure/hdinsight/hdinsight-submit-hadoop-jobs-programmatically)

<span data-ttu-id="38496-128">Azure SQL Database 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="38496-128">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight) of Azure SQL Database samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package

## <a name="hdinsight-net-management-sdk-3x-preview"></a><span data-ttu-id="38496-129">HDInsight .NET 관리 SDK 3.X 미리 보기</span><span class="sxs-lookup"><span data-stu-id="38496-129">HDInsight .NET Management SDK 3.X Preview</span></span>

## <a name="overview"></a><span data-ttu-id="38496-130">개요</span><span class="sxs-lookup"><span data-stu-id="38496-130">Overview</span></span>

<span data-ttu-id="38496-131">HDInsight .NET SDK는 HDInsight 클러스터 관리를 위한 클래스 및 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-131">The HDInsight .NET SDK provides classes and methods that allow you to manage your HDInsight clusters.</span></span> <span data-ttu-id="38496-132">여기에는 HDInsight 클러스터의 속성 만들기, 삭제, 업데이트, 나열, 크기 조정, 스크립트 작업 실행, 모니터링, 가져오기 작업을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-132">It includes operations to create, delete, update, list, resize, execute script actions, monitor, get properties of HDInsight clusters, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="38496-133">필수 조건</span><span class="sxs-lookup"><span data-stu-id="38496-133">Prerequisites</span></span>

* <span data-ttu-id="38496-134">Azure 계정.</span><span class="sxs-lookup"><span data-stu-id="38496-134">An Azure account.</span></span> <span data-ttu-id="38496-135">계정이 없으면 [체험 계정을 얻습니다](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="38496-135">If you don't have one, [get a free trial](https://azure.microsoft.com/free/).</span></span>
* [<span data-ttu-id="38496-136">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="38496-136">Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/)

## <a name="sdk-installation"></a><span data-ttu-id="38496-137">SDK 설치</span><span class="sxs-lookup"><span data-stu-id="38496-137">SDK Installation</span></span>

<span data-ttu-id="38496-138">Visual Studio 프로젝트에서 **도구**, **NuGet 패키지 관리자**를 클릭하여 패키지 고나리자 콘솔을 연 후 **패키지 관리자 콘솔**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-138">From your Visual Studio project, open the Package Manager Console by clicking **Tools**, **NuGet Package Manager**, and then click **Package Manager Console**.</span></span>

<span data-ttu-id="38496-139">패키지 관리자 콘솔에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-139">In the Package Manager Console, execute the following commands:</span></span>

```
  Install-Package Microsoft.Azure.Management.HDInsight -Version 3.1.0-preview
  Install-Package Microsoft.Azure.Management.Fluent
  Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

## <a name="authentication"></a><span data-ttu-id="38496-140">인증</span><span class="sxs-lookup"><span data-stu-id="38496-140">Authentication</span></span>

<span data-ttu-id="38496-141">Azure 구독을 사용해서 SDK를 먼저 인증해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-141">The SDK first needs to be authenticated with your Azure subscription.</span></span>  <span data-ttu-id="38496-142">아래 예제에 따라 서비스 주체를 만들고 이를 인증에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-142">Follow the example below to create a service principal and use it to authenticate.</span></span> <span data-ttu-id="38496-143">완료되었으면 관리 작업 수행을 위해 사용할 수 있는 여러 메서드(아래 섹션 참조)가 포함된 `HDInsightManagementClient` 인스턴스가 준비됩니다.</span><span class="sxs-lookup"><span data-stu-id="38496-143">After this is done, you will have an instance of an `HDInsightManagementClient`, which contains many methods (outlined in below sections) that can be used to perform management operations.</span></span>

> [!NOTE]
> <span data-ttu-id="38496-144">아래 설명된 예제 외에도 사용자 요구에 더 적합할 수 있는 다른 인증 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-144">There are other ways to authenticate besides the below example that could potentially be better suited for your needs.</span></span> <span data-ttu-id="38496-145">모든 메서드는 여기에 설명됩니다. [.NET용 Azure 라이브러리로 인증](https://docs.microsoft.com/en-us/dotnet/azure/dotnet-sdk-azure-authenticate?view=azure-dotnet)</span><span class="sxs-lookup"><span data-stu-id="38496-145">All methods are outlined here: [Authenticate with the Azure Libraries for .NET](https://docs.microsoft.com/en-us/dotnet/azure/dotnet-sdk-azure-authenticate?view=azure-dotnet)</span></span>

### <a name="authentication-example-using-a-service-principal"></a><span data-ttu-id="38496-146">서비스 주체를 사용한 인증 예제</span><span class="sxs-lookup"><span data-stu-id="38496-146">Authentication Example Using a Service Principal</span></span>

<span data-ttu-id="38496-147">먼저, [Azure Cloud Shell](https://shell.azure.com/bash)에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-147">First, login to [Azure Cloud Shell](https://shell.azure.com/bash).</span></span> <span data-ttu-id="38496-148">서비스 주체를 만들려는 구독을 현재 사용하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-148">Verify you are currently using the subscription in which you want the service principal created.</span></span> 

```azurecli-interactive
az account show
```

<span data-ttu-id="38496-149">구독 정보는 JSON으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38496-149">Your subscription information is displayed as JSON.</span></span>

```json
{
  "environmentName": "AzureCloud",
  "id": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "isDefault": true,
  "name": "XXXXXXX",
  "state": "Enabled",
  "tenantId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "user": {
    "cloudShellID": true,
    "name": "XXX@XXX.XXX",
    "type": "user"
  }
}
```

<span data-ttu-id="38496-150">올바른 구독으로 로그인되지 않은 경우 다음을 실행하여 올바른 구독을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-150">If you're not logged into the correct subscription, select the correct one by running:</span></span> 
```azurecli-interactive
az account set -s <name or ID of subscription>
```

> [!IMPORTANT]
> <span data-ttu-id="38496-151">Azure Portal을 통해 HDInsight Cluster를 만드는 등 다른 방법을 사용해서 HDInsight Resource Provider를 등록하지 않은 경우, 이를 먼저 수행해야 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-151">If you have not already registered the HDInsight Resource Provider by another method (such as by creating an HDInsight Cluster through the Azure Portal), you need to do this once before you can authenticate.</span></span> <span data-ttu-id="38496-152">이 작업은 [Azure Cloud Shell](https://shell.azure.com/bash)에서 다음 명령을 실행하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-152">This can be done from the [Azure Cloud Shell](https://shell.azure.com/bash) by running the following command:</span></span>
>```azurecli-interactive
>az provider register --namespace Microsoft.HDInsight
>```

<span data-ttu-id="38496-153">그런 다음 서비스 주체 이름을 선택하고 다음 명령을 사용해서 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38496-153">Next, choose a name for your service principal and create it with the following command:</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name <Service Principal Name> --sdk-auth
```

<span data-ttu-id="38496-154">서비스 주체 정보는 JSON으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38496-154">The service principal information is displayed as JSON.</span></span>

```json
{
  "clientId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "clientSecret": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "subscriptionId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "tenantId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
```
<span data-ttu-id="38496-155">아래 코드 조각을 복사하고 서비스 주체를 만들기 위해 명령을 실행한 후 반환된 JSON 문자열을 `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET` 및 `SUBSCRIPTION_ID`에 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="38496-155">Copy the below snippet and fill in `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET`, and `SUBSCRIPTION_ID` with the strings from the JSON that was returned after running the command to create the service principal.</span></span>

```csharp
using Microsoft.Azure.Management.HDInsight;
using Microsoft.Azure.Management.HDInsight.Models;
using Microsoft.Azure.Management.ResourceManager.Fluent;

namespace HDI_SDK_Test
{
    class Program
    {
        static void Main(string[] args)
        {
            // Tenant ID for your Azure Subscription
            var TENANT_ID = "";
            // Your Service Principal App Client ID
            var CLIENT_ID = "";
            // Your Service Principal Client Secret
            var CLIENT_SECRET = "";
            // Azure Subscription ID
            var SUBSCRIPTION_ID = "";

            var credentials = SdkContext.AzureCredentialsFactory
                .FromServicePrincipal(
                CLIENT_ID,
                CLIENT_SECRET,
                TENANT_ID,
                AzureEnvironment.AzureGlobalCloud);

            var client = new HDInsightManagementClient(credentials);
            client.SubscriptionId = SUBSCRIPTION_ID;
        }
    }
}
```


## <a name="cluster-management"></a><span data-ttu-id="38496-156">클러스터 관리</span><span class="sxs-lookup"><span data-stu-id="38496-156">Cluster Management</span></span>

> [!NOTE]
> <span data-ttu-id="38496-157">이 섹션에서는 이미 인증이 수행되었고 `HDInsightManagementClient` 인스턴스가 생성되었으며, `client`라는 변수로 저장되었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-157">This section assumes you have already authenticated and constructed an `HDInsightManagementClient` instance and store it in a variable called `client`.</span></span> <span data-ttu-id="38496-158">`HDInsightManagementClient` 인증 및 가져오기 지침은 위에 표시된 인증 섹션에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-158">Instructions for authenticating and obtaining an `HDInsightManagementClient` can be found in the Authentication section above.</span></span>

### <a name="create-a-cluster"></a><span data-ttu-id="38496-159">클러스터 만들기</span><span class="sxs-lookup"><span data-stu-id="38496-159">Create a Cluster</span></span>

<span data-ttu-id="38496-160">`client.Clusters.Create()`을(를) 호출하여 새 클러스터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-160">A new cluster can be created by calling `client.Clusters.Create()`.</span></span> 

#### <a name="example"></a><span data-ttu-id="38496-161">예</span><span class="sxs-lookup"><span data-stu-id="38496-161">Example</span></span>

<span data-ttu-id="38496-162">이 예제에서는 2개의 헤드 노드 및 1개의 작업자 노드를 사용하여 Spark 클러스터를 만드는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="38496-162">This example demonstrates how to create a Spark cluster with 2 head nodes and 1 worker node.</span></span>

> [!NOTE]
> <span data-ttu-id="38496-163">먼저 아래 설명된 대로 리소스 그룹 및 저장소 계정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-163">You first need to create a Resource Group and Storage Account, as explained below.</span></span> <span data-ttu-id="38496-164">이미 만든 경우에는 이 단계를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-164">If you have already created these, you can skip these steps.</span></span>

##### <a name="creating-a-resource-group"></a><span data-ttu-id="38496-165">리소스 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="38496-165">Creating a Resource Group</span></span>

<span data-ttu-id="38496-166">다음을 실행하여 [Azure Cloud Shell](https://shell.azure.com/bash)을 사용해서 리소스 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-166">You can create a resource group using the [Azure Cloud Shell](https://shell.azure.com/bash) by running</span></span>
```azurecli-interactive
az group create -l <Region Name (i.e. eastus)> --n <Resource Group Name>
```
##### <a name="creating-a-storage-account"></a><span data-ttu-id="38496-167">저장소 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="38496-167">Creating a Storage Account</span></span>

<span data-ttu-id="38496-168">다음을 실행하여 [Azure Cloud Shell](https://shell.azure.com/bash)을 사용해서 저장소 계정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-168">You can create a storage account using the [Azure Cloud Shell](https://shell.azure.com/bash) by running:</span></span>
```azurecli-interactive
az storage account create -n <Storage Account Name> -g <Existing Resource Group Name> -l <Region Name (i.e. eastus)> --sku <SKU i.e. Standard_LRS>
```
<span data-ttu-id="38496-169">이제 다음 명령을 사용해서 저장소 계정에 대한 키를 가져옵니다(클러스터를 만들기 위해 필요).</span><span class="sxs-lookup"><span data-stu-id="38496-169">Now run the following command to get the key for your storage account (you will need this to create a cluster):</span></span>
```azurecli-interactive
az storage account keys list -n <Storage Account Name>
```
---
<span data-ttu-id="38496-170">아래의 .NET 코드 조각은 2개의 헤드 노드 및 1개의 작업자 노드를 사용해서 Spark 클러스터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38496-170">The below .NET snippet creates a Spark cluster with 2 head nodes and 1 worker node.</span></span> <span data-ttu-id="38496-171">주석 설명에 따라 빈 변수를 채우고 특정 요구에 따라 다른 매개변수를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-171">Fill in the blank variables as explained in the comments and feel free to change other parameters to suit your specific needs.</span></span>

```csharp
// The name for the cluster you are creating
var clusterName = "";
// The name of your existing Resource Group
var resourceGroupName = "";
// Choose a username
var username = "";
// Choose a password
var password = "";
// Replace <> with the name of your storage account
var storageAccount = "<>.blob.core.windows.net";
// Storage account key you obtained above
var storageAccountKey = "";
// Choose a region
var location = "";
var container = "default";

var parameters = new ClusterCreateParametersExtended
{
    Location = location,
    Tags = new Dictionary<string, string>(),
    Properties = new ClusterCreateProperties
    {
        ClusterVersion = "3.6",
        OsType = OSType.Linux,
        ClusterDefinition = new ClusterDefinition
        {
            Kind = "Hadoop",            
            Configurations = new Dictionary<string, Dictionary<string, string>>()
            {                
                { "gateway", new Dictionary<string, string>
                    {
                        { "restAuthCredential.isEnabled", "true" },
                        { "restAuthCredential.username", username},
                        { "restAuthCredential.password", password}
                    }
                }
            }
        },
        Tier = Tier.Standard,
        ComputeProfile = new ComputeProfile
        {
            Roles = new List<Role>{
                new Role
                {
                    Name = "headnode",
                    TargetInstanceCount = 2,
                    HardwareProfile = new HardwareProfile
                    {
                        VmSize = "Large"
                    },
                    OsProfile = new OsProfile
                    {
                        LinuxOperatingSystemProfile = new LinuxOperatingSystemProfile
                        {
                            Username = username,
                            Password = password
                        }
                    }
                },
                new Role
                {
                    Name = "workernode",
                    TargetInstanceCount = 1,
                    HardwareProfile = new HardwareProfile
                    {
                        VmSize = "Large"
                    },
                    OsProfile = new OsProfile
                    {
                        LinuxOperatingSystemProfile = new LinuxOperatingSystemProfile
                        {
                            Username = username,
                            Password = password
                        }
                    }
                },
            }
        },
        StorageProfile = new StorageProfile
        {
            Storageaccounts = new[]
            {
                new StorageAccount
                {
                    Name = storageAccount,
                    Key = storageAccountKey,
                    Container = container,
                    IsDefault = true
                }
            }
        }
    }
};
client.Clusters.Create(
    resourceGroupName,
    clusterName,
    parameters
);
```

### <a name="get-cluster-details"></a><span data-ttu-id="38496-172">클러스터 세부 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38496-172">Get Cluster Details</span></span>

<span data-ttu-id="38496-173">지정된 클러스터에 대한 속성을 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="38496-173">To get properties for a given cluster:</span></span>

```csharp
client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="38496-174">예</span><span class="sxs-lookup"><span data-stu-id="38496-174">Example</span></span>

<span data-ttu-id="38496-175">`get`을(를) 사용하여 클러스터 만들기가 성공했는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-175">You can use `get` to confirm that you have successfully created your cluster.</span></span>

```csharp
var myCluster = client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
Debug.WriteLine(myCluster.Name); //Prints the name of the cluster
Debug.WriteLine(myCluster.Id) //Prints the resource Id of the cluster
```

<span data-ttu-id="38496-176">출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-176">The output should look like:</span></span>

```
<Cluster Name>
/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/<Resource Group Name>/providers/Microsoft.HDInsight/clusters/<Cluster Name>
```
> [!NOTE]
> <span data-ttu-id="38496-177">`myCluster` 변수에 저장된 `get`의 반환 값 유형은 `Microsoft.Azure.Management.HDInsight.ModelsCluster`입니다.</span><span class="sxs-lookup"><span data-stu-id="38496-177">The return value of `get`, stored in variable `myCluster`, is of type `Microsoft.Azure.Management.HDInsight.ModelsCluster`.</span></span> <span data-ttu-id="38496-178">이 개체 속성의 전체 목록은 [여기](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-178">A full list of this object's properties can be found [here](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview).</span></span>


### <a name="list-clusters"></a><span data-ttu-id="38496-179">클러스터 나열</span><span class="sxs-lookup"><span data-stu-id="38496-179">List Clusters</span></span>

#### <a name="list-clusters-under-the-subscription"></a><span data-ttu-id="38496-180">구독 아래에 클러스터 나열</span><span class="sxs-lookup"><span data-stu-id="38496-180">List Clusters Under The Subscription</span></span>

```csharp
client.Clusters.List();
```
#### <a name="list-clusters-by-resource-group"></a><span data-ttu-id="38496-181">리소스 그룹별로 클러스터 나열</span><span class="sxs-lookup"><span data-stu-id="38496-181">List Clusters By Resource Group</span></span>

```csharp
client.Clusters.ListByResourceGroup("<Resource Group Name>");
```
> [!NOTE]
> <span data-ttu-id="38496-182">`List()` 및 `ListByResourceGroup()` 모두 `IPage<Cluster>` 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-182">Both `List()` and `ListByResourceGroup()` return an `IPage<Cluster>` object.</span></span> <span data-ttu-id="38496-183">다음 페이지를 가져오려면 `client.Clusters.ListNext("Next Page Link")`을(를) 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-183">To get the next page, you can call `client.Clusters.ListNext("Next Page Link")`.</span></span> <span data-ttu-id="38496-184">이 작업은 아래 예제에 표시된 것처럼 `NextPageLink`이(가) `null`일 때까지 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-184">This can be repeated until `NextPageLink` is `null`, as shown in the example below.</span></span>

#### <a name="example"></a><span data-ttu-id="38496-185">예</span><span class="sxs-lookup"><span data-stu-id="38496-185">Example</span></span>
<span data-ttu-id="38496-186">다음 예제는 현재 구독에 대해 모든 클러스터 속성을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-186">The following example prints the properties of all clusters for the current subscription:</span></span>

```csharp
var clustersPaged = client.Clusters.List();
while (true)
{
  foreach (var cluster in clustersPaged)
  {
    Debug.WriteLine(cluster.Name);
  
}  if (clustersPaged.NextPageLink == null)
  {
    break;
  }
  clustersPaged = client.Clusters.ListNext(clustersPaged.NextPageLink);
}
```

### <a name="delete-a-cluster"></a><span data-ttu-id="38496-187">클러스터 삭제</span><span class="sxs-lookup"><span data-stu-id="38496-187">Delete a Cluster</span></span>

<span data-ttu-id="38496-188">클러스터를 삭제하려면:</span><span class="sxs-lookup"><span data-stu-id="38496-188">To delete a cluster:</span></span>

```csharp
client.Clusters.Delete("<Resource Group Name>", "<Cluster Name>");
```

### <a name="update-cluster-tags"></a><span data-ttu-id="38496-189">클러스터 태그 업데이트</span><span class="sxs-lookup"><span data-stu-id="38496-189">Update Cluster Tags</span></span>

<span data-ttu-id="38496-190">지정된 클러스터의 태그를 다음과 같이 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-190">You can update the tags of a given cluster like so:</span></span>

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(<Dictionary of Tags>));
```
#### <a name="example"></a><span data-ttu-id="38496-191">예</span><span class="sxs-lookup"><span data-stu-id="38496-191">Example</span></span>

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(new Dictionary<string, string> { { "tag1Name", "tag1Value" }, { "tag2Name", "tag2Value" } }));
```

### <a name="resize-cluster"></a><span data-ttu-id="38496-192">클러스터 크기 조정</span><span class="sxs-lookup"><span data-stu-id="38496-192">Resize Cluster</span></span>

<span data-ttu-id="38496-193">새 크기를 지정하여 작업자 노드의 지정된 클러스터 번호를 크기 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-193">You can resize a given cluster's number of worker nodes by specifying a new size like so:</span></span>

```csharp
client.Clusters.Resize("<Resource Group Name>", "<Cluster Name>", <Num of Worker Nodes (int)>)
```

## <a name="cluster-monitoring"></a><span data-ttu-id="38496-194">클러스터 모니터링</span><span class="sxs-lookup"><span data-stu-id="38496-194">Cluster Monitoring</span></span>

<span data-ttu-id="38496-195">또한 HDInsight 관리 SDK를 사용하여 OMS(Operations Management Suite)를 통해 클러스터에서 모니터링을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-195">The HDInsight Management SDK can also be used to manage monitoring on your clusters via the Operations Management Suite (OMS).</span></span>

### <a name="enable-oms-monitoring"></a><span data-ttu-id="38496-196">OMS 모니터링 사용</span><span class="sxs-lookup"><span data-stu-id="38496-196">Enable OMS Monitoring</span></span>

> [!NOTE]
> <span data-ttu-id="38496-197">OMS 모니터링을 사용하려면 기존 Log Analytics 작업 영역이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-197">To enable OMS Monitoring, you must have an existing Log Analytics workspace.</span></span> <span data-ttu-id="38496-198">아직 만들지 않았으면 [Azure Portal에서 Log Analytics 작업 영역 만들기](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-quick-create-workspace)에서 이를 수행하는 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-198">If you have not already created one, you can learn how to do that here: [Create a Log Analytics workspace in the Azure portal](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-quick-create-workspace).</span></span>

<span data-ttu-id="38496-199">클러스터에서 OMS 모니터링을 사용하려면:</span><span class="sxs-lookup"><span data-stu-id="38496-199">To enable OMS Monitoring on your cluster:</span></span>

```csharp
client.Extension.EnableMonitoring("<Resource Group Name", "Cluster Name", new ClusterMonitoringRequest(workspaceId: "<Workspace Id>"));
```

### <a name="view-status-of-oms-monitoring"></a><span data-ttu-id="38496-200">OMS 모니터링의 상태 보기</span><span class="sxs-lookup"><span data-stu-id="38496-200">View Status Of OMS Monitoring</span></span>

<span data-ttu-id="38496-201">클러스터에서 OMS 상태를 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="38496-201">To get the status of OMS on your cluster:</span></span>

```csharp
client.Extension.GetMonitoringStatus("<Resource Group Name", "Cluster Name");
```

### <a name="disable-oms-monitoring"></a><span data-ttu-id="38496-202">OMS 모니터링 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="38496-202">Disable OMS Monitoring</span></span>

<span data-ttu-id="38496-203">클러스터에서 OMS를 사용하지 않으려면:</span><span class="sxs-lookup"><span data-stu-id="38496-203">To disable OMS on your cluster:</span></span>

```csharp
client.Extension.DisableMonitoring("<Resource Group Name>", "<Cluster Name>");
```

## <a name="script-actions"></a><span data-ttu-id="38496-204">스크립트 동작</span><span class="sxs-lookup"><span data-stu-id="38496-204">Script Actions</span></span>

<span data-ttu-id="38496-205">HDInsight는 클러스터 사용자 지정을 위해 사용자 지정 스크립트를 호출하는 스크립트 작업이라고 부르는 구성 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-205">HDInsight provides a configuration method called script actions that invokes custom scripts to customize the cluster.</span></span>
> [!NOTE]
> <span data-ttu-id="38496-206">스크립트 작업 사용 방법에 대한 자세한 내용은 [스크립트 작업을 사용하여 Linux 기반 HDInsight 클러스터 사용자 지정](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-206">More information on how to use script actions can be found here: [Customize Linux-based HDInsight clusters using script actions](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)</span></span>

### <a name="execute-script-actions"></a><span data-ttu-id="38496-207">스크립트 작업 실행</span><span class="sxs-lookup"><span data-stu-id="38496-207">Execute Script Actions</span></span>

<span data-ttu-id="38496-208">지정된 클러스터에서 다음과 같이 스크립트 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-208">You can execute script actions on a given cluster like so:</span></span>

```csharp
var scriptAction1 = new RuntimeScriptAction("<Script Name>", "<URL To Script>", <List<string> of roles>); //valid roles are "headnode", "workernode", "zookeepernode", and "edgenode"

client.Clusters.ExecuteScriptActions("<Resource Group Name>", "<Cluster Name>", new List<RuntimeScriptAction> { scriptAction1 }, <persistOnSuccess (bool)>); //add more RuntimeScriptActions to the list to execute multiple scripts
```

### <a name="delete-script-action"></a><span data-ttu-id="38496-209">스크립트 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="38496-209">Delete Script Action</span></span>

<span data-ttu-id="38496-210">지정된 클러스터에서 지정된 지속형 스크립트 작업을 삭제하려면:</span><span class="sxs-lookup"><span data-stu-id="38496-210">To delete a specified persisted script action on a given cluster:</span></span>

```csharp
client.ScriptActions.Delete("<Resource Group Name>", "<Cluster Name>", "<Script Name>");
```

### <a name="list-persisted-script-actions"></a><span data-ttu-id="38496-211">지속형 스크립트 작업 나열</span><span class="sxs-lookup"><span data-stu-id="38496-211">List Persisted Script Actions</span></span>

> [!NOTE]
> <span data-ttu-id="38496-212">`ListPersistedScripts()` 및 `List()`은(는) `IPage<RuntimeScriptActionDetail>` 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-212">`ListPersistedScripts()` and `List()` return an `IPage<RuntimeScriptActionDetail>` object.</span></span> <span data-ttu-id="38496-213">다음 페이지를 가져오려면 `client.ScriptActions.ListPersistedScriptsNext("Next Page Link")` 또는 `client.ScriptExecutionHistory.ListNext("Next Page Link")`을(를) 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-213">To get the next page, you can call `client.ScriptActions.ListPersistedScriptsNext("Next Page Link")` or `client.ScriptExecutionHistory.ListNext("Next Page Link")`.</span></span> <span data-ttu-id="38496-214">이 작업은 아래 예제에 표시된 것처럼 `NextPageLink`이(가) `null`일 때까지 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38496-214">This can be repeated until `NextPageLink` is `null`, as shown in the examples below.</span></span>

<span data-ttu-id="38496-215">지정된 클러스터에 대해 모든 지속형 스크립트 작업을 나열하려면:</span><span class="sxs-lookup"><span data-stu-id="38496-215">To list all persisted script actions for the specified cluster:</span></span>
```csharp
client.ScriptActions.ListPersistedScripts("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="38496-216">예</span><span class="sxs-lookup"><span data-stu-id="38496-216">Example</span></span>

```csharp
var scriptsPaged = client.ScriptActions.ListPersistedScripts("<Resource Group Name>", "<Cluster Name>");
while (true)
{
    foreach (var script in scriptsPaged)
    {
        Debug.WriteLine(script.Name); //There are other properties of RuntimeScriptActionDetail besides Name, such as Status, Operation, StartTime, EndTime, etc. See reference documentation.
    }
    if (scriptsPaged.NextPageLink == null)
    {
        break;
    }
    scriptsPaged = client.ScriptActions.ListPersistedScriptsNext(scriptsPaged.NextPageLink);
}
```

### <a name="list-all-scripts-execution-history"></a><span data-ttu-id="38496-217">모든 스크립트 실행 기록 나열</span><span class="sxs-lookup"><span data-stu-id="38496-217">List All Scripts' Execution History</span></span>

<span data-ttu-id="38496-218">지정된 클러스터에 대해 모든 스크립트 실행 기록을 나열하려면:</span><span class="sxs-lookup"><span data-stu-id="38496-218">To list all scripts' execution history for the specified cluster:</span></span>

```csharp
client.script_execution_history.list("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a><span data-ttu-id="38496-219">예</span><span class="sxs-lookup"><span data-stu-id="38496-219">Example</span></span>

<span data-ttu-id="38496-220">이 예제는 모든 과거 스크립트 실행에 대한 모든 세부 정보를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="38496-220">This example prints all the details for all past script executions.</span></span>

```csharp
var scriptExecutionsPaged = client.ScriptExecutionHistory.List("<Resource Group Name>", "<Cluster Name>");
while (true)
{
    foreach (var script in scriptExecutionsPaged)
    {
        Debug.WriteLine(script.Name); //There are other properties of RuntimeScriptActionDetail besides Name, such as Status, Operation, StartTime, EndTime, etc. See reference documentation.

    }
    if (scriptExecutionsPaged.NextPageLink == null)
    {
        break;
    }
    scriptExecutionsPaged = client.ScriptExecutionHistory.ListNext(scriptExecutionsPaged.NextPageLink);
}
```
