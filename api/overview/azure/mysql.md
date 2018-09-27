---
title: .NET용 Azure Database for MySQL 라이브러리
description: .NET용 Azure Database for MySQL 클라이언트 라이브러리에 대한 참조 설명서
ms.date: 10/19/2017
ms.topic: reference
ms.service: mysql
ms.openlocfilehash: 34550c7089a2ec05164f7a16f24bfc8b18391f8a
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190156"
---
# <a name="azure-database-for-mysql-libraries-for-net"></a>.NET용 Azure Database for MySQL 라이브러리

## <a name="overview"></a>개요

[Azure Database for MySQL](/azure/mysql/overview)에 저장된 데이터 및 리소스를 사용하여 작업합니다.

## <a name="client-apis"></a>클라이언트 API

Azure Database for MySQL에 액세스하기 위한 권장되는 클라이언트 라이브러리는 MySQL의 [커넥터/Net](https://dev.mysql.com/doc/connector-net/en)입니다. 패키지를 사용하여 데이터베이스에 연결하고 직접 SQL 문을 실행합니다. 

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/MySql.Data)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package MySql.Data
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package MySql.Data
```

### <a name="code-example"></a>코드 예제

MySQL 데이터베이스에 연결하고 쿼리를 실행합니다.

```csharp
/* Include this "using" directive...
using MySql.Data.MySqlClient;
*/

string connectionString = "Server=[servername].mysql.database.azure.com; " +
    "Database=myDataBase; Uid=[userid]@[servername]; Pwd=myPassword;";

// Best practice is to scope the MySqlConnection to a "using" block
using (MySqlConnection conn = new MySqlConnection(connectionString))
{
    // Connect to the database
    conn.Open();

    // Read rows
    MySqlCommand selectCommand = new MySqlCommand("SELECT * FROM MyTable", conn);
    MySqlDataReader results = selectCommand.ExecuteReader();
    
    // Enumerate over the rows
    while(results.Read())
    {
        Console.WriteLine("Column 0: {0} Column 1: {1}", results[0], results[1]);
    }
}
```

## <a name="samples"></a>샘플

- [ADO.NET 코드 예제](/dotnet/framework/data/adonet/ado-net-code-examples)
- [Azure CLI를 사용하여 MySQL 데이터베이스 디자인](https://docs.microsoft.com/azure/mysql/tutorial-design-database-using-cli) 

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
