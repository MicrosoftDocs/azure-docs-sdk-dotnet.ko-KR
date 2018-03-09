---
title: "Azure .NET 저장소 API"
description: ".NET용 Azure Storage 라이브러리에 대한 참조"
keywords: "Azure, .NET, SDK, API, 저장소, Blob"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: storage
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 8f6e0414b54698d0a1dbe3d4c074456a6ad7b7be
ms.sourcegitcommit: dbec35008347b581dd238b882354300e427bec70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2018
---
# <a name="azure-storage-apis-for-net"></a><span data-ttu-id="afd3d-104">.NET용 Azure Storage API</span><span class="sxs-lookup"><span data-stu-id="afd3d-104">Azure Storage APIs for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="afd3d-105">개요</span><span class="sxs-lookup"><span data-stu-id="afd3d-105">Overview</span></span>

<span data-ttu-id="afd3d-106">[Azure Storage](https://review.docs.microsoft.com/azure/storage/storage-introduction)를 사용하여 .NET 응용 프로그램의 파일, Blob(개체) 데이터, 키-값 쌍 및 메시지를 읽고 씁니다.</span><span class="sxs-lookup"><span data-stu-id="afd3d-106">Read and write files, blob (object) data, key-value pairs, and messages from your .NET applications with [Azure Storage](https://review.docs.microsoft.com/azure/storage/storage-introduction).</span></span>

<span data-ttu-id="afd3d-107">Azure Storage를 시작하려면 [.NET을 사용하여 Azure Blob 저장소 시작](/azure/storage/storage-dotnet-how-to-use-blobs)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="afd3d-107">To get started with Azure Storage, see [Get started with Azure Blob storage using .NET](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="client-library"></a><span data-ttu-id="afd3d-108">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="afd3d-108">Client library</span></span>

<span data-ttu-id="afd3d-109">[연결 문자열](/azure/storage/storage-create-storage-account#manage-your-storage-account)을 사용하여 Azure Storage 계정에 연결한 다음, 클라이언트 라이브러리의 클래스와 메서드를 사용하여 Blob, 테이블, 파일 또는 큐 저장소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="afd3d-109">Use [connection strings](/azure/storage/storage-create-storage-account#manage-your-storage-account) to connect to an Azure Storage account, then use the client libraries' classes and methods to work with blob, table, file, or queue storage.</span></span>

<span data-ttu-id="afd3d-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/WindowsAzure.Storage)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="afd3d-110">Install the [NuGet package](https://www.nuget.org/packages/WindowsAzure.Storage) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="afd3d-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="afd3d-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package WindowsAzure.Storage
```

### <a name="net-core-cli"></a><span data-ttu-id="afd3d-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="afd3d-112">.NET Core CLI</span></span>

```bash
dotnet add package WindowsAzure.Storage
```

### <a name="code-example"></a><span data-ttu-id="afd3d-113">코드 예제</span><span class="sxs-lookup"><span data-stu-id="afd3d-113">Code Example</span></span>

<span data-ttu-id="afd3d-114">이 예제에서는 기존 저장소 계정의 새 컨테이너에 새 Blob을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="afd3d-114">This example creates a new blob to a new container in an existing storage account.</span></span>

```csharp
/* Include these "using" directives...
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Blob;
*/

string storageConnectionString = "DefaultEndpointsProtocol=https;"
    + "AccountName=[Storage Account Name]"
    + ";AccountKey=[Storage Account Key]"
    + ";EndpointSuffix=core.windows.net";

CloudStorageAccount account = CloudStorageAccount.Parse(storageConnectionString);
CloudBlobClient serviceClient = account.CreateCloudBlobClient();

// Create container. Name must be lower case.
Console.WriteLine("Creating container...");
var container = serviceClient.GetContainerReference("mycontainer");
container.CreateIfNotExistsAsync().Wait();

// write a blob to the container
CloudBlockBlob blob = container.GetBlockBlobReference("helloworld.txt");
blob.UploadTextAsync("Hello, World!").Wait();
```

> [!div class="nextstepactions"]
> [<span data-ttu-id="afd3d-115">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="afd3d-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/storage/client)

## <a name="management-apis"></a><span data-ttu-id="afd3d-116">관리 API</span><span class="sxs-lookup"><span data-stu-id="afd3d-116">Management APIs</span></span>

<span data-ttu-id="afd3d-117">관리 API를 사용하여 Azure Storage 계정 및 연결 키를 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="afd3d-117">Create and manage Azure Storage accounts and connection keys with the management API.</span></span>

<span data-ttu-id="afd3d-118">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="afd3d-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="afd3d-119">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="afd3d-119">Visual Studio package manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Storage.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="afd3d-120">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="afd3d-120">.NET Core CLI</span></span>

````bash
dotnet add package Microsoft.Azure.Management.Storage.Fluent
````

### <a name="code-example"></a><span data-ttu-id="afd3d-121">코드 예제</span><span class="sxs-lookup"><span data-stu-id="afd3d-121">Code Example</span></span>

<span data-ttu-id="afd3d-122">이 예제에서는 저장소 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="afd3d-122">This example creates a storage account.</span></span>

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Management.Storage.Fluent
*/

IStorageAccount storage = azure.StorageAccounts.Define(storageAccountName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .Create();
```

> [!div class="nextstepactions"]
> [<span data-ttu-id="afd3d-123">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="afd3d-123">Explore the management APIs</span></span>](/dotnet/api/overview/azure/storage/management)

## <a name="samples"></a><span data-ttu-id="afd3d-124">샘플</span><span class="sxs-lookup"><span data-stu-id="afd3d-124">Samples</span></span>

* [<span data-ttu-id="afd3d-125">.NET에서 Azure Blob Storage 시작(영문)</span><span class="sxs-lookup"><span data-stu-id="afd3d-125">Get started with Azure Blob Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/) 
* [<span data-ttu-id="afd3d-126">.NET에서 Azure Queue Storage 시작(영문)</span><span class="sxs-lookup"><span data-stu-id="afd3d-126">Get started with Azure Queue Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-queue-dotnet-getting-started/)

<span data-ttu-id="afd3d-127">Azure Storage 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="afd3d-127">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage) of Azure Storage samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package