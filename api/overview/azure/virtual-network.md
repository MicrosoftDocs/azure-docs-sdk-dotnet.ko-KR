---
title: .NET용 Azure Virtual Network 라이브러리
description: .NET용 Azure Virtual Network 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: virtual-network
ms.openlocfilehash: 54dd79cf0f5bed1eab7b606b8a6e3b30c797ecd0
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190666"
---
# <a name="azure-virtual-network-libraries-for-net"></a><span data-ttu-id="859c5-103">.NET용 Azure Virtual Network 라이브러리</span><span class="sxs-lookup"><span data-stu-id="859c5-103">Azure Virtual Network libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="859c5-104">개요</span><span class="sxs-lookup"><span data-stu-id="859c5-104">Overview</span></span>
<span data-ttu-id="859c5-105">[Azure Virtual Network](/azure/virtual-network/virtual-networks-overview) 서비스를 사용하면 Azure 리소스와 가상 네트워크(VNet)를 서로 안전하게 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859c5-105">The [Azure Virtual Network](/azure/virtual-network/virtual-networks-overview) service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="859c5-106">VNet은 클라우드에 있는 사용자의 네트워크를 나타내며,</span><span class="sxs-lookup"><span data-stu-id="859c5-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="859c5-107">VNet을 서로 연결하여 VNet에 연결된 리소스가 서로 통신하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859c5-107">You can also connect VNets to each other, enabling resources connected to either VNet to communicate with each other.</span></span> 

## <a name="management-library"></a><span data-ttu-id="859c5-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="859c5-108">Management library</span></span>

<span data-ttu-id="859c5-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="859c5-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="859c5-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="859c5-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Network.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="859c5-111">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="859c5-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Network.Fluent
```

### <a name="code-example"></a><span data-ttu-id="859c5-112">코드 예제</span><span class="sxs-lookup"><span data-stu-id="859c5-112">Code Example</span></span>
<span data-ttu-id="859c5-113">이 예제에서는 가상 네트워크를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="859c5-113">This example shows how you can create a virtual network.</span></span>

```csharp
/* 
  Include these "using" directives...
  
  using Microsoft.Azure.Management.Network.Fluent;
  using Microsoft.Azure.Management.Network.Fluent.Models;
*/
using (NetworkManagementClient client = new NetworkManagementClient(credentials))
{
    // Define VNet
    VirtualNetworkInner vnet = new VirtualNetworkInner()
    {
        Location = "West US",
        AddressSpace = new AddressSpace()
        {
            AddressPrefixes = new List<string>() { "0.0.0.0/16" }
        },

        DhcpOptions = new DhcpOptions()
        {
            DnsServers = new List<string>() { "1.1.1.1", "1.1.2.4" }
        },

        Subnets = new List<Subnet>()
        {
            new Subnet()
            {
                Name = subnet1Name,
                AddressPrefix = "1.0.1.0/24",
            },
            new Subnet()
            {
                Name = subnet2Name,
               AddressPrefix = "1.0.2.0/24",
            }
        }
    };
    
    await client.VirtualNetworks.CreateOrUpdateAsync(resourceGroupName, vNetName, vnet);
}

```

> [!div class="nextstepaction"]
> [<span data-ttu-id="859c5-114">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="859c5-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/network/management)

## <a name="samples"></a><span data-ttu-id="859c5-115">샘플</span><span class="sxs-lookup"><span data-stu-id="859c5-115">Samples</span></span>
- [<span data-ttu-id="859c5-116">서브넷으로 Virtual Network 관리</span><span class="sxs-lookup"><span data-stu-id="859c5-116">Managing Virtual Networks with subnets</span></span>](https://github.com/Azure-Samples/network-dotnet-manage-virtual-network)

<span data-ttu-id="859c5-117">앱에서 사용할 수 있는 [.NET 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="859c5-117">Explore more [.NET sample code](https://azure.microsoft.com/resources/samples/?platform=dotnet) that you can use in your apps.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console 
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package 

