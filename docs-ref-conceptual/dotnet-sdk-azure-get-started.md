---
title: Azure .NET 및 .NET Core API 시작
description: Azure 구독을 사용하여 .NET 및 .NET Core용 Azure 라이브러리의 기본적인 사용을 시작합니다.
keywords: Azure, .NET, .NET Core, ASP.NET, ASP.NET Core SDK, API, 인증, 시작
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 08/22/2018
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: ad894e47704fcccc83f7d02acb8e418b167993f9
ms.sourcegitcommit: b2a53a3aea9de6720bd975fb7fe4e722e9d182a3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42703056"
---
# <a name="get-started-with-the-azure-net-and-net-core-apis"></a><span data-ttu-id="116d3-104">Azure .NET 및 .NET Core API 시작</span><span class="sxs-lookup"><span data-stu-id="116d3-104">Get started with the Azure .NET and .NET Core APIs</span></span>

<span data-ttu-id="116d3-105">이 자습서에서는 [.NET용 Azure API](/dotnet/api/overview/azure/)에 대한 몇 가지 사용 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-105">This tutorial demonstrates the usage of several [Azure APIs for .NET](/dotnet/api/overview/azure/).</span></span>  <span data-ttu-id="116d3-106">인증을 설정하고, Azure Storage 계정을 만들어 사용하고, Azure SQL Database를 만들어 사용하고, 일부 가상 머신을 배포하고, GitHub에서 Azure App Service Web App을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-106">You will set up authentication, create and use an Azure Storage account, create and use an Azure SQL Database, deploy some virtual machines, and deploy an Azure App Service Web App from GitHub.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="116d3-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="116d3-107">Prerequisites</span></span>

