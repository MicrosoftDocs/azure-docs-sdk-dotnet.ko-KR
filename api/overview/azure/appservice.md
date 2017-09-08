---
title: ".NET용 Azure App Service 라이브러리"
description: ".NET용 Azure App Service 라이브러리에 대한 참조"
keywords: "Azure, .NET, SDK, API, Web Apps, App Service, 모바일, ASP.NET"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: e81a296ea5f5dadf7086439c88a347c20ec2abee
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-app-service-libraries-for-net"></a>.NET용 Azure App Service 라이브러리

## <a name="overview"></a>개요

[Azure App Service](/azure/app-service/app-service-value-prop-what-is)를 사용하면 웹 사이트, 웹 응용 프로그램, 서비스 및 REST API를 배포하고 크기 조정할 수 있습니다.

## <a name="management-api"></a>관리 API

관리 API를 사용하여 Azure App Service에서 호스팅되는 요소를 배포, 관리 및 크기 조정합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent)를 직접 설치합니다.


#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.AppService.Fluent
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Management.AppService.Fluent
```

### <a name="code-example"></a>코드 예제

새 웹앱을 만듭니다.

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
using Microsoft.Azure.Management.AppService.Fluent;
*/

IWebApp app1 = azure.WebApps
    .Define("MyUniqueWebAddress")
    .WithRegion(Region.USWest)
    .WithNewResourceGroup("MyResourceGroup")
    .WithNewWindowsPlan(PricingTier.StandardS1)
    .Create();
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/appservice/management)

### <a name="samples"></a>샘플

* [Azure용 .NET SDK를 사용하여 웹앱 관리(영문)](https://azure.microsoft.com/en-us/resources/samples/app-service-web-dotnet-manage/)
* [Azure App Service용 ASP.NET 샘플(영문)](https://azure.microsoft.com/en-us/resources/samples/app-service-web-dotnet-get-started/)

Azure App Service 샘플의 [전체 목록](https://azure.microsoft.com/en-us/resources/samples/?platform=dotnet&term=app%20service)을 봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package