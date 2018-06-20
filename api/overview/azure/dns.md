---
title: .NET용 Azure DNS 라이브러리
description: .NET용 Azure DNS 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, DNS
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: dns
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 34b50defa5f1524ab70c212b091f26016d59e81b
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2017
ms.locfileid: "23487056"
---
# <a name="azure-dns-libraries-for-net"></a><span data-ttu-id="cdd30-104">.NET용 Azure DNS 라이브러리</span><span class="sxs-lookup"><span data-stu-id="cdd30-104">Azure DNS libraries for .NET</span></span>

<span data-ttu-id="cdd30-105">.NET용 Microsoft Azure DNS 라이브러리를 사용하여 Azure 내에서 호스팅되는 DNS 영역 및 레코드를 만들고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="cdd30-105">Use the Microsoft Azure DNS libraries for .NET to create and modify DNS zones and records hosted within Azure.</span></span> <span data-ttu-id="cdd30-106">영역 및 레코드는 Azure 리소스로 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdd30-106">Zones and records are managed as Azure Resources.</span></span> <span data-ttu-id="cdd30-107">자세한 내용은 [Azure DNS 개요](/azure/dns/dns-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cdd30-107">Learn more by reading the [Azure DNS overview](/azure/dns/dns-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="cdd30-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="cdd30-108">Management library</span></span>

<span data-ttu-id="cdd30-109">관리 라이브러리를 사용하여 Azure에서 호스팅되는 DNS 영역과 레코드를 만들고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="cdd30-109">Use the management library to create and modify DNS zones and records that are hosted in Azure.</span></span>

<span data-ttu-id="cdd30-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cdd30-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="cdd30-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="cdd30-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Dns
```

```bash
dotnet add package Microsoft.Azure.Management.Dns
```

### <a name="example"></a><span data-ttu-id="cdd30-112">예제</span><span class="sxs-lookup"><span data-stu-id="cdd30-112">Example</span></span>

<span data-ttu-id="cdd30-113">다음 예제에서는 새 DNS 영역을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cdd30-113">The following example creates a new DNS zone.</span></span>

```csharp
/*
using Microsoft.Rest.Azure.Authentication;
using Microsoft.Azure.Management.Dns;
using Microsoft.Azure.Management.Dns.Models;
*/
Microsoft.Rest.ServiceClientCredentials serviceCreds = await ApplicationTokenProvider.LoginSilentAsync(tenantId, clientId, secret);
DnsManagementClient dnsClient = new DnsManagementClient(serviceCreds);            
Zone dnsZoneParams = new Zone("global");
dnsZoneParams.Tags = new Dictionary<string, string>();
dnsZoneParams.Tags.Add("dept", "finance");
Zone dnsZone =
    await dnsClient.Zones.CreateOrUpdateAsync(resourceGroupName, zoneName, dnsZoneParams, null, "*");
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="cdd30-114">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="cdd30-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/dns/management)

## <a name="samples"></a><span data-ttu-id="cdd30-115">샘플</span><span class="sxs-lookup"><span data-stu-id="cdd30-115">Samples</span></span>

* [<span data-ttu-id="cdd30-116">Azure DNS .NET SDK 샘플 프로젝트</span><span class="sxs-lookup"><span data-stu-id="cdd30-116">Azure DNS .NET SDK Sample Project</span></span>](https://www.microsoft.com/download/details.aspx?id=47268)

<span data-ttu-id="cdd30-117">앱에서 사용할 수 있는 [.NET 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="cdd30-117">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
