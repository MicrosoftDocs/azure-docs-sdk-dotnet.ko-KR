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
# <a name="azure-billing-libraries-for-net"></a><span data-ttu-id="b1be1-103">.NET용 Azure 청구 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b1be1-103">Azure Billing libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="b1be1-104">개요</span><span class="sxs-lookup"><span data-stu-id="b1be1-104">Overview</span></span>

<span data-ttu-id="b1be1-105">Azure 청구 API(미리 보기)는 Azure 청구 정보 및 송장에 대한 프로그래밍 방식의 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b1be1-105">Azure Billing API (preview) provides programmatic access to your Azure billing information and invoices.</span></span>

## <a name="management-library"></a><span data-ttu-id="b1be1-106">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="b1be1-106">Management library</span></span>

<span data-ttu-id="b1be1-107">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b1be1-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Billing) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="b1be1-108">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="b1be1-108">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Billing
```

```bash
dotnet add package Microsoft.Azure.Management.Billing
```

### <a name="code-example"></a><span data-ttu-id="b1be1-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="b1be1-109">Code Example</span></span>

<span data-ttu-id="b1be1-110">Azure에 연결하고 송장 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b1be1-110">Connect to Azure and get a list of invoices.</span></span>

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
> [<span data-ttu-id="b1be1-111">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="b1be1-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/billing/management)

## <a name="samples"></a><span data-ttu-id="b1be1-112">샘플</span><span class="sxs-lookup"><span data-stu-id="b1be1-112">Samples</span></span>

* [<span data-ttu-id="b1be1-113">사용량 API</span><span class="sxs-lookup"><span data-stu-id="b1be1-113">Usage API</span></span>](https://github.com/Azure-Samples/billing-dotnet-usage-api)
* [<span data-ttu-id="b1be1-114">RateCard API</span><span class="sxs-lookup"><span data-stu-id="b1be1-114">RateCard API</span></span>](https://github.com/Azure-Samples/billing-dotnet-ratecard-api)
* [<span data-ttu-id="b1be1-115">다중 테넌트 웹 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="b1be1-115">Multi-Tenant Web Application</span></span>](https://github.com/Azure-Samples/billing-dotnet-webapp-multitenant)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
