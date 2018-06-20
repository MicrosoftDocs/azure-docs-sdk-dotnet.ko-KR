---
title: .NET용 Azure Search 라이브러리
description: .NET용 Azure Search 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Search
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: search
ms.custom: devcenter, svc-overview
ms.openlocfilehash: bd0899d6dbc6d474389eebac78a77a62b86c5255
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
ms.locfileid: "23566304"
---
# <a name="azure-search-libraries-for-net"></a>.NET용 Azure Search 라이브러리

## <a name="overview"></a>개요

[Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search)는 웹, 모바일 및 엔터프라이즈 응용 프로그램의 데이터에 대 한 풍부한 검색 환경을 제공하는 완전히 관리되는 클라우드 검색 서비스입니다.

## <a name="client-library"></a>클라이언트 라이브러리

Azure Search 클라이언트 라이브러리를 사용하여 검색 서비스, 인덱스, 문서 또는 기타 개체에 대한 인덱싱 및 검색 작업에 액세스하고 실행합니다. 단계별 소개는 [.NET 응용 프로그램에서 Azure Search를 사용하는 방법](https://docs.microsoft.com/azure/search/search-howto-dotnet-sdk)을 참조하세요.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Search)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Search
```

```bash
dotnet add package Microsoft.Azure.Search
```

### <a name="code-example"></a>코드 예제

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
> [클라이언트 API 탐색](/dotnet/api/overview/azure/search/client)


## <a name="management-library"></a>관리 라이브러리

Azure Search 관리 라이브러리를 사용하여 서비스를 프로비전하고 api-keys를 관리하며 리소스를 조정합니다. 서비스 관리는 구독자 및 테넌트 식별을 위해 Azure Resource Manager에 대한 종속성을 갖습니다. 일반적으로 워크플로를 지원하기 위해서는 Azure Active Directory에 인증 및 응용 프로그램 등록도 필요합니다. Azure Search 서비스 프로비전에 대한 소개는 [관리 REST API를 사용하는 방법](https://docs.microsoft.com/rest/api/searchmanagement/search-howto-management-rest-api)을 참조하세요.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Search)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Search
```

```bash
dotnet add package Microsoft.Azure.Management.Search
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/search/management)

## <a name="samples"></a>샘플

 + [Azure 샘플 / search-dotnet-getting-started](https://github.com/Azure-Samples/search-dotnet-getting-started)
 + [Azure 샘플 / search-dotnet-management-api](https://github.com/Azure-Samples/search-dotnet-management-api)

Github의 [Azure 샘플 리포지토리](https://github.com/Azure-Samples/)에서 더 많은 검색 샘플을 찾습니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
