---
title: .NET용 Azure DNS 라이브러리
description: .NET용 Azure DNS 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: dns
ms.openlocfilehash: b9ab6359aaa1e4e9b6e99e7a7b007928d18f3453
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190196"
---
# <a name="azure-dns-libraries-for-net"></a><span data-ttu-id="7e92a-103">.NET용 Azure DNS 라이브러리</span><span class="sxs-lookup"><span data-stu-id="7e92a-103">Azure DNS libraries for .NET</span></span>

<span data-ttu-id="7e92a-104">.NET용 Microsoft Azure DNS 라이브러리를 사용하여 Azure 내에서 호스팅되는 DNS 영역 및 레코드를 만들고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e92a-104">Use the Microsoft Azure DNS libraries for .NET to create and modify DNS zones and records hosted within Azure.</span></span> <span data-ttu-id="7e92a-105">영역 및 레코드는 Azure 리소스로 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e92a-105">Zones and records are managed as Azure Resources.</span></span> <span data-ttu-id="7e92a-106">자세한 내용은 [Azure DNS 개요](/azure/dns/dns-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e92a-106">Learn more by reading the [Azure DNS overview](/azure/dns/dns-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="7e92a-107">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="7e92a-107">Management library</span></span>

<span data-ttu-id="7e92a-108">관리 라이브러리를 사용하여 Azure에서 호스팅되는 DNS 영역과 레코드를 만들고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e92a-108">Use the management library to create and modify DNS zones and records that are hosted in Azure.</span></span>

<span data-ttu-id="7e92a-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7e92a-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="7e92a-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="7e92a-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Dns
```

```bash
dotnet add package Microsoft.Azure.Management.Dns
```

### <a name="example"></a><span data-ttu-id="7e92a-111">예</span><span class="sxs-lookup"><span data-stu-id="7e92a-111">Example</span></span>

<span data-ttu-id="7e92a-112">다음 예제에서는 새 DNS 영역을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7e92a-112">The following example creates a new DNS zone.</span></span>

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
> [<span data-ttu-id="7e92a-113">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="7e92a-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/dns/management)

## <a name="samples"></a><span data-ttu-id="7e92a-114">샘플</span><span class="sxs-lookup"><span data-stu-id="7e92a-114">Samples</span></span>

* [<span data-ttu-id="7e92a-115">Azure DNS .NET SDK 샘플 프로젝트</span><span class="sxs-lookup"><span data-stu-id="7e92a-115">Azure DNS .NET SDK Sample Project</span></span>](https://www.microsoft.com/download/details.aspx?id=47268)

<span data-ttu-id="7e92a-116">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7e92a-116">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
