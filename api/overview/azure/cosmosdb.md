---
title: ".NET용 Azure CosmosDB 라이브러리"
description: ".NET용 Azure CosmosDB 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, CosmosDB
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: cosmos-db
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 890c00caeca06bf863425c7159d7833c4db8df38
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
---
# <a name="azure-cosmosdb-libraries-for-net"></a><span data-ttu-id="409a2-104">.NET용 Azure CosmosDB 라이브러리</span><span class="sxs-lookup"><span data-stu-id="409a2-104">Azure CosmosDB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="409a2-105">개요</span><span class="sxs-lookup"><span data-stu-id="409a2-105">Overview</span></span>

<span data-ttu-id="409a2-106">[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction)는 여러 유형의 데이터베이스를 지원하는 확장성 있는 분산 데이터 저장소입니다.</span><span class="sxs-lookup"><span data-stu-id="409a2-106">[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a distributed and scalable data store, supporting multiple different types of databases.</span></span>

## <a name="client-library"></a><span data-ttu-id="409a2-107">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="409a2-107">Client library</span></span>

<span data-ttu-id="409a2-108">CosmosDB .NET 클라이언트 라이브러리를 사용하여 CosmosDB 데이터 저장소에 액세스하고 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="409a2-108">Use the CosmosDB .NET client library to access and store data in a CosmosDB data store.</span></span>

<span data-ttu-id="409a2-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="409a2-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="409a2-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="409a2-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="409a2-111">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="409a2-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="409a2-112">코드 예제</span><span class="sxs-lookup"><span data-stu-id="409a2-112">Code Example</span></span>

<span data-ttu-id="409a2-113">이 예제에서는 기존 CosmosDB DocumentDB API 데이터베이스에 연결하고 컬렉션에서 문서를 읽고 `Item` 개체로 deserialize합니다.</span><span class="sxs-lookup"><span data-stu-id="409a2-113">This example connects to an existing CosmosDB DocumentDB API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
// "Item" is a class defined elsewhere...
Item item = client.ReadDocumentAsync<Item>(documentUri).ToString()).Result;
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="409a2-114">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="409a2-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="409a2-115">샘플</span><span class="sxs-lookup"><span data-stu-id="409a2-115">Samples</span></span>

* [<span data-ttu-id="409a2-116">Azure CosmosDB의 MongoDB API를 사용하여 .NET 앱 개발</span><span class="sxs-lookup"><span data-stu-id="409a2-116">Developing a .NET app using Azure Cosmos DB's MongoDB API</span></span>](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

<span data-ttu-id="409a2-117">Azure Cosmos DB 샘플의 [전체 목록](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="409a2-117">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
