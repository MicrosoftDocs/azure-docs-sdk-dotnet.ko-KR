---
title: .NET용 Power BI Embedded 라이브러리
description: .NET용 Power BI Embedded 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: multiple
ms.openlocfilehash: acb327b56e89522142e51016a6a9b279f995a674
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190376"
---
# <a name="power-bi-embedded-libraries-for-net"></a><span data-ttu-id="d29a4-103">.NET용 Power BI Embedded 라이브러리</span><span class="sxs-lookup"><span data-stu-id="d29a4-103">Power BI Embedded libraries for .NET</span></span>

<span data-ttu-id="d29a4-104">[Power BI](https://powerbi.microsoft.com/)는 가장 중요한 비즈니스 데이터의 단일 뷰를 제공하는 클라우드 기반의 비즈니스 분석 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="d29a4-104">[Power BI](https://powerbi.microsoft.com/) is a cloud-based business analytics service that gives you a single view of your most critical business data.</span></span>

<span data-ttu-id="d29a4-105">.NET과 함께 Power BI를 사용하는 방법에 대해 자세한 알아보려면 [Power BI에 포함](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d29a4-105">To learn more about using Power BI with .NET, see [Embedding with Power BI](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/).</span></span>

## <a name="client-library"></a><span data-ttu-id="d29a4-106">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="d29a4-106">Client library</span></span>

<span data-ttu-id="d29a4-107">Power BI API와 연결하는 데 클라이언트 라이브러리를 사용하여 데이터 집합 및 보고서에 액세스하고 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="d29a4-107">Use the client library to connect with Power BI APIs to access and interact with data sets and reports.</span></span>

<span data-ttu-id="d29a4-108">Visual Studio [패키지 관리자 콘솔][PackageManager]에서 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.PowerBI.Api)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d29a4-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.PowerBI.Api) directly from the Visual Studio [Package Manager console][PackageManager].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="d29a4-109">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="d29a4-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.PowerBI.Api
```

### <a name="example"></a><span data-ttu-id="d29a4-110">예</span><span class="sxs-lookup"><span data-stu-id="d29a4-110">Example</span></span>

<span data-ttu-id="d29a4-111">다음 예제에서는 데이터 세트 및 보고서의 목록을 검색하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d29a4-111">The following example retrieves and displays a list of datasets and reports.</span></span>

```csharp
/* Include these'using' directive:
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;
*/
using (PowerBIClient client = new PowerBIClient(new Uri(apiUrl), tokenCredentials))
{

    Console.WriteLine("\r*** DATASETS ***\r");

    // List of datasets in a group/app workspace
    ODataResponseListDataset datasetList = client.Datasets.GetDatasetsInGroup(groupId);

    foreach(Dataset ds in datasetList.Value)
    {
        Console.WriteLine(ds.Id + " | " + ds.Name);
    }

    Console.WriteLine("\r*** REPORTS ***\r");

    // List of reports in a group/app workspace
    ODataResponseListReport reportList = client.Reports.GetReportsInGroup(groupId);

    foreach (Report rpt in reportList.Value)
    {
        Console.WriteLine(rpt.Id + " | " + rpt.Name +  " | DatasetID = " + rpt.DatasetId);
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="d29a4-112">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="d29a4-112">Explore the client APIs</span></span>](https://powerbi.microsoft.com/documentation/powerbi-developer-rest-api-reference/)

## <a name="samples"></a><span data-ttu-id="d29a4-113">샘플</span><span class="sxs-lookup"><span data-stu-id="d29a4-113">Samples</span></span>

* [<span data-ttu-id="d29a4-114">Power BI 개발자 샘플</span><span class="sxs-lookup"><span data-stu-id="d29a4-114">Power BI Developer Samples</span></span>](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [<span data-ttu-id="d29a4-115">Power BI .NET GitHub 리포지토리</span><span class="sxs-lookup"><span data-stu-id="d29a4-115">Power BI .NET GitHub repo</span></span>](https://github.com/Microsoft/PowerBI-CSharp)

<span data-ttu-id="d29a4-116">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="d29a4-116">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
