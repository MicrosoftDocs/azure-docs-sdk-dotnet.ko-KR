---
title: .NET용 Azure Cosmos DB 라이브러리
description: .NET용 Azure Cosmos DB 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Cosmos DB
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 11/17/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: cosmos-db
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 4407e59cbcc7ceedc0c7964981d29d6e14a4aa95
ms.sourcegitcommit: 903457bd531e77797a86e6aedcfc94c1fb79fe6d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37132054"
---
# <a name="azure-cosmos-db-libraries-for-net"></a>.NET용 Azure Cosmos DB 라이브러리

## <a name="overview"></a>개요

[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)는 여러 유형의 데이터베이스를 지원하는 확장성 있는 분산 데이터 저장소입니다.

[Cosmos DB 시작](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).

## <a name="client-library"></a>클라이언트 라이브러리

Azure Cosmos DB .NET 클라이언트 라이브러리를 사용하여 기존 Azure Cosmos DB 데이터 저장소에 액세스하고 데이터를 저장합니다.  새 Azure Cosmos DB 계정 만들기를 자동화하려면 Azure Portal, CLI 또는 PowerShell을 사용합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

### <a name="code-example"></a>코드 예제

이 예제에서는 기존 Azure Cosmos DB SQL API 데이터베이스에 연결하고 컬렉션에서 문서를 읽고 `Item` 개체로 deserialize합니다.   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString().Result;
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a>샘플

* [Azure CosmosDB의 MongoDB API를 사용하여 .NET 앱 개발](https://azure.microsoft.com/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

Azure Cosmos DB 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb)을 봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
