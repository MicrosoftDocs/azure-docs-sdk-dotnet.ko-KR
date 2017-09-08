---
title: ".NET용 Azure Database for MySQL 라이브러리"
description: ".NET용 Azure Database for MySQL 클라이언트 라이브러리에 대한 참조 설명서"
keywords: "Azure, .NET, SDK, API, SQL, 데이터베이스, MySQL"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/17/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: mysql
ms.openlocfilehash: 1bc373d63b0172fd554277a6ef30fa09772a395b
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-database-for-mysql-libraries-for-net"></a><span data-ttu-id="6a6ed-104">.NET용 Azure Database for MySQL 라이브러리</span><span class="sxs-lookup"><span data-stu-id="6a6ed-104">Azure Database for MySQL libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="6a6ed-105">개요</span><span class="sxs-lookup"><span data-stu-id="6a6ed-105">Overview</span></span>

<span data-ttu-id="6a6ed-106">[Azure Database for MySQL](/azure/mysql/overview)에 저장된 데이터 및 리소스를 사용하여 작업합니다.</span><span class="sxs-lookup"><span data-stu-id="6a6ed-106">Work with data and resources stored in [Azure Database for MySQL](/azure/mysql/overview).</span></span>

## <a name="client-apis"></a><span data-ttu-id="6a6ed-107">클라이언트 API</span><span class="sxs-lookup"><span data-stu-id="6a6ed-107">Client APIs</span></span>

<span data-ttu-id="6a6ed-108">Azure Database for MySQL에 액세스하기 위한 권장되는 클라이언트 라이브러리는 MySQL의 [커넥터/Net](https://dev.mysql.com/doc/connector-net/en)입니다.</span><span class="sxs-lookup"><span data-stu-id="6a6ed-108">The recommended client library for accessing Azure Database for MySQL is MySQL's [Connector/Net](https://dev.mysql.com/doc/connector-net/en).</span></span> <span data-ttu-id="6a6ed-109">패키지를 사용하여 데이터베이스에 연결하고 직접 SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6a6ed-109">Use the package to connect to the database and execute SQL statements directly.</span></span> 

<span data-ttu-id="6a6ed-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/MySql.Data)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="6a6ed-110">Install the [NuGet package](https://www.nuget.org/packages/MySql.Data) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="6a6ed-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="6a6ed-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package MySql.Data
```

#### <a name="net-core-cli"></a><span data-ttu-id="6a6ed-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="6a6ed-112">.NET Core CLI</span></span>

```bash
dotnet add package MySql.Data
```

### <a name="code-example"></a><span data-ttu-id="6a6ed-113">코드 예제</span><span class="sxs-lookup"><span data-stu-id="6a6ed-113">Code Example</span></span>

<span data-ttu-id="6a6ed-114">MySQL 데이터베이스에 연결하고 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6a6ed-114">Connect to a MySQL database and execute a query:</span></span>

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

## <a name="samples"></a><span data-ttu-id="6a6ed-115">샘플</span><span class="sxs-lookup"><span data-stu-id="6a6ed-115">Samples</span></span>

- [<span data-ttu-id="6a6ed-116">ADO.NET 코드 예제</span><span class="sxs-lookup"><span data-stu-id="6a6ed-116">ADO.NET code examples</span></span>](/dotnet/framework/data/adonet/ado-net-code-examples)
- [<span data-ttu-id="6a6ed-117">Azure CLI를 사용하여 MySQL 데이터베이스 디자인</span><span class="sxs-lookup"><span data-stu-id="6a6ed-117">Design a MySQL database using the Azure CLI</span></span>](https://docs.microsoft.com/azure/mysql/tutorial-design-database-using-cli) 

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
