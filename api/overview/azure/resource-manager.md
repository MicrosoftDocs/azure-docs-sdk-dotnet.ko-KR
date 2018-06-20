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
# <a name="azure-resource-manager-libraries-for-net"></a>.NET용 Azure Resource Manager 라이브러리

## <a name="overview"></a>개요

Azure 리소스 관리자를 사용하면 솔루션에서 리소스를 그룹으로 사용할 수 있습니다.  리소스 관리자에 대한 자세한 내용은 [Azure Resource Manager 개요](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)를 참조하세요.

## <a name="management-library"></a>관리 라이브러리

.NET용 Azure Resource Manager 라이브러리를 통해 리소스 및 리소스 그룹을 만들고, 업데이트, 삭제 및 나열할 수 있습니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.ResourceManager.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="example"></a>예제

이 예제는 새 리소스 그룹을 만듭니다.

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
> [관리 API 탐색](/dotnet/api/overview/azure/resources/management)


## <a name="samples"></a>샘플

* [리소스 그룹 관리](https://github.com/Azure-Samples/resources-dotnet-manage-resource-group)
* [리소스 관리](https://github.com/Azure-Samples/resources-dotnet-manage-resource)
* [ARM 템플릿을 사용하여 리소스 배포](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template)
* [ARM 템플릿을 사용하여 리소스 배포(진행 상황과 함께)](https://github.com/Azure-Samples/resources-dotnet-deploy-using-arm-template-with-progress)


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