- <span data-ttu-id="116d3-108">Azure 계정.</span><span class="sxs-lookup"><span data-stu-id="116d3-108">An Azure account.</span></span> <span data-ttu-id="116d3-109">계정이 없으면 [체험 계정을 얻습니다](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="116d3-109">If you don't have one, [get a free trial](https://azure.microsoft.com/free/)</span></span>

## <a name="set-up-authentication"></a><span data-ttu-id="116d3-110">인증 설정</span><span class="sxs-lookup"><span data-stu-id="116d3-110">Set up authentication</span></span>

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="create-a-new-project"></a><span data-ttu-id="116d3-111">새 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="116d3-111">Create a new project</span></span> 

<span data-ttu-id="116d3-112">새 콘솔 응용 프로그램 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-112">Create a new console application project.</span></span>  <span data-ttu-id="116d3-113">이렇게 하려면 Visual Studio에서 **파일**, **새로 만들기**, **프로젝트...** 를 차례로 클릭합니다.  Visual C# 템플릿 아래에서 **콘솔 앱(.NET Core)** 을 선택하고, 프로젝트 이름을 지정한 다음, **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-113">In Visual Studio, do this by clicking **File**, **New**, and then clicking **Project...**.  Under the Visual C# templates, select **Console App (.NET Core)**, name your project, and then click **OK**.</span></span>

![새 프로젝트 대화 상자](media/dotnet-sdk-azure-get-started/new-project.png)

<span data-ttu-id="116d3-115">새 콘솔 앱이 만들어지면 **도구**, **NuGet 패키지 관리자**, **패키지 관리자 콘솔**을 차례로 클릭하여 [패키지 관리자 콘솔]을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-115">When the new console app is created, open the Package Manager Console by clicking **Tools**, **NuGet Package Manager**, and then click **Package Manager Console**.</span></span>  <span data-ttu-id="116d3-116">콘솔에서 다음 세 가지 명령을 실행하여 필요한 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-116">In the console, get the packages you'll need by executing the following three commands:</span></span>

```powershell
# Azure Management Libraries for .NET (Fluent)
Install-Package Microsoft.Azure.Management.Fluent

# Azure Store client libraries
Install-Package WindowsAzure.Storage

# SQL Database client libraries
Install-Package System.Data.SqlClient
```

## <a name="directives"></a><span data-ttu-id="116d3-117">지시문</span><span class="sxs-lookup"><span data-stu-id="116d3-117">Directives</span></span>

<span data-ttu-id="116d3-118">응용 프로그램의 `Program.cs` 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-118">Edit your application's `Program.cs` file.</span></span>  <span data-ttu-id="116d3-119">위에 있는 `using` 지시문을 다음 예제로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-119">Replace the `using` directives at the top with the following:</span></span>

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

## <a name="create-a-virtual-machine"></a><span data-ttu-id="116d3-120">가상 머신 만들기</span><span class="sxs-lookup"><span data-stu-id="116d3-120">Create a virtual machine</span></span>

<span data-ttu-id="116d3-121">이 예제에서는 가상 머신을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-121">This example deploys a virtual machine.</span></span> 

<span data-ttu-id="116d3-122">`Main` 메서드를 다음 예제로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-122">Replace the `Main` method with the following.</span></span>  <span data-ttu-id="116d3-123">가상 컴퓨터에 실제 `username` 및 `password`를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-123">Be sure to provide an actual `username` and `password` for the virtual machine.</span></span>

```csharp
static void Main(string[] args)
{
    // Set some variables...
    string username = "MY_USERNAME";
    string password = "MY_PASSWORD";
    string rgName = "sampleResourceGroup";
    string windowsVmName = "sampleWindowsVM";
    string publicIpDnsLabel = "samplePublicIP" + (new Random().Next(0,100000)).ToString();

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

<span data-ttu-id="116d3-124">**F5** 키를 눌러 샘플을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-124">Press **F5** to run the sample.</span></span>

<span data-ttu-id="116d3-125">몇 분 후에 프로그램이 완료되면 Enter 키를 누르라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-125">After several minutes, the program will finish, prompting you to press enter.</span></span> <span data-ttu-id="116d3-126">Enter 키를 누른 후에 Cloud Shell을 사용하여 구독 중인 가상 머신을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-126">After pressing enter, verify the virtual machine in your subscription with the Cloud Shell:</span></span>

```azurecli-interactive
az vm list
```

## <a name="deploy-a-web-app-from-a-github-repo"></a><span data-ttu-id="116d3-127">GitHub 리포지토리에서 웹앱 배포</span><span class="sxs-lookup"><span data-stu-id="116d3-127">Deploy a web app from a GitHub repo</span></span>

<span data-ttu-id="116d3-128">이제 코드를 수정하여 기존 GitHub 리포지토리에서 새 웹앱을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-128">Now you'll modify your code to create a deploy a new web app from an existing GitHub repository.</span></span> <span data-ttu-id="116d3-129">`Main` 메서드를 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-129">Replace the `Main` method with the following code:</span></span>

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

<span data-ttu-id="116d3-130">**F5** 키를 눌러 이전과 같이 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-130">Run the code as before by pressing **F5**.</span></span>  <span data-ttu-id="116d3-131">브라우저를 열고 콘솔에 표시된 URL로 이동하여 배포를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-131">Verify the deployment by opening a browser and navigating to URL displayed in the console.</span></span>

## <a name="connect-to-a-sql-database"></a><span data-ttu-id="116d3-132">SQL 데이터베이스에 연결</span><span class="sxs-lookup"><span data-stu-id="116d3-132">Connect to a SQL database</span></span>

<span data-ttu-id="116d3-133">이 예제에서는 새 Azure SQL Database를 만들고 몇 가지 SQL 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-133">This example creates a new Azure SQL Database and performs a few SQL operations.</span></span>

<span data-ttu-id="116d3-134">`Main` 메서드를 다음 예제로 바꾸고 `dbPassword`에 강력한 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-134">Replace the `Main` method with the following, making sure to assign a strong password for `dbPassword`:</span></span>

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

<span data-ttu-id="116d3-135">**F5** 키를 눌러 이전과 같이 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-135">Run the code as before by pressing **F5**.</span></span>  <span data-ttu-id="116d3-136">콘솔 출력에서 서버가 만들어져 예상대로 작동하는지 확인해야 하지만, 원하는 경우 SQL Server Management Studio와 같은 도구를 사용하여 직접 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-136">The console output should validate that the server was created and works as expected, but you can connect to it directly with a tool like SQL Server Management Studio if you like.</span></span>

## <a name="write-a-blob-into-a-new-storage-account"></a><span data-ttu-id="116d3-137">새 저장소 계정에 Blob 쓰기</span><span class="sxs-lookup"><span data-stu-id="116d3-137">Write a blob into a new storage account</span></span>

<span data-ttu-id="116d3-138">이 예제에서는 저장소 계정을 만들고 Blob을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-138">This example creates a storage account and upload a blob.</span></span>  

<span data-ttu-id="116d3-139">`Main` 메서드를 다음 예제로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-139">Replace the `Main` method with the following.</span></span>

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

<span data-ttu-id="116d3-140">**F5** 키를 눌러 샘플을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-140">Press **F5** to run the sample.</span></span>

<span data-ttu-id="116d3-141">몇 분 후에 프로그램이 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-141">After several minutes, the program finishes.</span></span> <span data-ttu-id="116d3-142">콘솔에 표시된 URL을 이동하여 Blob이 업로드되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-142">Verify the blob was uploaded by browsing to the URL displayed in the console.</span></span>  <span data-ttu-id="116d3-143">브라우저에서 "Hello, Azure!" 텍스트가</span><span class="sxs-lookup"><span data-stu-id="116d3-143">You should see the text "Hello, Azure!"</span></span> <span data-ttu-id="116d3-144">표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-144">in your browser.</span></span>

## <a name="clean-up"></a><span data-ttu-id="116d3-145">정리</span><span class="sxs-lookup"><span data-stu-id="116d3-145">Clean up</span></span>

> [!IMPORTANT]
> <span data-ttu-id="116d3-146">이 자습서에서 리소스를 정리하지 않으면 요금이 계속 청구됩니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-146">If you don't clean up your resources from this tutorial, you will continue to be charged for them.</span></span>  <span data-ttu-id="116d3-147">따라서 이 단계는 반드시 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-147">Be sure to do this step.</span></span>

<span data-ttu-id="116d3-148">Cloud Shell에서 다음을 입력하여 만든 리소스를 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-148">Delete all the resources you created by entering the following in the Cloud Shell:</span></span>

```azurecli-interactive
az group delete --name sampleResourceGroup
```

## <a name="explore-more-samples"></a><span data-ttu-id="116d3-149">더 많은 샘플 탐색</span><span class="sxs-lookup"><span data-stu-id="116d3-149">Explore more samples</span></span>

<span data-ttu-id="116d3-150">.NET용 Azure 라이브러리를 사용하여 리소스를 관리하고 작업을 자동화하는 방법에 대한 자세한 내용은 [가상 머신](dotnet-sdk-azure-virtual-machine-samples.md), [웹앱](dotnet-sdk-azure-web-apps-samples.md) 및 [SQL 데이터베이스](dotnet-sdk-azure-sql-database-samples.md)에 대한 샘플 코드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="116d3-150">To learn more about how to use the Azure libraries for .NET to manage resources and automate tasks, see our sample code for [virtual machines](dotnet-sdk-azure-virtual-machine-samples.md), [web apps](dotnet-sdk-azure-web-apps-samples.md) and [SQL database](dotnet-sdk-azure-sql-database-samples.md).</span></span>

## <a name="reference"></a><span data-ttu-id="116d3-151">참고 자료</span><span class="sxs-lookup"><span data-stu-id="116d3-151">Reference</span></span>

<span data-ttu-id="116d3-152">[참조](http://docs.microsoft.com/dotnet/api)는 모든 패키지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116d3-152">A [reference](http://docs.microsoft.com/dotnet/api) is available for all packages.</span></span>

[!include[Contribute and community](includes/contribute.md)]
