---
title: .NET용 Azure Resource Manager 라이브러리
description: .NET용 Azure Resource Manager 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: multiple
ms.openlocfilehash: 6d3a27c5f7ba94f5579723cc4f798826c8bdefd6
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190846"
---
# <a name="azure-resource-manager-libraries-for-net"></a><span data-ttu-id="2c214-103">.NET용 Azure Resource Manager 라이브러리</span><span class="sxs-lookup"><span data-stu-id="2c214-103">Azure Resource Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="2c214-104">개요</span><span class="sxs-lookup"><span data-stu-id="2c214-104">Overview</span></span>

<span data-ttu-id="2c214-105">Azure 리소스 관리자를 사용하면 솔루션에서 리소스를 그룹으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c214-105">Azure Resource Manager enables you to work with the resources in your solution as a group.</span></span>  <span data-ttu-id="2c214-106">리소스 관리자에 대한 자세한 내용은 [Azure Resource Manager 개요](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c214-106">For more information about Resource Manager, see [Azure Resource Manager overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="2c214-107">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="2c214-107">Management library</span></span>

<span data-ttu-id="2c214-108">.NET용 Azure Resource Manager 라이브러리를 통해 리소스 및 리소스 그룹을 만들고, 업데이트, 삭제 및 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c214-108">The Azure Resource Manager library for .NET enables you to create, update, delete, and list resources and resource groups.</span></span>

<span data-ttu-id="2c214-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2c214-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="2c214-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="2c214-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="example"></a><span data-ttu-id="2c214-111">예</span><span class="sxs-lookup"><span data-stu-id="2c214-111">Example</span></span>

<span data-ttu-id="2c214-112">이 예제는 새 리소스 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c214-112">This example creates a new resource group.</span></span>

```csharp
/* Include these "using" directives.
using Microsoft.Azure.Management.ResourceManager.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

IResourceGroup resourceGroup = azure.ResourceGroups
    .Define("ResourceGroupName")
    .WithRegion(Region.USWest)
    .Create();
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="2c214-113">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="2c214-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/resources/management)


## <a name="samples"></a><span data-ttu-id="2c214-114">샘플</span><span class="sxs-lookup"><span data-stu-id="2c214-114">Samples</span></span>

* [<span data-ttu-id="2c214-115">리소스 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="2c214-115">Manage resource groups</span></span>](https://github.com/Azure-Samples/resources-dotnet-manage-resource-group)
* [<span data-ttu-id="2c214-116">리소스 관리</span><span class="sxs-lookup"><span data-stu-id="2c214-116">Manage resources</span></span>](https://github.com/Azure-Samples/resources-dotnet-manage-resource)
* [<span data-ttu-id="2c214-117">ARM 템플릿을 사용하여 리소스 배포</span><span class="sxs-lookup"><span data-stu-id="2c214-117">Deploy resources with ARM templates</span></span>](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template)
* [<span data-ttu-id="2c214-118">ARM 템플릿을 사용하여 리소스 배포(진행 상황과 함께)</span><span class="sxs-lookup"><span data-stu-id="2c214-118">Deploy resources with ARM templates (with progress)</span></span>](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template-with-progress)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
