---
title: ".NET용 Azure CosmosDB 라이브러리"
description: ".NET용 Azure CosmosDB 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, CosmosDB
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 11/17/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: cosmos-db
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 9f29e53e7f202e48ade12e28f08487bbacd2833c
ms.sourcegitcommit: 9cc5f8da9e9a15ba07fd67fe8b9a2d4ee6b57c73
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2017
---
# <a name="azure-cosmosdb-libraries-for-net"></a><span data-ttu-id="a4a10-104">.NET용 Azure CosmosDB 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a4a10-104">Azure CosmosDB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="a4a10-105">개요</span><span class="sxs-lookup"><span data-stu-id="a4a10-105">Overview</span></span>

<span data-ttu-id="a4a10-106">[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction)는 여러 유형의 데이터베이스를 지원하는 확장성 있는 분산 데이터 저장소입니다.</span><span class="sxs-lookup"><span data-stu-id="a4a10-106">[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a distributed and scalable data store, supporting multiple different types of databases.</span></span>

<span data-ttu-id="a4a10-107">[CosmosDB 시작](https://docs.microsoft.com/azure/cosmos-db/create-documentdb-dotnet).</span><span class="sxs-lookup"><span data-stu-id="a4a10-107">[Get started with CosmosDB](https://docs.microsoft.com/azure/cosmos-db/create-documentdb-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="a4a10-108">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a4a10-108">Client library</span></span>

<span data-ttu-id="a4a10-109">CosmosDB .NET 클라이언트 라이브러리를 사용하여 기존 CosmosDB 데이터 저장소에 액세스하고 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a4a10-109">Use the CosmosDB .NET client library to access and store data in an existing CosmosDB data store.</span></span>  <span data-ttu-id="a4a10-110">새 CosmosDB 계정 만들기를 자동화하려면 Azure Portal, CLI 또는 PowerShell을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a4a10-110">To automate creation of a new CosmosDB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="a4a10-111">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a4a10-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="a4a10-112">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="a4a10-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="a4a10-113">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a4a10-113">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="a4a10-114">코드 예제</span><span class="sxs-lookup"><span data-stu-id="a4a10-114">Code Example</span></span>

<span data-ttu-id="a4a10-115">이 예제에서는 기존 CosmosDB DocumentDB API 데이터베이스에 연결하고 컬렉션에서 문서를 읽고 `Item` 개체로 deserialize합니다.</span><span class="sxs-lookup"><span data-stu-id="a4a10-115">This example connects to an existing CosmosDB DocumentDB API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString()).Result;
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4a10-116">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="a4a10-116">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="a4a10-117">샘플</span><span class="sxs-lookup"><span data-stu-id="a4a10-117">Samples</span></span>

* [<span data-ttu-id="a4a10-118">Azure CosmosDB의 MongoDB API를 사용하여 .NET 앱 개발</span><span class="sxs-lookup"><span data-stu-id="a4a10-118">Developing a .NET app using Azure Cosmos DB's MongoDB API</span></span>](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

<span data-ttu-id="a4a10-119">Azure Cosmos DB 샘플의 [전체 목록](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a4a10-119">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
