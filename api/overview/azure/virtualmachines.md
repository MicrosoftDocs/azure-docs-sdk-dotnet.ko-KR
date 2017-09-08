---
title: ".NET용 Azure 계산 라이브러리"
description: ".NET용 Azure 계산 라이브러리에 대한 참조"
keywords: "Azure, .NET, SDK, API, VM, 가상 컴퓨터, 계산"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: b30c1433b8f25941fc1d4ea4718aa07c0a870580
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-virtual-machine-libraries-for-net"></a><span data-ttu-id="f388a-104">.NET용 Azure 가상 컴퓨터 라이브러리</span><span class="sxs-lookup"><span data-stu-id="f388a-104">Azure virtual machine libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="f388a-105">개요</span><span class="sxs-lookup"><span data-stu-id="f388a-105">Overview</span></span>

<span data-ttu-id="f388a-106">Linux 또는 Windows를 실행하는 요청 시 확장 가능한 컴퓨팅 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="f388a-106">On-demand, scalable computing resources running Linux or Windows.</span></span>

<span data-ttu-id="f388a-107">Azure 가상 컴퓨터를 시작하려면 [Azure Portal을 사용하여 Linux 가상 컴퓨터 만들기](https://review.docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f388a-107">To get started with Azure virtual machines, see [Create a Linux virtual machine with the Azure portal](https://review.docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal).</span></span>

## <a name="management-apis"></a><span data-ttu-id="f388a-108">관리 API</span><span class="sxs-lookup"><span data-stu-id="f388a-108">Management APIs</span></span>

<span data-ttu-id="f388a-109">관리 API를 사용하여 코드에서 Azure의 Windows 및 Linux 가상 컴퓨터를 생성, 구성 및 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f388a-109">Create, configure, and scale out Windows and Linux virtual machines in Azure from your code with the management API.</span></span>

<span data-ttu-id="f388a-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Compute.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f388a-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Compute.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f388a-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="f388a-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Compute.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="f388a-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="f388a-112">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.Compute.Fluent
```

### <a name="code-example"></a><span data-ttu-id="f388a-113">코드 예제</span><span class="sxs-lookup"><span data-stu-id="f388a-113">Code Example</span></span>

<span data-ttu-id="f388a-114">Windows VM을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f388a-114">Create a Windows VM.</span></span>

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.Compute.Fluent;
using Microsoft.Azure.Management.Compute.Fluent.Models;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

IVirtualMachine windowsVM = azure.VirtualMachines.Define("MyVirtualMachine")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup("MyResourceGroup")
    .WithNewPrimaryNetwork("10.0.0.0/28")
    .WithPrimaryPrivateIPAddressDynamic()
    .WithNewPrimaryPublicIPAddress("MyIPAddressLabel")
    .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
    .WithAdminUsername("UserName")
    .WithAdminPassword("Password")
    .WithSize(VirtualMachineSizeTypes.StandardD3V2)
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f388a-115">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="f388a-115">Explore the management APIs</span></span>](https://review.docs.microsoft.com/en-us/dotnet/api/overview/azure/virtualmachines/management?view=azure-dotnet)

### <a name="samples"></a><span data-ttu-id="f388a-116">샘플</span><span class="sxs-lookup"><span data-stu-id="f388a-116">Samples</span></span>

* [<span data-ttu-id="f388a-117">가상 컴퓨터 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="f388a-117">Create and manage virtual machines</span></span>](/dotnet/azure/dotnet-sdk-azure-virtual-machine-samples)
* [<span data-ttu-id="f388a-118">.NET에서 템플릿을 사용하여 SSH 사용 VM 배포(영문)</span><span class="sxs-lookup"><span data-stu-id="f388a-118">Deploy an SSH-enabled VM with a Template with .NET</span></span>](https://azure.microsoft.com/en-us/resources/samples/resource-manager-dotnet-template-deployment/)

<span data-ttu-id="f388a-119">가상 컴퓨터 샘플의 [전체 목록](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=VM)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="f388a-119">View the [complete list](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=VM) of virtual machine samples.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
