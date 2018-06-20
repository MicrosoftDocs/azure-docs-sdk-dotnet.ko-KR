---
title: .NET용 Azure CDN 라이브러리
description: .NET용 Azure CDN 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, CDN
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: cdn
ms.custom: devcenter, svc-overview
ms.openlocfilehash: afc63f943fcac3afd9afb7d85f6e699079829244
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
ms.locfileid: "23566334"
---
# <a name="azure-cdn-libraries-for-net"></a>.NET용 Azure CDN 라이브러리

## <a name="overview"></a>개요

Azure CDN(Content Delivery Network)은 전략적으로 배치된 위치에서 정적 웹 콘텐츠를 캐싱하여 사용자에게 콘텐츠를 배달하기 위한 최대 처리량을 제공합니다. CDN은 전 세계 물리적 노드에 콘텐츠를 캐시하여 고대역폭 콘텐츠를 배달하기 위한 글로벌 솔루션을 개발자에게 제공합니다.

Azure CDN에 대한 자세한 내용은 [Azure CDN(Content Delivery Network) 개요](https://docs.microsoft.com/azure/cdn/cdn-overview)를 참조하세요.


## <a name="management-library"></a>관리 라이브러리

.NET용 Azure CDN 라이브러리를 사용하여 CDN 프로필 및 끝점의 생성과 관리를 자동화할 수 있습니다. 

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Cdn.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Cdn.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Cdn.Fluent
```

### <a name="example"></a>예제

이 예제에서는 `www.contoso.com`을 가리키는 새 끝점을 사용하여 새 CDN 프로필을 만듭니다.

```csharp
/* Include these "using" directives.
using Microsoft.Azure.Management.Cdn.Fluent;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

ICdnProfile profileDefinition = azure.CdnProfiles.Define("CdnProfileName")
    .WithRegion(Region.USCentral)
    .WithExistingResourceGroup("ResourceGroupName")
    .WithStandardVerizonSku()
    .WithNewEndpoint("www.contoso.com")
    .Create();

```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/cdn/management)


## <a name="samples"></a>샘플

* [CDN 시작 - CDN 관리 - .NET에서(영문)](https://github.com/Azure-Samples/cdn-dotnet-manage-cdn)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
