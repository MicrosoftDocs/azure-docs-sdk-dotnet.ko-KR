---
title: Azure 앱 보안에 대 한 .NET 자습서
description: Azure에서 실행되는 .NET 앱에서 응용 프로그램 보안 및 ID 관리에 대한 자습서입니다.
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 88ecfc69fbd57becf1adf1163a063c0d2bb086a8
ms.sourcegitcommit: 61638b504b6c4d96b357894835c80c2680a99fe6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750591"
---
# <a name="tutorials-for-authenticating-users-in-your-net-apps-running-on-azure"></a>Azure에서 실행되는 .NET 앱에서 사용자 인증에 대한 자습서

다음 테이블은 사용자 인증 및 Azure에서 실행되는 .NET 응용 프로그램 보안에 대한 자세한 자습서에 연결합니다.

샘플 소스 코드는 [Azure 서비스 샘플](https://azure.microsoft.com/resources/samples/?platform=dotnet) 목록을 참조하세요.

| | |
|---|---|
|**Active Directory**||
| [Visual Studio에 연결된 서비스를 사용하여 웹 응용 프로그램에 Azure Active Directory 추가][5] | Visual Studio에서 Azure AD에 웹 앱 연결 |
| [Azure AD에서 웹앱 로그인 및 로그아웃][1] | ADAL 라이브러리를 사용하여 ASP.NET에서 사용자를 로그인 및 로그아웃합니다. |
| [Azure AD로 데스크톱 응용 프로그램 인증][2]| ADAL을 사용하여 Windows Desktop WPF 앱에 Azure AD를 통합합니다. | 
| [Azure AD로 Web API 인증][3] | Azure AD에서 전달자 토큰을 사용하여 웹 API를 보호합니다. |
|**Key Vault**||
| [Visual Studio에 연결된 서비스를 사용하여 웹 응용 프로그램에 Key Vault 추가][6] | Visual Studio에서 Azure Key Vault에 웹 앱 연결 |
| [웹 응용 프로그램에서 Azure Key Vault 사용][4] | 웹 응용 프로그램에서 사용할 수 있도록 Azure Key Vault의 비밀에 액세스합니다. | 

[1]: /azure/active-directory/develop/active-directory-devquickstarts-webapp-dotnet
[2]: /azure/active-directory/develop/active-directory-devquickstarts-dotnet
[3]: /azure/active-directory/develop/active-directory-devquickstarts-webapi-dotnet
[4]: /azure/key-vault/key-vault-use-from-web-application
[5]: /azure/active-directory/develop/vs-active-directory-add-connected-service
[6]: /azure/key-vault/vs-key-vault-add-connected-service