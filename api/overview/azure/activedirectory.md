---
title: .NET용 Azure Active Directory 라이브러리
description: .NET용 Azure Active Directory 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, AAD, Active Directory
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: active-directory
ms.custom: devcenter, svc-overview
ms.openlocfilehash: aa20715fb62b1d4b714245c404f1a7c142caf586
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
ms.locfileid: "23565994"
---
# <a name="azure-active-directory-libraries-for-net"></a><span data-ttu-id="51447-104">.NET용 Azure Active Directory 라이브러리</span><span class="sxs-lookup"><span data-stu-id="51447-104">Azure Active Directory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="51447-105">개요</span><span class="sxs-lookup"><span data-stu-id="51447-105">Overview</span></span>

<span data-ttu-id="51447-106">Azure Active Directory를 사용하여 사용자를 로그온하고 응용 프로그램 및 API에 대한 액세스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="51447-106">Sign-on users and manage access to applications and APIs with Azure Active Directory.</span></span>

<span data-ttu-id="51447-107">Azure Active Directory를 시작하려면 [Azure AD에서 ASP.NET 웹앱 로그인 및 로그아웃](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51447-107">To get started with Azure Active Directory, see [ASP.NET web app sign-in and sign-out with Azure AD](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="51447-108">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="51447-108">Client library</span></span>

<span data-ttu-id="51447-109">OAuth2, OpenID Connect, Active Directory Graph API 인증 또는 [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference)을 통해 사용자 또는 응용 프로그램에 연결하고 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="51447-109">Connect and authenticate users or applications over OAuth2, OpenID Connect, Active Directory Graph API authentication or [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).</span></span>

<span data-ttu-id="51447-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="51447-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="51447-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="51447-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="net-core-cli"></a><span data-ttu-id="51447-112">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="51447-112">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.IdentityModel.Clients.ActiveDirectory
```

### <a name="code-example"></a><span data-ttu-id="51447-113">코드 예제</span><span class="sxs-lookup"><span data-stu-id="51447-113">Code Example</span></span>

<span data-ttu-id="51447-114">데스크톱 응용 프로그램에 대한 액세스 토큰을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="51447-114">Retrieve an access token for a desktop application.</span></span>

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
> [<span data-ttu-id="51447-115">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="51447-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/activedirectory/client)

### <a name="samples"></a><span data-ttu-id="51447-116">샘플</span><span class="sxs-lookup"><span data-stu-id="51447-116">Samples</span></span>

* [<span data-ttu-id="51447-117">OpenID Connect를 사용하여 Azure AD 테넌트의 사용자 인증</span><span class="sxs-lookup"><span data-stu-id="51447-117">Use OpenID Connect to authenticate users from an Azure AD tenant</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect)
* [<span data-ttu-id="51447-118">Oauth2를 사용하여 응용 프로그램 사용 권한으로 웹 API 호출</span><span class="sxs-lookup"><span data-stu-id="51447-118">Use Oauth2 to call a web API with application permissions</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-appidentity)
* [<span data-ttu-id="51447-119">응용 프로그램에서 RBAC(역할 기반 액세스 제어) 사용</span><span class="sxs-lookup"><span data-stu-id="51447-119">Use role-based access control (RBAC) in an application</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-roleclaims)

<span data-ttu-id="51447-120">[Azure Active Directory 코드 샘플](/azure/active-directory/develop/active-directory-code-samples)의 전체 컬렉션을 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="51447-120">Explore the full collection of [Azure Active Directory code samples](/azure/active-directory/develop/active-directory-code-samples).</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
