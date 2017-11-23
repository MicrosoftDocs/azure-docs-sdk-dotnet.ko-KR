---
title: ".NET용 Azure Database for PostgreSQL 라이브러리"
description: ".NET용 Azure Database for PostgreSQL 클라이언트 라이브러리에 대한 참조 설명서"
keywords: "Azure, .NET ODBC, SDK, API, SQL, ADO.NET, 데이터베이스, PostGres, PostgreSQL"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: postgresql
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 7a8c1965432d5cca36665bce3963c30cdaee9205
ms.sourcegitcommit: 4dba7cd869bddff3dee7315d258522dc4879abce
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2017
---
# <a name="azure-database-for-postgresql-libraries-for-net"></a>.NET용 Azure Database for PostgreSQL 라이브러리

## <a name="overview"></a>개요

[Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)에 저장된 데이터 및 리소스를 사용하여 작업합니다.

## <a name="client-api"></a>클라이언트 API

Azure Database for PostgreSQL에 액세스하기 위해 권장되는 클라이언트 라이브러리는 오픈 소스 [Npgsql ADO.NET 데이터 공급자](http://www.npgsql.org/)입니다. ADO.NET 공급자를 사용하여 데이터베이스에 연결하고 SQL 문을 직접 실행하거나, Npgsql의 [Entity Framework 6](http://www.npgsql.org/ef6/index.html) 또는 [Entity Framework Core](http://www.npgsql.org/efcore/index.html) 공급자가 있는 Entity Framework를 통해 실행합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Npgsql)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Npgsql
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Npgsql
```

### <a name="code-example"></a>코드 예제

```csharp
/* Include this 'using' directive...
using Npgsql;
*/

// Always store connection strings securely. 
string connectionString = "Server=[servername].postgres.database.azure.com; " +
    "Port=5432; Database=myDataBase; User Id=[userid]@[servername]; Password=password;";

// Best practice is to scope the NpgsqlConnection to a "using" block
using (NpgsqlConnection conn = new NpgsqlConnection(connectionString))
{
    // Connect to the database
    conn.Open();

    // Read rows
    NpgsqlCommand selectCommand = new NpgsqlCommand("SELECT * FROM MyTable", conn);
    NpgsqlDataReader results = selectCommand.ExecuteReader();
    
    // Enumerate over the rows
    while(results.Read())
    {
        Console.WriteLine("Column 0: {0} Column 1: {1}", results[0], results[1]);
    }
}
```

### <a name="samples"></a>샘플

- [ADO.NET 코드 예제](/dotnet/framework/data/adonet/ado-net-code-examples)
- [Azure CLI를 사용하여 PostgreSQL 데이터베이스 디자인](https://docs.microsoft.com/azure/postgresql/tutorial-design-database-using-azure-cli)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
