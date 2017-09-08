---
title: ".NET용 Azure CosmosDB 라이브러리"
description: ".NET용 Azure CosmosDB 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, CosmosDB
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/17/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: babf34e98dae439a2dc3d4c63bd638335428e935
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-cosmosdb-libraries-for-net"></a>.NET용 Azure CosmosDB 라이브러리

## <a name="overview"></a>개요

[Azure CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction)는 여러 유형의 데이터베이스를 지원하는 확장성 있는 분산 데이터 저장소입니다.

## <a name="client-library"></a>클라이언트 라이브러리

CosmosDB .NET 클라이언트 라이브러리를 사용하여 CosmosDB 데이터 저장소에 액세스하고 데이터를 저장합니다.

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

이 예제에서는 기존 CosmosDB DocumentDB API 데이터베이스에 연결하고 컬렉션에서 문서를 읽고 `Item` 개체로 deserialize합니다.

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
> [클라이언트 API 탐색](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a>샘플

* [Azure CosmosDB의 MongoDB API를 사용하여 .NET 앱 개발](https://azure.microsoft.com/en-us/resources/samples/azure-cosmos-db-mongodb-dotnet-getting-started/)

Azure Cosmos DB 샘플의 [전체 목록](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=cosmosdb)을 봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
