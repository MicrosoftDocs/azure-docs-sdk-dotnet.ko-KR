---
title: .NET용 Azure Cosmos DB 라이브러리
description: .NET용 Azure Cosmos DB 라이브러리에 대한 참조
ms.date: 08/31/2018
ms.topic: reference
ms.service: cosmos-db
ms.openlocfilehash: 8ff565f1cd72eec2f574b45d04ceac526b8c5eb0
ms.sourcegitcommit: 01ec3adba39a6f946015552c28da0a9a6bb57180
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112021"
---
# <a name="azure-cosmos-db-libraries-for-net"></a><span data-ttu-id="1acad-103">.NET용 Azure Cosmos DB 라이브러리</span><span class="sxs-lookup"><span data-stu-id="1acad-103">Azure Cosmos DB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="1acad-104">개요</span><span class="sxs-lookup"><span data-stu-id="1acad-104">Overview</span></span>

<span data-ttu-id="1acad-105">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)는 전 세계에 배포된 다중 모델 데이터베이스 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-105">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a globally distributed, multi-model database service.</span></span> <span data-ttu-id="1acad-106">해당 서비스는 포괄적인 SLA를 제공하는 원하는 수의 지역에서 처리량 및 저장소 크기를 탄력적 및 독립적으로 조정할 수 있도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-106">It is designed to elastically and independently scale throughput and storage across any number of geographical regions with a comprehensive SLA.</span></span> <span data-ttu-id="1acad-107">Azure Cosmos DB를 사용하면 API 및 프로그래밍 모델을 사용하여 문서, 키-값, 넓은 열 및 그래프 데이터베이스를 저장하고 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-107">With Azure Cosmos DB, you can store and access document, key-value, wide-column, and graph databases by using APIs and programming models.</span></span> 

<span data-ttu-id="1acad-108">[Cosmos DB 시작](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span><span class="sxs-lookup"><span data-stu-id="1acad-108">[Get started with Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="1acad-109">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="1acad-109">Client library</span></span>

<span data-ttu-id="1acad-110">Azure Cosmos DB .NET 클라이언트 라이브러리를 사용하여 기존 Azure Cosmos DB 데이터 저장소에 액세스하고 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-110">Use the Azure Cosmos DB .NET client library to access and store data in an existing Azure Cosmos DB data store.</span></span> <span data-ttu-id="1acad-111">새 Azure Cosmos DB 계정 만들기를 자동화하려면 Azure Portal, CLI 또는 PowerShell을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-111">To automate creation of a new Azure Cosmos DB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="1acad-112">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

<span data-ttu-id="1acad-113">2.x 버전을 설치하려면:</span><span class="sxs-lookup"><span data-stu-id="1acad-113">To install version 2.x:</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="1acad-114">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="1acad-114">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="1acad-115">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="1acad-115">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

<span data-ttu-id="1acad-116">.NET 표준을 대상으로 버전 3.0의 미리 보기를 설치하려면:</span><span class="sxs-lookup"><span data-stu-id="1acad-116">To install the preview of version 3.0, which targets .NET standard:</span></span> 

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="1acad-117">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="1acad-117">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Cosmos -prerelease
```

#### <a name="net-core-cli"></a><span data-ttu-id="1acad-118">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="1acad-118">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Cosmos
```


### <a name="code-example"></a><span data-ttu-id="1acad-119">코드 예제</span><span class="sxs-lookup"><span data-stu-id="1acad-119">Code Example</span></span>

<span data-ttu-id="1acad-120">이 예제에서는 기존 Azure Cosmos DB SQL API 데이터베이스에 연결하고 컬렉션에서 문서를 읽고 `Item` 개체로 deserialize합니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-120">This example connects to an existing Azure Cosmos DB SQL API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span> <span data-ttu-id="1acad-121">이 예제에서는 .NET SDK의 2.x 버전을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-121">This example uses version 2.x of the .NET SDK.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString();
```

<span data-ttu-id="1acad-122">이 예제는 기존 Azure Cosmos DB SQL API 데이터베이스에 연결하고, 새 데이터베이스와 컨테이너를 만들고, 컨테이너에서 항목을 읽고, `TodoItem` 객체로 deserialize합니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-122">This example connects to an existing Azure Cosmos DB SQL API database, creates a new database and container, reads an item from the container, and deserializes it to a `TodoItem` object.</span></span> <span data-ttu-id="1acad-123">이 예제에서는 .NET SDK의 3.x 버전을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-123">This example uses version 3.x of the .NET SDK.</span></span>   

```csharp
using (CosmosClient cosmosClient = new CosmosClient("endpoint", "primaryKey"))
{
    // Read item from container
    CosmosItemResponse<TodoItem> todoItemResponse = await cosmosClient.Databases["DatabaseId"].Containers["ContainerId"].Items.ReadItemAsync<TodoItem>("partitionKeyValue", "ItemId");
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="1acad-124">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="1acad-124">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="1acad-125">샘플</span><span class="sxs-lookup"><span data-stu-id="1acad-125">Samples</span></span>

* [<span data-ttu-id="1acad-126">Azure Cosmos DB의 SQL API (버전 2.x)를 사용하여 .NET 앱 개발</span><span class="sxs-lookup"><span data-stu-id="1acad-126">Developing a .NET app using Azure Cosmos DB's SQL API (Version 2.x)</span></span>](https://github.com/Azure-Samples/documentdb-dotnet-todo-app/)
* [<span data-ttu-id="1acad-127">Azure Cosmos DB의 SQL API (버전 3.x 미리보기)를 사용하여 .NET 앱 개발</span><span class="sxs-lookup"><span data-stu-id="1acad-127">Developing a .NET app using Azure Cosmos DB's SQL API (Version 3.x Preview)</span></span>](https://github.com/Azure-Samples/cosmos-dotnet-todo-app/)
* [<span data-ttu-id="1acad-128">Azure Cosmos DB의 SQL API (버전 3.x 미리보기)를 사용하여 .NET Core 앱 개발</span><span class="sxs-lookup"><span data-stu-id="1acad-128">Developing a .NET Core app using Azure Cosmos DB's SQL API (Version 3.x Preview)</span></span>](https://github.com/Azure-Samples/cosmos-dotnet-core-getting-started)

<span data-ttu-id="1acad-129">Azure Cosmos DB 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="1acad-129">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
