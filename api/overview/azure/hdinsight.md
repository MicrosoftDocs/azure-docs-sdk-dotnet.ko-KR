---
title: Azure HDInsight .NET SDK
description: Azure HDInsight .NET SDK 참조
keywords: Azure, .NET, SDK, API, HDInsight
author: tylerfox
ms.author: tyfox
manager: arindamc
ms.date: 9/19/2018
ms.topic: reference
ms.devlang: dotnet
ms.service: hd-insight
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 1f85a9333d3008977137f271df9acb72bb7c17d7
ms.sourcegitcommit: a2c56781d52abbc09a5d56ca3103ed54545076a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46484588"
---
# <a name="azure-hdinsight-libraries-for-net-2x"></a>.NET 2.X용 Azure HDInsight 라이브러리

## <a name="overview"></a>개요

HDInsight Service .NET SDK는 Azure HDInsight Service에서 관리하는 Hadoop 작업의 생성, 구성, 전송 및 모니터링과 관련된 클래스를 제공합니다. 또한 HDInsight Service를 사용하여 Azure 구독을 관리하고, Azure 구독에서 관리하는 HDInsight 클러스터와 관련된 기타 자산, 저장소 계정 및 클러스터를 구성하는 클래스도 제공합니다.

## <a name="management-libraries"></a>관리 라이브러리

### <a name="jobs"></a>교육

Azure HDInsight 클라이언트 SDK를 사용하여 Hadoop 클러스터에서 작업을 만들고 관리하며 모니터링합니다. 

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight.Job)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.HDInsight.Job
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight.Job
```

#### <a name="code-example"></a>코드 예제

이 예제는 Hadoop 클러스터에서 Hive 작업을 실행합니다.

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

### <a name="hdinsight"></a>HDInsight

Azure HDInsight 관리 SDK를 사용하여 Hadoop 클러스터를 만들고, 관리하며, 시작 및 중지하고 크기를 조정합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.HDInsight)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.HDInsight
```

```bash
dotnet add package Microsoft.Azure.Management.HDInsight
```

#### <a name="code-example"></a>코드 예제

이 예에서는 기존 Azure Blob Storage와 함께 HDInsight 2노드 Linux Hadoop 클러스터를 만듭니다.

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
> [관리 API 탐색](/dotnet/api/overview/azure/hdinsights/management)


## <a name="samples"></a>샘플

