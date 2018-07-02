---
title: .NET용 Azure Search 라이브러리
description: .NET용 Azure Search 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Search
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: search
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 5062d444b859711d7f87a0ecbd65e6b204c04b16
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065283"
---
# <a name="azure-search-libraries-for-net"></a><span data-ttu-id="b5d55-104">.NET용 Azure Search 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b5d55-104">Azure Search libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b5d55-105">개요</span><span class="sxs-lookup"><span data-stu-id="b5d55-105">Overview</span></span>

<span data-ttu-id="b5d55-106">[Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search)는 웹, 모바일 및 엔터프라이즈 응용 프로그램의 데이터에 대 한 풍부한 검색 환경을 제공하는 완전히 관리되는 클라우드 검색 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="b5d55-106">[Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search) is a fully managed cloud search service that provides a rich search experience over data in web, mobile, and enterprise applications.</span></span>

## <a name="client-library"></a><span data-ttu-id="b5d55-107">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b5d55-107">Client library</span></span>

<span data-ttu-id="b5d55-108">Azure Search 클라이언트 라이브러리를 사용하여 검색 서비스, 인덱스, 문서 또는 기타 개체에 대한 인덱싱 및 검색 작업에 액세스하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d55-108">Use the Azure Search client library to access and execute indexing and search operations on a search service, index, documents, or other object.</span></span> <span data-ttu-id="b5d55-109">단계별 소개는 [.NET 응용 프로그램에서 Azure Search를 사용하는 방법](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5d55-109">For a step-by-step introduction, see [How to use Azure Search from a .NET application](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk).</span></span>

<span data-ttu-id="b5d55-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Search)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d55-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Search) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b5d55-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="b5d55-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Search
```

```bash
dotnet add package Microsoft.Azure.Search
```

### <a name="code-example"></a><span data-ttu-id="b5d55-112">코드 예제</span><span class="sxs-lookup"><span data-stu-id="b5d55-112">Code Example</span></span>

```csharp
/* Include these 'using' directives:
   using Microsoft.Azure.Search;
   using Microsoft.Azure.Search.Models;
*/

// A service endpoint and an api-key are required on a connection.
// Set them in a config file (not shown) and then connect to the client.
IConfigurationBuilder builder = new ConfigurationBuilder().AddJsonFile("appsettings.json");
IConfigurationRoot configuration = builder.Build();

SearchServiceClient serviceClient = CreateSearchServiceClient(configuration);

// Create an index named hotels
ISearchIndexClient indexClient = serviceClient.Indexes.GetClient("hotels");

```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b5d55-113">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="b5d55-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/search/client)


## <a name="management-library"></a><span data-ttu-id="b5d55-114">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b5d55-114">Management library</span></span>

<span data-ttu-id="b5d55-115">Azure Search 관리 라이브러리를 사용하여 서비스를 프로비전하고 api-keys를 관리하며 리소스를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d55-115">Use the Azure Search management library to provision a service, manage api-keys, and adjust resources.</span></span> <span data-ttu-id="b5d55-116">서비스 관리는 구독자 및 테넌트 식별을 위해 Azure Resource Manager에 대한 종속성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d55-116">Service management has a dependency on Azure Resource Manager for subscriber and tenant identification.</span></span> <span data-ttu-id="b5d55-117">일반적으로 워크플로를 지원하기 위해서는 Azure Active Directory에 인증 및 응용 프로그램 등록도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d55-117">Typically, authentication and application registration with Azure Active Directory is also necessary to support the workflow.</span></span> <span data-ttu-id="b5d55-118">Azure Search 서비스 프로비전에 대한 소개는 [관리 REST API를 사용하는 방법](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5d55-118">For an introduction to Azure Search service provisioning, see [How to use the Management REST API](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api).</span></span>

<span data-ttu-id="b5d55-119">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Search)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d55-119">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Search) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b5d55-120">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="b5d55-120">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Search
```

```bash
dotnet add package Microsoft.Azure.Management.Search
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b5d55-121">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="b5d55-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/search/management)

## <a name="samples"></a><span data-ttu-id="b5d55-122">샘플</span><span class="sxs-lookup"><span data-stu-id="b5d55-122">Samples</span></span>

 + [<span data-ttu-id="b5d55-123">Azure 샘플 / search-dotnet-getting-started</span><span class="sxs-lookup"><span data-stu-id="b5d55-123">Azure Samples / search-dotnet-getting-started</span></span>](https://github.com/Azure-Samples/search-dotnet-getting-started)
 + [<span data-ttu-id="b5d55-124">Azure 샘플 / search-dotnet-management-api</span><span class="sxs-lookup"><span data-stu-id="b5d55-124">Azure Samples / search-dotnet-management-api</span></span>](https://github.com/Azure-Samples/search-dotnet-management-api)

<span data-ttu-id="b5d55-125">Github의 [Azure 샘플 리포지토리](https://github.com/Azure-Samples/)에서 더 많은 검색 샘플을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d55-125">Find more search samples in the [Azure samples repository](https://github.com/Azure-Samples/) on Github.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
