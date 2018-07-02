---
title: .NET용 Azure Active Directory 라이브러리
description: .NET용 Azure Active Directory 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, AAD, Active Directory
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: active-directory
ms.custom: devcenter, svc-overview
ms.openlocfilehash: a5a228fcde29dbef6a6e8d0482121ee710b002a4
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065863"
---
# <a name="azure-active-directory-libraries-for-net"></a>.NET용 Azure Active Directory 라이브러리

## <a name="overview"></a>개요

Azure Active Directory를 사용하여 사용자를 로그온하고 응용 프로그램 및 API에 대한 액세스를 관리합니다.

Azure Active Directory를 시작하려면 [Azure AD에서 ASP.NET 웹앱 로그인 및 로그아웃](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)을 참조하세요.

## <a name="client-library"></a>클라이언트 라이브러리

OAuth2, OpenID Connect, Active Directory Graph API 인증 또는 [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference)을 통해 사용자 또는 응용 프로그램에 연결하고 인증합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.IdentityModel.Clients.ActiveDirectory
```

### <a name="code-example"></a>코드 예제

데스크톱 응용 프로그램에 대한 액세스 토큰을 검색합니다.

```csharp
/* Include this "using" directive...
using Microsoft.IdentityModel.Clients.ActiveDirectory;
*/

AuthenticationResult result = null;
AuthenticationContext authContext = new AuthenticationContext("https://someauthority.com");
try
{
    result = await authContext.AcquireTokenAsync(graphResourceId, clientId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
}
catch (AdalException ex)
{
    // An unexpected error occurred, or user canceled the sign in.
    if (ex.ErrorCode != "access_denied")
        MessageBox.Show(ex.Message);

    return;
}
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/activedirectory/client)

### <a name="samples"></a>샘플

* [OpenID Connect를 사용하여 Azure AD 테넌트의 사용자 인증](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect)
* [Oauth2를 사용하여 응용 프로그램 사용 권한으로 웹 API 호출](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-appidentity)
* [응용 프로그램에서 RBAC(역할 기반 액세스 제어) 사용](https://github.com/Azure-Samples/active-directory-dotnet-webapp-roleclaims)

[Azure Active Directory 코드 샘플](/azure/active-directory/develop/active-directory-code-samples)의 전체 컬렉션을 탐색합니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
