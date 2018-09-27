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
# <a name="azure-dns-libraries-for-net"></a>.NET용 Azure DNS 라이브러리

.NET용 Microsoft Azure DNS 라이브러리를 사용하여 Azure 내에서 호스팅되는 DNS 영역 및 레코드를 만들고 수정합니다. 영역 및 레코드는 Azure 리소스로 관리됩니다. 자세한 내용은 [Azure DNS 개요](/azure/dns/dns-overview)를 참조하세요.

## <a name="management-library"></a>관리 라이브러리

관리 라이브러리를 사용하여 Azure에서 호스팅되는 DNS 영역과 레코드를 만들고 수정합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Dns)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Dns
```

```bash
dotnet add package Microsoft.Azure.Management.Dns
```

### <a name="example"></a>예

다음 예제에서는 새 DNS 영역을 만듭니다.

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
> [관리 API 탐색](/dotnet/api/overview/azure/dns/management)

## <a name="samples"></a>샘플

* [Azure DNS .NET SDK 샘플 프로젝트](https://www.microsoft.com/download/details.aspx?id=47268)

앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
