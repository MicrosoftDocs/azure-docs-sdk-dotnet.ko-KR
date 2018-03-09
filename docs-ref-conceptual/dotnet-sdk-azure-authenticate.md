---
title: ".NET용 Azure 라이브러리를 사용하여 인증"
description: ".NET용 Azure 라이브러리에 대한 인증"
keywords: "Azure, .NET, SDK, API, 인증, Active Directory, 서비스 사용자"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 783b5ebf14abad992c18726df7232e4f3a68b72b
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2018
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a><span data-ttu-id="712e0-104">.NET용 Azure 라이브러리를 사용하여 인증</span><span class="sxs-lookup"><span data-stu-id="712e0-104">Authenticate with the Azure Libraries for .NET</span></span>

## <a name="connect-to-services-with-connection-strings"></a><span data-ttu-id="712e0-105">연결 문자열을 사용하여 서비스에 연결</span><span class="sxs-lookup"><span data-stu-id="712e0-105">Connect to services with connection strings</span></span>

<span data-ttu-id="712e0-106">대부분의 Azure 서비스 라이브러리에는 인증을 위한 연결 문자열 또는 보안 키가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-106">Most Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="712e0-107">예를 들어 SQL Database에서는 표준 SQL 연결 문자열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-107">For example, SQL Database uses a standard SQL connection string:</span></span>

```csharp
var builder = new SqlConnectionStringBuilder();
builder.DataSource = "example.database.windows.net";
builder.InitialCatalog = "MyDatabase";
builder.UserID = "sampleuser@example"; // Format user ID as "user@server"
builder.Password = password;
builder.Encrypt = true;
builder.TrustServerCertificate = true;
                
using (var conn = new SqlConnection(builder.ConnectionString))
{
    conn.Open();
    // Do things with the connection...
    // ...
}
```

<span data-ttu-id="712e0-108">Azure Storage에서는 저장소 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-108">Azure Storage uses a storage key:</span></span>

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

<span data-ttu-id="712e0-109">서비스 연결 문자열은 [CosmosDB](/azure/documentdb/documentdb-dotnet-application#a-nametoc395637769astep-5-wiring-up-azure-cosmos-db), [Redis Cache](/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache) 및 [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues)와 같은 다른 Azure 서비스에서 사용되며, Azure Portal, CLI 또는 PowerShell을 사용하여 해당 문자열을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-109">Service connection strings are used in other Azure services like [CosmosDB](/azure/documentdb/documentdb-dotnet-application#a-nametoc395637769astep-5-wiring-up-azure-cosmos-db), [Redis Cache](/azure/redis-cache/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues) and you can get those strings using the Azure portal, CLI, or PowerShell.</span></span>  <span data-ttu-id="712e0-110">또한 .NET용 Azure 관리 라이브러리를 사용하여 코드에서 연결 문자열을 작성하는 리소스를 쿼리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-110">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span> 

<span data-ttu-id="712e0-111">이 코드 조각에서는 관리 라이브러리를 사용하여 저장소 계정 연결 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-111">This snippet uses the management libraries to create a storage account connection string:</span></span>

```csharp
// Get a storage account
var storage = azure.StorageAccounts.GetByResourceGroup("myResourceGroup", "myStorageAccount");

// Extract the keys
var storageKeys = storage.GetKeys();

// Build the connection string
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

// Connect
var account = CloudStorageAccount.Parse(storageConnectionString);

// Do things with the account here...
```

<span data-ttu-id="712e0-112">다른 라이브러리에서는 권한이 부여된 자격 증명을 사용하여 응용 프로그램 실행 권한을 부여하는 [서비스 사용자](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects)를 통해 응용 프로그램을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-112">Other libraries require your application to run with a [service principal](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) authorizing the application to run with granted credentials.</span></span> <span data-ttu-id="712e0-113">이 구성은 아래에서 나열하는 관리 라이브러리에 대한 개체 기반 인증 단계와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-113">This configuration is similar to the object-based authentication steps for the management library listed below.</span></span>

## <a name="mgmt-auth"></a><span data-ttu-id="712e0-114">.NET 인증에 대한 Azure 관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="712e0-114">Azure management libraries for .NET authentication</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="712e0-115">이제 서비스 사용자를 만들었으므로 두 가지 옵션을 사용하여 리소스를 만들고 관리할 서비스 사용자를 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-115">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="712e0-116">두 옵션에서는 모두 다음과 같은 NuGet 패키지를 프로젝트에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-116">For both options you will need to add the following nuget packages to your project.</span></span>

```
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="712e0-117">토큰 자격 증명을 사용하여 인증</span><span class="sxs-lookup"><span data-stu-id="712e0-117">Authenticate with token credentials</span></span>

<span data-ttu-id="712e0-118">첫 번째 방법은 코드에 토큰 자격 증명 개체를 작성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-118">The first method is to build the token credential object in code.</span></span>  <span data-ttu-id="712e0-119">구성 파일, 레지스트리 또는 Azure Key Vault에 자격 증명을 안전하게 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-119">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId, 
    AzureEnvironment.AzureGlobalCloud);
```

- <span data-ttu-id="712e0-120">clientId: 서비스 사용자 출력의 *ApplicationId* 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-120">clientId: use the *ApplicationId* value from the service principal output.</span></span>
- <span data-ttu-id="712e0-121">clientSecret: `New-AzureRmADServicePrincipal`을 실행할 때 할당한 *-Password* 매개 변수를 사용합니다(따옴표 제외).</span><span class="sxs-lookup"><span data-stu-id="712e0-121">clientSecret: use the *-Password* parameter you assigned when you ran `New-AzureRmADServicePrincipal` (without quotes).</span></span>
- <span data-ttu-id="712e0-122">tenantId: `Login-AzureRmAccount`를 실행할 때의 *TenantId* 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-122">tenantId: use the *TenantId* value from when you ran `Login-AzureRmAccount`.</span></span>

<span data-ttu-id="712e0-123">그런 다음 `Azure` 진입점 개체를 만들어 API 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-123">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="mgmt-file"></a><span data-ttu-id="712e0-124">파일 기반 인증</span><span class="sxs-lookup"><span data-stu-id="712e0-124">File-based authentication</span></span>

<span data-ttu-id="712e0-125">파일 기반 인증을 사용하면 서비스 사용자 자격 증명을 일반 텍스트 파일에 저장하고 파일 시스템 내에서 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-125">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="712e0-126">파일의 내용을 읽고 `Azure` 끝점 개체를 만들어 API 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="712e0-126">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment 
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
