---
title: .NET용 Azure SQL Database API
description: .NET용 Azure SQL Database 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: sql-database
ms.openlocfilehash: e4c1620ddf488952c6720b9bedf2521c6512b9a3
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190636"
---
# <a name="azure-sql-database-apis-for-net"></a>.NET용 Azure SQL Database API

## <a name="overview"></a>개요

[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)는 관계형, JSON, 공간 및 XML 데이터를 지원하는 Microsoft SQL Server 엔진을 사용하는 데이터베이스 서비스입니다. 

.NET에서 SQL Database를 사용하는 방법에 대한 자세한 내용은 [Visual Studio에서 .NET을 사용하여 Azure SQL Database 연결 및 쿼리](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-visual-studio)를 참조하세요.

## <a name="client-library"></a>클라이언트 라이브러리

.NET SQL 클라이언트 라이브러리를 사용하여 데이터베이스에 연결하여 인증하고 임시 T-SQL 문과 저장 프로 시저를 실행합니다.

Visual Studio [패키지 관리자 콘솔](https://docs.microsoft.com/nuget/tools/package-manager-console) 또는 [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package)를 사용하여 [NuGet 패키지]( https://www.nuget.org/packages/System.Data.SqlClient)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package System.Data.SqlClient
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package System.Data.SqlClient
```

### <a name="code-example"></a>코드 예제

이 예제에서는 데이터베이스에 연결하고 테이블에서 행을 읽습니다.

```csharp
/* Include this 'using' directive...
using System.Data.SqlClient;
*/

// Always store connection strings securely. 
string connectionString = "Server=tcp:[serverName].database.windows.net;" 
    + "Database=myDataBase;User ID=[loginname]@[serverName];Password=myPassword;"
    + "Trusted_Connection=False;Encrypt=True;";

// Best practice is to scope the SqlConnection to a "using" block
using (SqlConnection conn = new SqlConnection(connectionString))
{
    // Connect to the database
    conn.Open();

    // Read rows
    SqlCommand selectCommand = new SqlCommand("SELECT * FROM MyTable", conn);
    SqlDataReader results = selectCommand.ExecuteReader();
    
    // Enumerate over the rows
    while(results.Read())
    {
        Console.WriteLine("Column 0: {0} Column 1: {1}", results[0], results[1]);
    }
}
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/sql/client)

## <a name="management-library"></a>관리 라이브러리

Azure SQL Database 관리 라이브러리를 사용하여 Azure SQL Database 서버 인스턴스를 생성, 관리 및 크기 조정합니다.

Visual Studio [패키지 관리자 콘솔](https://docs.microsoft.com/nuget/tools/package-manager-console) 또는 [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package)를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Sql.Fluent/)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Sql.Fluent
``` 

#### <a name="net-core-command-line"></a>.NET Core 명령줄

```bash
dotnet add package Microsoft.Azure.Management.Sql.Fluent
```

### <a name="code-example"></a>코드 예제

이 예제에서는 새 SQL Database 서버 인스턴스를 만든 다음 해당 인스턴스에 새 데이터베이스를 만듭니다.

```csharp
/* Include these 'using' directives...
using Microsoft.Azure.Management.Sql.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

string startAddress = "0.0.0.0";
string endAddress = "255.255.255.255";

// Create the SQL server instance
ISqlServer sqlServer = azure.SqlServers.Define("UniqueServerName")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup("ResourceGroupName")
    .WithAdministratorLogin("UserName")
    .WithAdministratorPassword("Password")
    .WithNewFirewallRule(startAddress, endAddress)
    .Create();

// Create the database
ISqlDatabase sqlDb = sqlServer.Databases.Define("DatabaseName").Create();
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/sql/management)

## <a name="samples"></a>샘플

- [ADO.NET 코드 예제](/dotnet/framework/data/adonet/ado-net-code-examples)
- [.NET SQL Database 샘플용 Azure 관리 라이브러리](/dotnet/azure/dotnet-sdk-azure-sql-database-samples)

Azure SQL Database 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=sql+database)을 봅니다.

