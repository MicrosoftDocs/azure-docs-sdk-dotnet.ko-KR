---
title: "Azure 앱 보안에 대 한 .NET 자습서"
description: "Azure에서 실행되는 .NET 앱에서 응용 프로그램 보안 및 ID 관리에 대한 자습서입니다."
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 0cd530ef5f70778571e2f702aebc4a8b43c40e93
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2017
---
# <a name="tutorials-for-authenticating-users-in-your-net-apps-running-on-azure"></a><span data-ttu-id="54c6b-103">Azure에서 실행되는 .NET 앱에서 사용자 인증에 대한 자습서</span><span class="sxs-lookup"><span data-stu-id="54c6b-103">Tutorials for authenticating users in your .NET apps running on Azure</span></span>

<span data-ttu-id="54c6b-104">다음 테이블은 사용자 인증 및 Azure에서 실행되는 .NET 응용 프로그램 보안에 대한 자세한 자습서에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="54c6b-104">The following table links to in-depth tutorials for authenticating users and securing .NET applications running on Azure.</span></span>

<span data-ttu-id="54c6b-105">샘플 소스 코드는 [Azure 서비스 샘플](https://azure.microsoft.com/resources/samples/?platform=dotnet) 목록을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54c6b-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>

| | |
|---|---|
|<span data-ttu-id="54c6b-106">**Active Directory**</span><span class="sxs-lookup"><span data-stu-id="54c6b-106">**Active Directory**</span></span>||
| <span data-ttu-id="54c6b-107">[Azure AD에서 웹앱 로그인 및 로그아웃][1]</span><span class="sxs-lookup"><span data-stu-id="54c6b-107">[Web app sign-in and sign-out with Azure AD][1]</span></span> | <span data-ttu-id="54c6b-108">ADAL 라이브러리를 사용하여 ASP.NET에서 사용자를 로그인 및 로그아웃합니다.</span><span class="sxs-lookup"><span data-stu-id="54c6b-108">Sign users in and out of your ASP.NET with the ADAL library.</span></span>
| <span data-ttu-id="54c6b-109">[Azure AD로 데스크톱 응용 프로그램 인증][2]</span><span class="sxs-lookup"><span data-stu-id="54c6b-109">[Desktop application authentication with Azure AD][2]</span></span>| <span data-ttu-id="54c6b-110">ADAL을 사용하여 Windows Desktop WPF 앱에 Azure AD를 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="54c6b-110">Integrate Azure AD into a Windows Desktop WPF app using ADAL.</span></span> | 
| <span data-ttu-id="54c6b-111">[Azure AD로 Web API 인증][3]</span><span class="sxs-lookup"><span data-stu-id="54c6b-111">[Web API authentication with Azure AD][3]</span></span> | <span data-ttu-id="54c6b-112">Azure AD에서 전달자 토큰을 사용하여 웹 API를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="54c6b-112">Protect a web API using bearer tokens from Azure AD.</span></span> |
|<span data-ttu-id="54c6b-113">**키 자격 증명 모음**</span><span class="sxs-lookup"><span data-stu-id="54c6b-113">**Key Vault**</span></span>||
| <span data-ttu-id="54c6b-114">[웹 응용 프로그램에서 Azure Key Vault 사용][4]</span><span class="sxs-lookup"><span data-stu-id="54c6b-114">[Use Azure Key Vault from a Web Application][4]</span></span> | <span data-ttu-id="54c6b-115">웹 응용 프로그램에서 사용할 수 있도록 Azure Key Vault의 비밀에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="54c6b-115">Access a secret from an Azure Key Vault so that it can be used in your web application.</span></span> | 

[1]: /azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet
[2]: /azure/active-directory/develop/active-directory-devquickstarts-dotnet
[3]: /azure/active-directory/develop/active-directory-devquickstarts-webapi-dotnet
[4]: /azure/key-vault/key-vault-use-from-web-application