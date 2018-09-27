---
title: .NET용 Azure Database for PostgreSQL 라이브러리
description: .NET용 Azure Database for PostgreSQL 클라이언트 라이브러리에 대한 참조 설명서
ms.date: 10/19/2017
ms.topic: reference
ms.service: postgresql
ms.openlocfilehash: 4137e024eadba93c9cb3e94c1e7478d0816f8370
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190749"
---
# <a name="azure-database-for-postgresql-libraries-for-net"></a><span data-ttu-id="687b0-103">.NET용 Azure Database for PostgreSQL 라이브러리</span><span class="sxs-lookup"><span data-stu-id="687b0-103">Azure Database for PostgreSQL libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="687b0-104">개요</span><span class="sxs-lookup"><span data-stu-id="687b0-104">Overview</span></span>

<span data-ttu-id="687b0-105">[Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)에 저장된 데이터 및 리소스를 사용하여 작업합니다.</span><span class="sxs-lookup"><span data-stu-id="687b0-105">Work with data and resources stored in [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/).</span></span>

## <a name="client-api"></a><span data-ttu-id="687b0-106">클라이언트 API</span><span class="sxs-lookup"><span data-stu-id="687b0-106">Client API</span></span>

<span data-ttu-id="687b0-107">Azure Database for PostgreSQL에 액세스하기 위해 권장되는 클라이언트 라이브러리는 오픈 소스 [Npgsql ADO.NET 데이터 공급자](http://www.npgsql.org/)입니다.</span><span class="sxs-lookup"><span data-stu-id="687b0-107">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Npgsql ADO.NET data provider](http://www.npgsql.org/).</span></span> <span data-ttu-id="687b0-108">ADO.NET 공급자를 사용하여 데이터베이스에 연결하고 SQL 문을 직접 실행하거나, Npgsql의 [Entity Framework 6](http://www.npgsql.org/ef6/index.html) 또는 [Entity Framework Core](http://www.npgsql.org/efcore/index.html) 공급자가 있는 Entity Framework를 통해 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="687b0-108">Use the ADO.NET provider to connect to the database and execute SQL statements directly or through Entity Framework with the Npgsql's [Entity Framework 6](http://www.npgsql.org/ef6/index.html) or [Entity Framework Core](http://www.npgsql.org/efcore/index.html) providers.</span></span>

<span data-ttu-id="687b0-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Npgsql)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="687b0-109">Install the [NuGet package](https://www.nuget.org/packages/Npgsql) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="687b0-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="687b0-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Npgsql
```

#### <a name="net-core-cli"></a><span data-ttu-id="687b0-111">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="687b0-111">.NET Core CLI</span></span>

```bash
dotnet add package Npgsql
```

### <a name="code-example"></a><span data-ttu-id="687b0-112">코드 예제</span><span class="sxs-lookup"><span data-stu-id="687b0-112">Code Example</span></span>

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

### <a name="samples"></a><span data-ttu-id="687b0-113">샘플</span><span class="sxs-lookup"><span data-stu-id="687b0-113">Samples</span></span>

- [<span data-ttu-id="687b0-114">ADO.NET 코드 예제</span><span class="sxs-lookup"><span data-stu-id="687b0-114">ADO.NET code examples</span></span>](/dotnet/framework/data/adonet/ado-net-code-examples)
- [<span data-ttu-id="687b0-115">Azure CLI를 사용하여 PostgreSQL 데이터베이스 디자인</span><span class="sxs-lookup"><span data-stu-id="687b0-115">Design a PostgreSQL database using the Azure CLI</span></span>](https://docs.microsoft.com/azure/postgresql/tutorial-design-database-using-azure-cli)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
