---
title: .NET용 Azure Data Lake Store 라이브러리
description: .NET용 Azure Data Lake Store 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Data Lake Store
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: data-lake-store
ms.custom: devcenter, svc-overview
ms.openlocfilehash: f1b014c4835784ed8ecfa1e3b4bfd62a6ebf9562
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065633"
---
# <a name="azure-data-lake-store-libraries-for-net"></a><span data-ttu-id="b2369-104">.NET용 Azure Data Lake Store 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b2369-104">Azure Data Lake Store libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b2369-105">개요</span><span class="sxs-lookup"><span data-stu-id="b2369-105">Overview</span></span>

<span data-ttu-id="b2369-106">Azure 데이터 레이크 저장소는 빅 데이터 분석 작업을 위한 엔터프라이즈 수준 하이퍼 스케일 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="b2369-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="b2369-107">Azure 데이터 레이크를 사용하면 작동 및 예비 분석에 대해 한 곳에서 모든 크기, 형식 및 수집 속도의 데이터를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2369-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

<span data-ttu-id="b2369-108">자세히 알아보려면 [Azure Data Lake Store의 개요](/azure/data-lake-store/data-lake-store-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2369-108">To learn more, see [Overview of Azure Data Lake Store](/azure/data-lake-store/data-lake-store-overview).</span></span>

## <a name="client-library"></a><span data-ttu-id="b2369-109">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b2369-109">Client library</span></span>

<span data-ttu-id="b2369-110">클라이언트 라이브러리를 사용하여 Data Lake Store 계정에 폴더를 만들고, 파일을 업로드하며, 파일을 다운로드하는 등 Data Lake Store에서 파일 시스템 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b2369-110">Use the client library to perform filesystem operations on Data Lake Store, such as creating folders in a Data Lake Store account, uploading files, and downloading files.</span></span>  <span data-ttu-id="b2369-111">.NET에서 Data Lake Store를 사용하는 방법에 대한 자세한 자습서는 [.NET SDK를 사용한 Azure Data Lake Store에서의 파일 시스템 작업](/azure/data-lake-store/data-lake-store-data-operations-net-sdk)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2369-111">For a full tutorial on using Data Lake Store with .NET, see [Filesystem operations on Azure Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-data-operations-net-sdk).</span></span>

<span data-ttu-id="b2369-112">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b2369-112">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b2369-113">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="b2369-113">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.DataLake.Store
```
### <a name="authentication"></a><span data-ttu-id="b2369-114">인증</span><span class="sxs-lookup"><span data-stu-id="b2369-114">Authentication</span></span>

* <span data-ttu-id="b2369-115">응용 프로그램에 대한 최종 사용자 인증의 경우 [.NET SDK를 사용한 Data Lake Store의 최종 사용자 인증](/azure/data-lake-store/data-lake-store-end-user-authenticate-net-sdk)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2369-115">For end-user authentication for your application, see [End-user authentication with Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-end-user-authenticate-net-sdk).</span></span>
* <span data-ttu-id="b2369-116">응용 프로그램에 대한 서비스 간 인증의 경우 [.NET SDK를 사용한 Data Lake Store의 서비스 간 인증](/azure/data-lake-store/data-lake-store-service-to-service-authenticate-net-sdk)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2369-116">For service-to-service authentication for your application, see [Service-to-service authentication with Data Lake Store using .NET SDK](/azure/data-lake-store/data-lake-store-service-to-service-authenticate-net-sdk).</span></span>

### <a name="code-example"></a><span data-ttu-id="b2369-117">코드 예제</span><span class="sxs-lookup"><span data-stu-id="b2369-117">Code Example</span></span>

<span data-ttu-id="b2369-118">다음 코드 조각은 이는 서비스에 요청을 발급하는 데 사용되는 Data Lake Store 파일 시스템 클라이언트 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2369-118">The following snippet creates the Data Lake Store filesystem client object, which is used to issue requests to the service.</span></span>

```csharp
// Create client objects
AdlsClient client = AdlsClient.CreateClient(_adlsAccountName, adlCreds);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2369-119">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="b2369-119">Explore the client APIs</span></span>](/dotnet/api/overview/azure/datalakestore/client)


## <a name="management-library"></a><span data-ttu-id="b2369-120">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b2369-120">Management library</span></span>

<span data-ttu-id="b2369-121">관리 라이브러리를 사용하여 빅 데이터 리포지토리에 연결하고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="b2369-121">Use the management library to connect to and manage your big data repositories.</span></span>

<span data-ttu-id="b2369-122">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b2369-122">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b2369-123">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="b2369-123">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Store
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2369-124">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="b2369-124">Explore the client APIs</span></span>](/dotnet/api/overview/azure/datalakestore/management)


## <a name="samples"></a><span data-ttu-id="b2369-125">샘플</span><span class="sxs-lookup"><span data-stu-id="b2369-125">Samples</span></span>

* [<span data-ttu-id="b2369-126">Azure Data Lake .NET 클라이언트 예제</span><span class="sxs-lookup"><span data-stu-id="b2369-126">Azure Data Lake .NET Client Example</span></span>](https://azure.microsoft.com/en-us/resources/samples/data-lake-dotnet-client/)

<span data-ttu-id="b2369-127">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="b2369-127">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
