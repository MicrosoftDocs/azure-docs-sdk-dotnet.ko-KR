---
title: .NET용 Azure Resource Manager 라이브러리
description: .NET용 Azure Resource Manager 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, 리소스 관리자
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: f9fe96fcdc94d3d27445f462c5220def9f2966da
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
ms.locfileid: "23566374"
---
# <a name="azure-resource-manager-libraries-for-net"></a><span data-ttu-id="d6e3c-104">.NET용 Azure Resource Manager 라이브러리</span><span class="sxs-lookup"><span data-stu-id="d6e3c-104">Azure Resource Manager libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="d6e3c-105">개요</span><span class="sxs-lookup"><span data-stu-id="d6e3c-105">Overview</span></span>

<span data-ttu-id="d6e3c-106">Azure 리소스 관리자를 사용하면 솔루션에서 리소스를 그룹으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6e3c-106">Azure Resource Manager enables you to work with the resources in your solution as a group.</span></span>  <span data-ttu-id="d6e3c-107">리소스 관리자에 대한 자세한 내용은 [Azure Resource Manager 개요](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6e3c-107">For more information about Resource Manager, see [Azure Resource Manager overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="d6e3c-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="d6e3c-108">Management library</span></span>

<span data-ttu-id="d6e3c-109">.NET용 Azure Resource Manager 라이브러리를 통해 리소스 및 리소스 그룹을 만들고, 업데이트, 삭제 및 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6e3c-109">The Azure Resource Manager library for .NET enables you to create, update, delete, and list resources and resource groups.</span></span>

<span data-ttu-id="d6e3c-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d6e3c-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="d6e3c-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="d6e3c-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="example"></a><span data-ttu-id="d6e3c-112">예제</span><span class="sxs-lookup"><span data-stu-id="d6e3c-112">Example</span></span>

<span data-ttu-id="d6e3c-113">이 예제는 새 리소스 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d6e3c-113">This example creates a new resource group.</span></span>

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
> [<span data-ttu-id="d6e3c-114">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="d6e3c-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/resources/management)


## <a name="samples"></a><span data-ttu-id="d6e3c-115">샘플</span><span class="sxs-lookup"><span data-stu-id="d6e3c-115">Samples</span></span>

* [<span data-ttu-id="d6e3c-116">리소스 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="d6e3c-116">Manage resource groups</span></span>](https://github.com/Azure-Samples/resources-dotnet-manage-resource-group)
* [<span data-ttu-id="d6e3c-117">리소스 관리</span><span class="sxs-lookup"><span data-stu-id="d6e3c-117">Manage resources</span></span>](https://github.com/Azure-Samples/resources-dotnet-manage-resource)
* [<span data-ttu-id="d6e3c-118">ARM 템플릿을 사용하여 리소스 배포</span><span class="sxs-lookup"><span data-stu-id="d6e3c-118">Deploy resources with ARM templates</span></span>](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template)
* [<span data-ttu-id="d6e3c-119">ARM 템플릿을 사용하여 리소스 배포(진행 상황과 함께)</span><span class="sxs-lookup"><span data-stu-id="d6e3c-119">Deploy resources with ARM templates (with progress)</span></span>](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template-with-progress)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
