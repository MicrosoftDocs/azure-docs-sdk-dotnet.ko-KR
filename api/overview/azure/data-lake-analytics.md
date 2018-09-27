---
title: .NET용 Azure Data Lake Analytics 라이브러리
description: .NET용 Azure Data Lake Analytics 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: data-lake-analytics
ms.openlocfilehash: 829f9245ae06c64c4ad9a175fd25c742533a284e
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47189796"
---
# <a name="azure-data-lake-analytics-libraries-for-net"></a><span data-ttu-id="a45c8-103">.NET용 Azure Data Lake Analytics 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a45c8-103">Azure Data Lake Analytics libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="a45c8-104">개요</span><span class="sxs-lookup"><span data-stu-id="a45c8-104">Overview</span></span>

<span data-ttu-id="a45c8-105">Azure Data Lake Analytics는 빅 데이터 분석을 간소화하는 주문형 분석 작업 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="a45c8-105">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span>

<span data-ttu-id="a45c8-106">자세한 내용은 [Microsoft Azure Data Lake Analytics 개요](/azure/data-lake-analytics/data-lake-analytics-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a45c8-106">To learn more, see [Overview of Microsoft Azure Data Lake Analytics](/azure/data-lake-analytics/data-lake-analytics-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="a45c8-107">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a45c8-107">Management library</span></span>

<span data-ttu-id="a45c8-108">관리 라이브러리를 사용하여 서비스에 연결하고 분석 작업을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="a45c8-108">Use the management library to connect to the service and manage analytics jobs.</span></span>

<span data-ttu-id="a45c8-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a45c8-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="a45c8-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="a45c8-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Analytics
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Analytics
```

### <a name="code-example"></a><span data-ttu-id="a45c8-111">코드 예제</span><span class="sxs-lookup"><span data-stu-id="a45c8-111">Code Example</span></span>

<span data-ttu-id="a45c8-112">이 예제에서는 분석 계정을 연결 및 관리할 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a45c8-112">This example creates the clients to connect with and manage the analytics account.</span></span>

```csharp
/*
using AdlClient 
*/

// Setup authentication for this demo
Authentication auth = new Authentication("microsoft.onmicrosoft.com"); // change this to YOUR tenant
auth.Authenticate();

// Identify the accounts
AnalyticsAccountRef adla_account = new AnalyticsAccountRef(subscriptionId, resourceGroup, userName);

// Create the clients
AzureClient az = new AzureClient(auth);
AnalyticsClient adla = new AnalyticsClient(auth, adla_account);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="a45c8-113">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="a45c8-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datalakeanalytics/management)

## <a name="samples"></a><span data-ttu-id="a45c8-114">샘플</span><span class="sxs-lookup"><span data-stu-id="a45c8-114">Samples</span></span>
* [<span data-ttu-id="a45c8-115">Azure Data Lake .NET 클라이언트 예제</span><span class="sxs-lookup"><span data-stu-id="a45c8-115">Azure Data Lake .NET Client Example</span></span>](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/)

<span data-ttu-id="a45c8-116">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a45c8-116">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
