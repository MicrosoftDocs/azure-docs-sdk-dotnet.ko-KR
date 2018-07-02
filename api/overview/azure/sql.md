---
title: .NET용 Azure SQL Database API
description: .NET용 Azure SQL Database 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, SQL, SQL 데이터베이스
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: sql-database
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 30d5f9ffa0654673fe358872cbb7342fb87d4127
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065893"
---
# <a name="azure-sql-database-apis-for-net"></a><span data-ttu-id="9625e-104">.NET용 Azure SQL Database API</span><span class="sxs-lookup"><span data-stu-id="9625e-104">Azure SQL Database APIs for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="9625e-105">개요</span><span class="sxs-lookup"><span data-stu-id="9625e-105">Overview</span></span>

<span data-ttu-id="9625e-106">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)는 관계형, JSON, 공간 및 XML 데이터를 지원하는 Microsoft SQL Server 엔진을 사용하는 데이터베이스 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="9625e-106">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) is a database service using the Microsoft SQL Server engine that supports relational, JSON, spatial, and XML data.</span></span> 

<span data-ttu-id="9625e-107">.NET에서 SQL Database를 사용하는 방법에 대한 자세한 내용은 [Visual Studio에서 .NET을 사용하여 Azure SQL Database 연결 및 쿼리](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-visual-studio)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9625e-107">To learn more about the using SQL Database with .NET, see [Use .NET with Visual Studio to connect and query an Azure SQL database](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).</span></span>

## <a name="client-library"></a><span data-ttu-id="9625e-108">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9625e-108">Client library</span></span>

<span data-ttu-id="9625e-109">.NET SQL 클라이언트 라이브러리를 사용하여 데이터베이스에 연결하여 인증하고 임시 T-SQL 문과 저장 프로 시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9625e-109">Use the .NET SQL client library to connect and authenticate with your database and execute ad-hoc T-SQL statements and stored procedures.</span></span>

<span data-ttu-id="9625e-110">Visual Studio [패키지 관리자 콘솔](https://docs.microsoft.com/nuget/tools/package-manager-console) 또는 [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package)를 사용하여 [NuGet 패키지]( https://www.nuget.org/packages/System.Data.SqlClient)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="9625e-110">Install the [NuGet package]( https://www.nuget.org/packages/System.Data.SqlClient) directly from the Visual Studio [Package Manager console](https://docs.microsoft.com/nuget/tools/package-manager-console) or with the [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9625e-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="9625e-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package System.Data.SqlClient
```

#### <a name="net-core-cli"></a><span data-ttu-id="9625e-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="9625e-112">.NET Core CLI</span></span>

```bash
dotnet add package System.Data.SqlClient
```

### <a name="code-example"></a><span data-ttu-id="9625e-113">코드 예제</span><span class="sxs-lookup"><span data-stu-id="9625e-113">Code Example</span></span>

<span data-ttu-id="9625e-114">이 예제에서는 데이터베이스에 연결하고 테이블에서 행을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="9625e-114">This example connects to a database and reads rows from a table.</span></span>

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
> [<span data-ttu-id="9625e-115">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="9625e-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/sql/client)

## <a name="management-library"></a><span data-ttu-id="9625e-116">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9625e-116">Management library</span></span>

<span data-ttu-id="9625e-117">Azure SQL Database 관리 라이브러리를 사용하여 Azure SQL Database 서버 인스턴스를 생성, 관리 및 크기 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="9625e-117">Use the Azure SQL Database management library to create, manage, and scale Azure SQL Database server instances.</span></span>

<span data-ttu-id="9625e-118">Visual Studio [패키지 관리자 콘솔](https://docs.microsoft.com/nuget/tools/package-manager-console) 또는 [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package)를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Sql.Fluent/)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="9625e-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Sql.Fluent/) directly from the Visual Studio [Package Manager console](https://docs.microsoft.com/nuget/tools/package-manager-console) or with the [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package).</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9625e-119">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="9625e-119">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Sql.Fluent
``` 

#### <a name="net-core-command-line"></a><span data-ttu-id="9625e-120">.NET Core 명령줄</span><span class="sxs-lookup"><span data-stu-id="9625e-120">.NET Core command line</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Sql.Fluent
```

### <a name="code-example"></a><span data-ttu-id="9625e-121">코드 예제</span><span class="sxs-lookup"><span data-stu-id="9625e-121">Code Example</span></span>

<span data-ttu-id="9625e-122">이 예제에서는 새 SQL Database 서버 인스턴스를 만든 다음 해당 인스턴스에 새 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9625e-122">This example creates a new SQL Database server instance and then creates a new database on that instance.</span></span>

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
> [<span data-ttu-id="9625e-123">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="9625e-123">Explore the management APIs</span></span>](/dotnet/api/overview/azure/sql/management)

## <a name="samples"></a><span data-ttu-id="9625e-124">샘플</span><span class="sxs-lookup"><span data-stu-id="9625e-124">Samples</span></span>

- [<span data-ttu-id="9625e-125">ADO.NET 코드 예제</span><span class="sxs-lookup"><span data-stu-id="9625e-125">ADO.NET code examples</span></span>](/dotnet/framework/data/adonet/ado-net-code-examples)
- [<span data-ttu-id="9625e-126">.NET SQL Database 샘플용 Azure 관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9625e-126">Azure management libraries for .NET samples for SQL Database</span></span>](/dotnet/azure/dotnet-sdk-azure-sql-database-samples)

<span data-ttu-id="9625e-127">Azure SQL Database 샘플의 [전체 목록](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=sql+database)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9625e-127">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=sql+database) of Azure SQL Database samples.</span></span>

