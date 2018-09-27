---
title: .NET용 Azure Active Directory 라이브러리
description: .NET용 Azure Active Directory 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: active-directory
ms.openlocfilehash: 0226f06546f7dc14b9ab3392008744754d47a19a
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190226"
---
# <a name="azure-active-directory-libraries-for-net"></a><span data-ttu-id="a84a9-103">.NET용 Azure Active Directory 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a84a9-103">Azure Active Directory libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="a84a9-104">개요</span><span class="sxs-lookup"><span data-stu-id="a84a9-104">Overview</span></span>

<span data-ttu-id="a84a9-105">Azure Active Directory를 사용하여 사용자를 로그온하고 응용 프로그램 및 API에 대한 액세스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="a84a9-105">Sign-on users and manage access to applications and APIs with Azure Active Directory.</span></span>

<span data-ttu-id="a84a9-106">Azure Active Directory를 시작하려면 [Azure AD에서 ASP.NET 웹앱 로그인 및 로그아웃](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a84a9-106">To get started with Azure Active Directory, see [ASP.NET web app sign-in and sign-out with Azure AD](/azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet).</span></span>

## <a name="client-library"></a><span data-ttu-id="a84a9-107">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a84a9-107">Client library</span></span>

<span data-ttu-id="a84a9-108">OAuth2, OpenID Connect, Active Directory Graph API 인증 또는 [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference)을 통해 사용자 또는 응용 프로그램에 연결하고 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="a84a9-108">Connect and authenticate users or applications over OAuth2, OpenID Connect, Active Directory Graph API authentication or [SAML 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-saml-protocol-reference).</span></span>

<span data-ttu-id="a84a9-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a84a9-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.AppService.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="a84a9-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="a84a9-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="net-core-cli"></a><span data-ttu-id="a84a9-111">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a84a9-111">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.IdentityModel.Clients.ActiveDirectory
```

### <a name="code-example"></a><span data-ttu-id="a84a9-112">코드 예제</span><span class="sxs-lookup"><span data-stu-id="a84a9-112">Code Example</span></span>

<span data-ttu-id="a84a9-113">데스크톱 응용 프로그램에 대한 액세스 토큰을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a84a9-113">Retrieve an access token for a desktop application.</span></span>

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
> [<span data-ttu-id="a84a9-114">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="a84a9-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/activedirectory/client)

### <a name="samples"></a><span data-ttu-id="a84a9-115">샘플</span><span class="sxs-lookup"><span data-stu-id="a84a9-115">Samples</span></span>

* [<span data-ttu-id="a84a9-116">OpenID Connect를 사용하여 Azure AD 테넌트의 사용자 인증</span><span class="sxs-lookup"><span data-stu-id="a84a9-116">Use OpenID Connect to authenticate users from an Azure AD tenant</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-openidconnect)
* [<span data-ttu-id="a84a9-117">Oauth2를 사용하여 응용 프로그램 사용 권한으로 웹 API 호출</span><span class="sxs-lookup"><span data-stu-id="a84a9-117">Use Oauth2 to call a web API with application permissions</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-webapi-oauth2-appidentity)
* [<span data-ttu-id="a84a9-118">응용 프로그램에서 RBAC(역할 기반 액세스 제어) 사용</span><span class="sxs-lookup"><span data-stu-id="a84a9-118">Use role-based access control (RBAC) in an application</span></span>](https://github.com/Azure-Samples/active-directory-dotnet-webapp-roleclaims)

<span data-ttu-id="a84a9-119">[Azure Active Directory 코드 샘플](/azure/active-directory/develop/active-directory-code-samples)의 전체 컬렉션을 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="a84a9-119">Explore the full collection of [Azure Active Directory code samples](/azure/active-directory/develop/active-directory-code-samples).</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