- [클러스터 만들기](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-create-linux-clusters-dotnet-sdk)
- [클러스터 관리](https://docs.microsoft.com/azure/hdinsight/hdinsight-administer-use-dotnet-sdk)
- [Hive 작업 실행](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-hive-dotnet-sdk)
- [Pig 작업 실행](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-pig-dotnet-sdk)
- [더 많은 작업](https://docs.microsoft.com/azure/hdinsight/hdinsight-submit-hadoop-jobs-programmatically)

Azure SQL Database 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=hdinsight)을 봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package

# <a name="hdinsight-net-management-sdk-3x-preview"></a>HDInsight .NET 관리 SDK 3.X 미리 보기

## <a name="overview"></a>개요
HDInsight .NET SDK는 HDInsight 클러스터 관리를 위한 클래스 및 메서드를 제공합니다. 여기에는 HDInsight 클러스터의 속성 만들기, 삭제, 업데이트, 나열, 크기 조정, 스크립트 작업 실행, 모니터링, 가져오기 작업이 포함됩니다.

## <a name="prerequisites"></a>필수 조건
* Azure 계정. 계정이 없으면 [체험 계정을 얻습니다](https://azure.microsoft.com/free/).
* [Visual Studio](https://visualstudio.microsoft.com/downloads/)

## <a name="sdk-installation"></a>SDK 설치
Visual Studio 프로젝트에서 **도구**, **NuGet 패키지 관리자**를 클릭하여 패키지 고나리자 콘솔을 연 후 **패키지 관리자 콘솔**을 클릭합니다.

패키지 관리자 콘솔에서 다음 명령을 실행합니다.

```
  Install-Package Microsoft.Azure.Management.HDInsight -Version 3.1.0-preview
  Install-Package Microsoft.Azure.Management.Fluent
  Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

## <a name="authentication"></a>인증
Azure 구독을 사용해서 SDK를 먼저 인증해야 합니다.  아래 예제에 따라 서비스 주체를 만들고 이를 인증에 사용합니다. 완료되었으면 관리 작업 수행을 위해 사용할 수 있는 여러 메서드(아래 섹션 참조)가 포함된 `HDInsightManagementClient` 인스턴스가 준비됩니다.

> [!NOTE]
> 아래 설명된 예제 외에도 사용자 요구에 더 적합할 수 있는 다른 인증 방법이 있습니다. 모든 메서드는 여기에 설명됩니다. [.NET용 Azure 라이브러리로 인증](https://docs.microsoft.com/en-us/dotnet/azure/dotnet-sdk-azure-authenticate?view=azure-dotnet)

### <a name="authentication-example-using-a-service-principal"></a>서비스 주체를 사용한 인증 예제
먼저, [Azure Cloud Shell](https://shell.azure.com/bash)에 로그인합니다. 서비스 주체를 만들려는 구독을 현재 사용하고 있는지 확인합니다. 

```azurecli-interactive
az account show
```

구독 정보는 JSON으로 표시됩니다.

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

올바른 구독으로 로그인되지 않은 경우 다음을 실행하여 올바른 구독을 선택합니다. 
```azurecli-interactive
az account set -s <name or ID of subscription>
```

> [!IMPORTANT]
> Azure Portal을 통해 HDInsight Cluster를 만드는 등 다른 방법을 사용해서 HDInsight Resource Provider를 등록하지 않은 경우, 이를 먼저 수행해야 인증할 수 있습니다. 이 작업은 [Azure Cloud Shell](https://shell.azure.com/bash)에서 다음 명령을 실행하여 수행할 수 있습니다.
>```azurecli-interactive
>az provider register --namespace Microsoft.HDInsight
>```

그런 다음 서비스 주체 이름을 선택하고 다음 명령을 사용해서 만듭니다.

```azurecli-interactive
az ad sp create-for-rbac --name <Service Principal Name> --sdk-auth
```

서비스 주체 정보는 JSON으로 표시됩니다.

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
아래 코드 조각을 복사하고 서비스 주체를 만들기 위해 명령을 실행한 후 반환된 JSON 문자열을 `TENANT_ID`, `CLIENT_ID`, `CLIENT_SECRET` 및 `SUBSCRIPTION_ID`에 채웁니다.

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


## <a name="cluster-management"></a>클러스터 관리
> [!NOTE]
> 이 섹션에서는 이미 인증이 수행되었고 `HDInsightManagementClient` 인스턴스가 생성되었으며, `client`라는 변수로 저장되었다고 가정합니다. `HDInsightManagementClient` 인증 및 가져오기 지침은 위에 표시된 인증 섹션에서 찾을 수 있습니다.

### <a name="create-a-cluster"></a>클러스터 만들기
`client.Clusters.Create()`을(를) 호출하여 새 클러스터를 만들 수 있습니다. 

#### <a name="example"></a>예
이 예제에서는 2개의 헤드 노드 및 1개의 작업자 노드를 사용하여 Spark 클러스터를 만드는 방법을 보여줍니다.

> [!NOTE]
> 먼저 아래 설명된 대로 리소스 그룹 및 저장소 계정을 만들어야 합니다. 이미 만든 경우에는 이 단계를 건너뛸 수 있습니다.

##### <a name="creating-a-resource-group"></a>리소스 그룹 만들기
다음을 실행하여 [Azure Cloud Shell](https://shell.azure.com/bash)을 사용해서 리소스 그룹을 만들 수 있습니다.
```azurecli-interactive
az group create -l <Region Name (i.e. eastus)> --n <Resource Group Name>
```
##### <a name="creating-a-storage-account"></a>저장소 계정 만들기
다음을 실행하여 [Azure Cloud Shell](https://shell.azure.com/bash)을 사용해서 저장소 계정을 만들 수 있습니다.
```azurecli-interactive
az storage account create -n <Storage Account Name> -g <Existing Resource Group Name> -l <Region Name (i.e. eastus)> --sku <SKU i.e. Standard_LRS>
```
이제 다음 명령을 사용해서 저장소 계정에 대한 키를 가져옵니다(클러스터를 만들기 위해 필요).
```azurecli-interactive
az storage account keys list -n <Storage Account Name>
```
---
아래의 .NET 코드 조각은 2개의 헤드 노드 및 1개의 작업자 노드를 사용해서 Spark 클러스터를 만듭니다. 주석 설명에 따라 빈 변수를 채우고 특정 요구에 따라 다른 매개변수를 변경합니다.

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

### <a name="get-cluster-details"></a>클러스터 세부 정보 가져오기
지정된 클러스터에 대한 속성을 가져오려면:

```csharp
client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
```
https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview
#### <a name="example"></a>예
`get`을(를) 사용하여 클러스터 만들기가 성공했는지 확인할 수 있습니다.

```csharp
var myCluster = client.Clusters.Get("<Resource Group Name>", "<Cluster Name>");
Debug.WriteLine(myCluster.Name); //Prints the name of the cluster
Debug.WriteLine(myCluster.Id) //Prints the resource Id of the cluster
```

출력은 다음과 같습니다.

```
<Cluster Name>
/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/<Resource Group Name>/providers/Microsoft.HDInsight/clusters/<Cluster Name>
```
> [!NOTE]
> `myCluster` 변수에 저장된 `get`의 반환 값 유형은 `Microsoft.Azure.Management.HDInsight.ModelsCluster`입니다. 이 개체 속성의 전체 목록은 [여기](https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.management.hdinsight.models.cluster?view=azure-dotnet-preview)에서 찾을 수 있습니다.


### <a name="list-clusters"></a>클러스터 나열

#### <a name="list-clusters-under-the-subscription"></a>구독 아래에 클러스터 나열
```csharp
client.Clusters.List();
```
#### <a name="list-clusters-by-resource-group"></a>리소스 그룹별로 클러스터 나열
```csharp
client.Clusters.ListByResourceGroup("<Resource Group Name>");
```
> [!NOTE]
> `List()` 및 `ListByResourceGroup()` 모두 `IPage<Cluster>` 개체를 반환합니다. 다음 페이지를 가져오려면 `client.Clusters.ListNext("Next Page Link")`을(를) 호출할 수 있습니다. 이 작업은 아래 예제에 표시된 것처럼 `NextPageLink`이(가) `null`일 때까지 반복할 수 있습니다.

#### <a name="example"></a>예
다음 예제는 현재 구독에 대해 모든 클러스터 속성을 출력합니다.

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

### <a name="delete-a-cluster"></a>클러스터 삭제
클러스터를 삭제하려면:

```csharp
client.Clusters.Delete("<Resource Group Name>", "<Cluster Name>");
```

### <a name="update-cluster-tags"></a>클러스터 태그 업데이트
지정된 클러스터의 태그를 다음과 같이 업데이트할 수 있습니다.

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(<Dictionary of Tags>));
```
#### <a name="example"></a>예

```csharp
client.Clusters.Update("<Resource Group Name>", "<Cluster Name>", new ClusterPatchParameters(new Dictionary<string, string> { { "tag1Name", "tag1Value" }, { "tag2Name", "tag2Value" } }));
```

### <a name="scale-cluster"></a>클러스터 크기 조정
새 크기를 지정하여 작업자 노드의 지정된 클러스터 번호를 크기 조정할 수 있습니다.

```csharp
client.Clusters.Resize("<Resource Group Name>", "<Cluster Name>", <Num of Worker Nodes (int)>)
```

## <a name="cluster-monitoring"></a>클러스터 모니터링
또한 HDInsight 관리 SDK를 사용하여 OMS(Operations Management Suite)를 통해 클러스터에서 모니터링을 관리할 수 있습니다.

### <a name="enable-oms-monitoring"></a>OMS 모니터링 사용

> [!NOTE]
> OMS 모니터링을 사용하려면 기존 Log Analytics 작업 영역이 있어야 합니다. 아직 만들지 않았으면 [Azure Portal에서 Log Analytics 작업 영역 만들기](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-quick-create-workspace)에서 이를 수행하는 방법을 확인할 수 있습니다.

클러스터에서 OMS 모니터링을 사용하려면:

```csharp
client.Extension.EnableMonitoring("<Resource Group Name", "Cluster Name", new ClusterMonitoringRequest(workspaceId: "<Workspace Id>"));
```

### <a name="view-status-of-oms-monitoring"></a>OMS 모니터링의 상태 보기
클러스터에서 OMS 상태를 가져오려면:

```csharp
client.Extension.GetMonitoringStatus("<Resource Group Name", "Cluster Name");
```

### <a name="disable-oms-monitoring"></a>OMS 모니터링 사용 안 함
클러스터에서 OMS를 사용하지 않으려면:

```csharp
client.Extension.DisableMonitoring("<Resource Group Name>", "<Cluster Name>");
```

## <a name="script-actions"></a>스크립트 동작
HDInsight는 클러스터 사용자 지정을 위해 사용자 지정 스크립트를 호출하는 스크립트 작업이라고 부르는 구성 메서드를 제공합니다.
> [!NOTE]
> 스크립트 작업 사용 방법에 대한 자세한 내용은 [스크립트 작업을 사용하여 Linux 기반 HDInsight 클러스터 사용자 지정](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)에서 확인할 수 있습니다.

### <a name="execute-script-actions"></a>스크립트 작업 실행
지정된 클러스터에서 다음과 같이 스크립트 작업을 실행할 수 있습니다.

```csharp
var scriptAction1 = new RuntimeScriptAction("<Script Name>", "<URL To Script>", <List<string> of roles>); //valid roles are "headnode", "workernode", "zookeepernode", and "edgenode"

client.Clusters.ExecuteScriptActions("<Resource Group Name>", "<Cluster Name>", new List<RuntimeScriptAction> { scriptAction1 }, <persistOnSuccess (bool)>); //add more RuntimeScriptActions to the list to execute multiple scripts
```

### <a name="delete-script-action"></a>스크립트 작업 삭제
지정된 클러스터에서 지정된 지속형 스크립트 작업을 삭제하려면:

```csharp
client.ScriptActions.Delete("<Resource Group Name>", "<Cluster Name>", "<Script Name>");
```

### <a name="list-persisted-script-actions"></a>지속형 스크립트 작업 나열

> [!NOTE]
> `ListPersistedScripts()` 및 `List()`은(는) `IPage<RuntimeScriptActionDetail>` 개체를 반환합니다. 다음 페이지를 가져오려면 `client.ScriptActions.ListPersistedScriptsNext("Next Page Link")` 또는 `client.ScriptExecutionHistory.ListNext("Next Page Link")`을(를) 호출할 수 있습니다. 이 작업은 아래 예제에 표시된 것처럼 `NextPageLink`이(가) `null`일 때까지 반복할 수 있습니다.

지정된 클러스터에 대해 모든 지속형 스크립트 작업을 나열하려면:
```csharp
client.ScriptActions.ListPersistedScripts("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a>예

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

### <a name="list-all-scripts-execution-history"></a>모든 스크립트 실행 기록 나열
지정된 클러스터에 대해 모든 스크립트 실행 기록을 나열하려면:

```csharp
client.script_execution_history.list("<Resource Group Name>", "<Cluster Name>");
```

#### <a name="example"></a>예
이 예제는 모든 과거 스크립트 실행에 대한 모든 세부 정보를 출력합니다.

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
