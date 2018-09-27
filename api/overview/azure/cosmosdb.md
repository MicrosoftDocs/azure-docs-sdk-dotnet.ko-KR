---
title: .NET용 Azure Cosmos DB 라이브러리
description: .NET용 Azure Cosmos DB 라이브러리에 대한 참조
ms.date: 08/31/2018
ms.topic: reference
ms.service: cosmos-db
ms.openlocfilehash: 21a2f2168259528a0d27103783e34aa532d7e17a
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190801"
---
# <a name="azure-cosmos-db-libraries-for-net"></a><span data-ttu-id="a6cfb-103">.NET용 Azure Cosmos DB 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a6cfb-103">Azure Cosmos DB libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="a6cfb-104">개요</span><span class="sxs-lookup"><span data-stu-id="a6cfb-104">Overview</span></span>

<span data-ttu-id="a6cfb-105">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)는 전 세계에 배포된 다중 모델 데이터베이스 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="a6cfb-105">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is a globally distributed, multi-model database service.</span></span> <span data-ttu-id="a6cfb-106">해당 서비스는 포괄적인 SLA를 제공하는 원하는 수의 지역에서 처리량 및 저장소 크기를 탄력적 및 독립적으로 조정할 수 있도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6cfb-106">It is designed to elastically and independently scale throughput and storage across any number of geographical regions with a comprehensive SLA.</span></span> <span data-ttu-id="a6cfb-107">Azure Cosmos DB를 사용하면 API 및 프로그래밍 모델을 사용하여 문서, 키-값, 넓은 열 및 그래프 데이터베이스를 저장하고 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6cfb-107">With Azure Cosmos DB, you can store and access document, key-value, wide-column, and graph databases by using APIs and programming models.</span></span> 

<span data-ttu-id="a6cfb-108">[Cosmos DB 시작](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span><span class="sxs-lookup"><span data-stu-id="a6cfb-108">[Get started with Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="a6cfb-109">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a6cfb-109">Client library</span></span>

<span data-ttu-id="a6cfb-110">Azure Cosmos DB .NET 클라이언트 라이브러리를 사용하여 기존 Azure Cosmos DB 데이터 저장소에 액세스하고 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a6cfb-110">Use the Azure Cosmos DB .NET client library to access and store data in an existing Azure Cosmos DB data store.</span></span> <span data-ttu-id="a6cfb-111">새 Azure Cosmos DB 계정 만들기를 자동화하려면 Azure Portal, CLI 또는 PowerShell을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a6cfb-111">To automate creation of a new Azure Cosmos DB account, use the Azure portal, CLI, or PowerShell.</span></span>

<span data-ttu-id="a6cfb-112">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a6cfb-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="a6cfb-113">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="a6cfb-113">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a><span data-ttu-id="a6cfb-114">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a6cfb-114">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a><span data-ttu-id="a6cfb-115">코드 예제</span><span class="sxs-lookup"><span data-stu-id="a6cfb-115">Code Example</span></span>

<span data-ttu-id="a6cfb-116">이 예제에서는 기존 Azure Cosmos DB SQL API 데이터베이스에 연결하고 컬렉션에서 문서를 읽고 `Item` 개체로 deserialize합니다.</span><span class="sxs-lookup"><span data-stu-id="a6cfb-116">This example connects to an existing Azure Cosmos DB SQL API database, reads a document from a collection, and deserializes it as an `Item` object.</span></span>   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6cfb-117">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="a6cfb-117">Explore the client APIs</span></span>](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a><span data-ttu-id="a6cfb-118">샘플</span><span class="sxs-lookup"><span data-stu-id="a6cfb-118">Samples</span></span>

* [<span data-ttu-id="a6cfb-119">Azure CosmosDB의 MongoDB API를 사용하여 .NET 앱 개발</span><span class="sxs-lookup"><span data-stu-id="a6cfb-119">Developing a .NET app using Azure Cosmos DB's MongoDB API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

<span data-ttu-id="a6cfb-120">Azure Cosmos DB 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a6cfb-120">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb) of Azure Cosmos DB samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
