---
title: .NET용 Azure 청구 라이브러리
description: .NET용 Azure 청구 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: billing
ms.openlocfilehash: 196b9b4ed5f1f5f6794d86a43d26827355800d7b
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348085"
---
# <a name="azure-billing-libraries-for-net"></a>.NET용 Azure 청구 라이브러리

## <a name="overview"></a>개요

Azure 청구 API(미리 보기)는 Azure 청구 정보 및 송장에 대한 프로그래밍 방식의 액세스를 제공합니다.

## <a name="management-library"></a>관리 라이브러리

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Billing
```

```bash
dotnet add package Microsoft.Azure.Management.Billing
```

### <a name="code-example"></a>코드 예제

Azure에 연결하고 송장 목록을 가져옵니다.

```csharp
/* Include these directives
using Microsoft.Rest.Azure.Authentication;
using Microsoft.Azure.Management.Billing;
using Microsoft.Azure.Management.Billing.Models;
*/

// Log into Azure
var serviceCreds = ApplicationTokenProvider.LoginSilentAsync(tenantId, clientId, secret);
var billingClient = new BillingClient(serviceCreds);
billingClient.SubscriptionId = subscriptionId;

// Get list of invoices
billingClient.Invoices.List();
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/billing/management)

## <a name="samples"></a>샘플

* [사용량 API](https://github.com/Azure-Samples/billing-dotnet-usage-api)
* [RateCard API](https://github.com/Azure-Samples/billing-dotnet-ratecard-api)
* [다중 테넌트 웹 응용 프로그램](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
