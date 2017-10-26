---
title: "Azure .NET API 시작"
description: "Azure 구독을 사용하여 .NET용 Azure 라이브러리의 기본적인 사용을 시작합니다."
keywords: "Azure, .NET, SDK, API, 인증, 시작"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 80f796493362a84474f5913a26ad6802f68a4906
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
---
# <a name="get-started-with-the-azure-net-apis"></a>Azure .NET API 시작

이 자습서에서는 [.NET용 Azure API](/dotnet/api/overview/azure/)에 대한 몇 가지 사용 방법을 보여 줍니다.  인증을 설정하고, Azure Storage 계정을 만들어 사용하고, Azure SQL Database를 만들어 사용하고, 일부 가상 컴퓨터를 배포하고, GitHub에서 Azure App Service Web App을 배포합니다.

## <a name="prerequisites"></a>필수 조건

- Azure 계정. 계정이 없으면 [체험 계정을 얻습니다](https://azure.microsoft.com/free/).
- [Azure PowerShell](/powershell/azure/install-azurerm-ps)

## <a name="set-up-authentication"></a>인증 설정

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="create-a-new-project"></a>새 프로젝트 만들기 

새 콘솔 응용 프로그램 프로젝트를 만듭니다.  이렇게 하려면 Visual Studio에서 **파일**, **새로 만들기**, **프로젝트...**를 차례로 클릭합니다.  Visual C# 템플릿 아래에서 **콘솔 앱(.NET Core)**을 선택하고, 프로젝트 이름을 지정한 다음, **확인**을 클릭합니다.

![새 프로젝트 대화 상자](media/dotnet-sdk-azure-get-started/new-project.png)

새 콘솔 앱이 만들어지면 **도구**, **NuGet 패키지 관리자**, **패키지 관리자 콘솔**을 차례로 클릭하여 [패키지 관리자 콘솔]을 엽니다.  콘솔에서 다음 세 가지 명령을 실행하여 필요한 패키지를 가져옵니다.

```powershell
# Azure Management Libraries for .NET (Fluent)
Install-Package Microsoft.Azure.Management.Fluent

# Azure Store client libraries
Install-Package WindowsAzure.Storage

# SQL Database client libraries
Install-Package System.Data.SqlClient
```

## <a name="directives"></a>지시문

응용 프로그램의 `Program.cs` 파일을 편집합니다.  위에 있는 `using` 지시문을 다음 예제로 바꿉니다.

```csharp
using System;
using System.Linq;
using Microsoft.Azure.Management.Compute.Fluent;
using Microsoft.Azure.Management.Compute.Fluent.Models;
using Microsoft.Azure.Management.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Blob;
using System.Data.SqlClient;
```

## <a name="create-a-virtual-machine"></a>가상 컴퓨터 만들기

이 예제에서는 가상 컴퓨터를 배포합니다. 

`Main` 메서드를 다음 예제로 바꿉니다.  가상 컴퓨터에 실제 `username` 및 `password`를 제공해야 합니다.

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string username = "MY_USERNAME";
    string password = "MY_PASSWORD";
    string rgName = "sampleResourceGroup";
    string windowsVmName = "sampleWindowsVM";
    string publicIpDnsLabel = "samplePublicIP";

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .WithLogLevel(HttpLoggingDelegatingHandler.Level.Basic)
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the VM
    Console.WriteLine("Creating VM...");
    var windowsVM = azure.VirtualMachines.Define(windowsVmName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .WithNewPrimaryNetwork("10.0.0.0/28")
        .WithPrimaryPrivateIPAddressDynamic()
        .WithNewPrimaryPublicIPAddress(publicIpDnsLabel)
        .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
        .WithAdminUsername(username)
        .WithAdminPassword(password)
        .WithSize(VirtualMachineSizeTypes.StandardD2V2)
        .Create();

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();
}
```

**F5** 키를 눌러 샘플을 실행합니다.

몇 분 후에 프로그램이 완료되면 Enter 키를 누르라는 메시지가 표시됩니다. Enter 키를 누른 후에 PowerShell을 사용하여 구독 중인 가상 컴퓨터를 확인합니다.

```powershell
Get-AzureRmVm -ResourceGroupName sampleResourceGroup
```

## <a name="deploy-a-web-app-from-a-github-repo"></a>GitHub 리포지토리에서 웹앱 배포

이제 코드를 수정하여 기존 GitHub 리포지토리에서 새 웹앱을 배포합니다. `Main` 메서드를 다음 코드로 바꿉니다.

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string rgName = "sampleResourceGroup";
    string appName = SdkContext.RandomResourceName("WebApp", 20);

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the web app
    Console.WriteLine("Creating Web App...");
    var app = azure.WebApps.Define(appName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .WithNewFreeAppServicePlan()
        .DefineSourceControl()
        .WithPublicGitRepository("https://github.com/Azure-Samples/app-service-web-dotnet-get-started")
        .WithBranch("master")
        .Attach()
        .Create();
    Console.WriteLine("Your web app is live at: https://{0}", app.HostNames.First());

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();
}
```

**F5** 키를 눌러 이전과 같이 코드를 실행합니다.  브라우저를 열고 콘솔에 표시된 URL로 이동하여 배포를 확인합니다.

## <a name="connect-to-a-sql-database"></a>SQL 데이터베이스에 연결

이 예제에서는 새 Azure SQL Database를 만들고 몇 가지 SQL 작업을 수행합니다.

`Main` 메서드를 다음 예제로 바꾸고 `dbPassword`에 강력한 암호를 지정합니다.

```csharp
 static void Main(string[] args)
{
    // Set some variables...
    string rgName = "sampleResourceGroup";
    string adminUser = SdkContext.RandomResourceName("db", 8);
    string sqlServerName = SdkContext.RandomResourceName("sql", 10);
    string sqlDbName = SdkContext.RandomResourceName("dbname", 8);
    string dbPassword = "YOUR_PASSWORD_HERE";

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the SQL server and database
    Console.WriteLine("Creating server...");
    var sqlServer = azure.SqlServers.Define(sqlServerName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .WithAdministratorLogin(adminUser)
        .WithAdministratorPassword(dbPassword)
        .WithNewFirewallRule("0.0.0.0", "255.255.255.255")
        .Create();

    Console.WriteLine("Creating database...");
    var sqlDb = sqlServer.Databases.Define(sqlDbName).Create();
    
    // Display information for connecting later...
    Console.WriteLine("Created database {0} in server {1}.", sqlDbName, sqlServer.FullyQualifiedDomainName);
    Console.WriteLine("Your user name is {0}.", adminUser + "@" + sqlServer.Name);
    
    // Build the connection string
    var builder = new SqlConnectionStringBuilder();
    builder.DataSource = sqlServer.FullyQualifiedDomainName;
    builder.InitialCatalog = sqlDbName;
    builder.UserID = adminUser + "@" + sqlServer.Name; // Format user ID as "user@server"
    builder.Password = dbPassword;
    builder.Encrypt = true;
    builder.TrustServerCertificate = true;

    // connect to the database, create a table and insert an entry into it
    using (var conn = new SqlConnection(builder.ConnectionString))
    {
        conn.Open();

        Console.WriteLine("Populating database...");
        var createCommand = new SqlCommand("CREATE TABLE CLOUD (name varchar(255), code int);", conn);
        createCommand.ExecuteNonQuery();

        var insertCommand = new SqlCommand("INSERT INTO CLOUD (name, code ) VALUES ('Azure', 1);", conn);
        insertCommand.ExecuteNonQuery();

        Console.WriteLine("Reading from database...");
        var selectCommand = new SqlCommand("SELECT * FROM CLOUD", conn);
        var results = selectCommand.ExecuteReader();
        while(results.Read())
        {
            Console.WriteLine("Name: {0} Code: {1}", results[0], results[1]);
        }
    }

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();
}
```
**F5** 키를 눌러 이전과 같이 코드를 실행합니다.  콘솔 출력에서 서버가 만들어져 예상대로 작동하는지 확인해야 하지만, 원하는 경우 SQL Server Management Studio와 같은 도구를 사용하여 직접 연결할 수 있습니다.

## <a name="write-a-blob-into-a-new-storage-account"></a>새 저장소 계정에 Blob 쓰기

이 예제에서는 저장소 계정을 만들고 Blob을 업로드합니다.  

`Main` 메서드를 다음 예제로 바꿉니다.

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string rgName = "sampleResourceGroup";
    string storageAccountName = SdkContext.RandomResourceName("st", 10);

    // Authenticate
    var credentials = SdkContext.AzureCredentialsFactory
        .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

    var azure = Azure
        .Configure()
        .Authenticate(credentials)
        .WithDefaultSubscription();

    // Create the storage account
    Console.WriteLine("Creating storage account...");
    var storage = azure.StorageAccounts.Define(storageAccountName)
        .WithRegion(Region.USEast)
        .WithNewResourceGroup(rgName)
        .Create();

    var storageKeys = storage.GetKeys();
    string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

    var account = CloudStorageAccount.Parse(storageConnectionString);
    var serviceClient = account.CreateCloudBlobClient();
    
    // Create container. Name must be lower case.
    Console.WriteLine("Creating container...");
    var container = serviceClient.GetContainerReference("helloazure");
    container.CreateIfNotExistsAsync().Wait();

    // Make the container public
    var containerPermissions = new BlobContainerPermissions()
        { PublicAccess = BlobContainerPublicAccessType.Container };
    container.SetPermissionsAsync(containerPermissions).Wait();
    
    // write a blob to the container
    Console.WriteLine("Uploading blob...");
    var blob = container.GetBlockBlobReference("helloazure.txt");
    blob.UploadTextAsync("Hello, Azure!").Wait();
    Console.WriteLine("Your blob is located at {0}", blob.StorageUri.PrimaryUri);

    // Wait for the user
    Console.WriteLine("Press enter to continue...");
    Console.ReadLine();        
}
```

**F5** 키를 눌러 샘플을 실행합니다.

몇 분 후에 프로그램이 완료됩니다. 콘솔에 표시된 URL을 이동하여 Blob이 업로드되었는지 확인합니다.  브라우저에서 "Hello, Azure!" 텍스트가 표시됩니다.

## <a name="clean-up"></a>정리

> [!IMPORTANT]
> 이 자습서에서 리소스를 정리하지 않으면 요금이 계속 청구됩니다.  따라서 이 단계는 반드시 수행해야 합니다.

PowerShell에서 다음을 입력하여 만든 리소스를 모두 삭제합니다.

```powershell
Remove-AzureRmResourceGroup -ResourceGroupName sampleResourceGroup
```
## <a name="explore-more-samples"></a>더 많은 샘플 탐색

.NET용 Azure 라이브러리를 사용하여 리소스를 관리하고 작업을 자동화하는 방법에 대한 자세한 내용은 [가상 컴퓨터](dotnet-sdk-azure-virtual-machine-samples.md), [웹앱](dotnet-sdk-azure-web-apps-samples.md) 및 [SQL 데이터베이스](dotnet-sdk-azure-sql-database-samples.md)에 대한 샘플 코드를 참조하세요.

## <a name="reference"></a>참조

[참조](http://docs.microsoft.com/dotnet/api)는 모든 패키지에서 사용할 수 있습니다.

[!include[Contribute and community](includes/contribute.md)]
