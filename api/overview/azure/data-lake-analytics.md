---
title: .NET용 Azure Data Lake Analytics 라이브러리
description: .NET용 Azure Data Lake Analytics 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Data Lake Analytics
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: data-lake-analytics
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 063513d8c523330276cdfc222d3ca00a9629f63a
ms.sourcegitcommit: dbec35008347b581dd238b882354300e427bec70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2018
ms.locfileid: "29728414"
---
# <a name="azure-data-lake-analytics-libraries-for-net"></a>.NET용 Azure Data Lake Analytics 라이브러리

## <a name="overview"></a>개요

Azure Data Lake Analytics는 빅 데이터 분석을 간소화하는 주문형 분석 작업 서비스입니다.

자세한 내용은 [Microsoft Azure Data Lake Analytics 개요](/azure/data-lake-analytics/data-lake-analytics-overview)를 참조하세요.

## <a name="management-library"></a>관리 라이브러리

관리 라이브러리를 사용하여 서비스에 연결하고 분석 작업을 관리합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Analytics)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Analytics
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Analytics
```

### <a name="code-example"></a>코드 예제

이 예제에서는 분석 계정을 연결 및 관리할 클라이언트를 만듭니다.

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
> [관리 API 탐색](/dotnet/api/overview/azure/datalakeanalytics/management)

## <a name="samples"></a>샘플
* [Azure Data Lake .NET 클라이언트 예제](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/)

앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
