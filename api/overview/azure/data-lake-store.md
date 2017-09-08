---
title: ".NET용 Azure Data Lake Store 라이브러리"
description: ".NET용 Azure Data Lake Store 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Data Lake Store
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/18/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 18746d745d64065a3d92215e704bce575130bdb0
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-data-lake-store-libraries-for-net"></a><span data-ttu-id="cd370-104">.NET용 Azure Data Lake Store 라이브러리</span><span class="sxs-lookup"><span data-stu-id="cd370-104">Azure Data Lake Store libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="cd370-105">개요</span><span class="sxs-lookup"><span data-stu-id="cd370-105">Overview</span></span>

<span data-ttu-id="cd370-106">Azure 데이터 레이크 저장소는 빅 데이터 분석 작업을 위한 엔터프라이즈 수준 하이퍼 스케일 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="cd370-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="cd370-107">Azure 데이터 레이크를 사용하면 작동 및 예비 분석에 대해 한 곳에서 모든 크기, 형식 및 수집 속도의 데이터를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd370-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

<span data-ttu-id="cd370-108">자세히 알아보려면 [Azure Data Lake Store의 개요](/azure/data-lake-store/data-lake-store-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd370-108">To learn more, see [Overview of Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="cd370-109">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="cd370-109">Management library</span></span>

<span data-ttu-id="cd370-110">관리 라이브러리를 사용하여 빅 데이터 리포지토리에 연결하고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="cd370-110">Use the management library to connect to and manage your big data repositories.</span></span>

<span data-ttu-id="cd370-111">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cd370-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="cd370-112">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="cd370-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Store
```

### <a name="code-example"></a><span data-ttu-id="cd370-113">코드 예제</span><span class="sxs-lookup"><span data-stu-id="cd370-113">Code Example</span></span>

<span data-ttu-id="cd370-114">이 예제에서는 분석 계정 및 저장소를 인증하고 관리에 필요한 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd370-114">This example authenticates to an analytics account and store and creates the clients necessary for management.</span></span>

```csharp
/*
using AdlClient
using AdlClient.Models 
*/

// Setup authentication 
Authentication auth = new Authentication("microsoft.onmicrosoft.com"); // change this to YOUR tenant
auth.Authenticate();

// Identify the accounts
StoreAccountRef adls_account = new StoreAccountRef(subscriptionId, resourceGroup, userName);

// Create the clients
AzureClient az = new AzureClient(auth);
StoreClient adls = new StoreClient(auth, adls_account);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="cd370-115">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="cd370-115">Explore the management APIs</span></span>](/dotnet/api/overview/azure/datalakestore/management)

## <a name="samples"></a><span data-ttu-id="cd370-116">샘플</span><span class="sxs-lookup"><span data-stu-id="cd370-116">Samples</span></span>

* [<span data-ttu-id="cd370-117">Azure Data Lake .NET 클라이언트 예제</span><span class="sxs-lookup"><span data-stu-id="cd370-117">Azure Data Lake .NET Client Example</span></span>](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/)

<span data-ttu-id="cd370-118">앱에서 사용할 수 있는 [.NET 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd370-118">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
