---
title: .NET용 Power BI Embedded 라이브러리
description: .NET용 Power BI Embedded 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Power BI Embedded
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 3e28525f61ca8b4f8347b7a7e8994f9e479749ea
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065963"
---
# <a name="power-bi-embedded-libraries-for-net"></a>.NET용 Power BI Embedded 라이브러리

[Power BI](https://powerbi.microsoft.com/)는 가장 중요한 비즈니스 데이터의 단일 뷰를 제공하는 클라우드 기반의 비즈니스 분석 서비스입니다.

.NET과 함께 Power BI를 사용하는 방법에 대해 자세한 알아보려면 [Power BI에 포함](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-embedding/)을 참조하세요.

## <a name="client-library"></a>클라이언트 라이브러리

Power BI API와 연결하는 데 클라이언트 라이브러리를 사용하여 데이터 집합 및 보고서에 액세스하고 상호 작용합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager]에서 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.PowerBI.Api)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.PowerBI.Api
```

### <a name="example"></a>예

다음 예제에서는 데이터 집합 및 보고서의 목록을 검색하고 표시합니다.

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
> [클라이언트 API 탐색](https://powerbi.microsoft.com/documentation/powerbi-developer-rest-api-reference/)

## <a name="samples"></a>샘플

* [Power BI 개발자 샘플](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [Power BI .NET GitHub 리포지토리](https://github.com/Microsoft/PowerBI-CSharp)

앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
