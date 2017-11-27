---
title: "Azure App Service로 ASP.NET 웹 응용 프로그램 마이그레이션"
description: "ASP.NET 웹 응용 프로그램을 온-프레미스에서 Azure App Service로 마이그레이션하는 방법에 대해 알아봅니다."
keywords: "Azure.NET, ASP.NET, App Service, Web App, 마이그레이션, 마이그레이션"
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: app-service
ms.custom: devcenter
ms.openlocfilehash: 8ad1bcd11a823c1b6f7e592a5990dd6f7ed06e97
ms.sourcegitcommit: ccc95adb96cf7d56ebce5e09bedf10c2d48f5e1f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="migrate-an-aspnet-web-application-to-azure-app-service"></a>Azure App Service로 ASP.NET 웹 응용 프로그램 마이그레이션

[App Service](https://docs.microsoft.com/azure/app-service/app-service-web-overview#why-use-web-apps)는 확장 가능한 웹 사이트와 웹 응용 프로그램 호스팅을 위해 최적화된 완전히 관리되는 계산 플랫폼 서비스입니다. 이 문서는 기존 애플리케이션을 Azure App Service로 리프트 앤드 시프트하는 방법, 고려할 수정 사항 및 클라우드로 이전하기 위한 추가 리소스에 대한 정보를 제공합니다.

시작할 준비가 되셨습니까? [Azure App Service에 ASP.NET + SQL 응용 프로그램 게시](https://go.microsoft.com/fwlink/?linkid=863214)

# <a name="preparation"></a>준비   
* [앱이 App Service에 적합한지 판단하는 방법](https://azure.microsoft.com/downloads/migration-assistant/)
* [클라우드로 데이터베이스 이동](https://go.microsoft.com/fwlink/?linkid=863217)

# <a name="considerations"></a>고려 사항
응용 프로그램을 마이그레이션하기 전에 고려해야 할 몇 가지 요소가 있습니다. 아래에는 응용 프로그램에 적용해야 할 잠재적인 수정 사항 목록과 이를 수행하는 방법이 나와 있습니다.

## <a name="sql-database-configuration"></a>SQL 데이터베이스 구성
응용 프로그램이 온-프레미스 데이터베이스를 사용하는 경우 웹앱에 대한 몇 가지 옵션이 있습니다. [Azure로 SQL 데이터베이스 마이그레이션에 대해 자세히 읽어보세요](https://go.microsoft.com/fwlink/?linkid=863217).

## <a name="iis"></a>IIS
기존에는 응용 프로그램에서 applicationHost.config를 통해 구성하던 모든 것을 이제 Azure Portal을 통해 구성할 수 있습니다. 이는 AppPool 비트 수, 웹 소켓 활성화/비활성화, 관리되는 파이프라인 버전, .NET Framework 버전(2.0/4.0) 등에 적용됩니다. [응용 프로그램 설정](https://docs.microsoft.com/en-us/azure/app-service/web-sites-configure)을 수정하려면 [Azure Portal](https://portal.azure.com)로 이동하고 웹앱의 블레이드를 연 다음 **응용 프로그램 설정** 탭을 선택합니다.

## <a name="authentication"></a>인증
응용 프로그램이 언제라도 사용자를 인증하는 경우, 응용 프로그램이 Azure Web Apps에 배포되면 작동하도록 이 기능을 수정해야 합니다. 한 가지 방법은 Azure AD Connect를 사용하여 온-프레미스 디렉터리와 Azure Active Directory를 통합하는 것입니다. [온-프레미스 디렉터리와 Azure Active Directory를 통합하는 방법에 대해 알아보세요](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

## <a name="virtual-network-modification"></a>가상 네트워크 수정
둘 이상의 Azure Service를 사용하는 경우, 가상 네트워크를 사용하여 이러한 서비스 간에 안전하게 통신하는 것을 고려할 수 있습니다. VPN 또는 ExpressRoute를 사용하여 온-프레미스 네트워크에서 [Azure Virtual Network](https://docs.microsoft.com/en-us/azure/app-service/web-sites-integrate-with-vnet)로의 연결을 구성할 수 있습니다.

## <a name="monitoring-and-diagnostics"></a>모니터링 및 진단
모니터링 및 진단을 위해 현재 온-프레미스 솔루션은 클라우드에서 작동하지 않을 수 있습니다. 그러나 Azure는 앱의 문제를 식별하고 디버깅할 수 있도록 로깅, 모니터링 및 진단을 위한 도구를 제공합니다. 구성에서 웹앱에 대해 쉽게 진단하고 Azure Application Insights에 기록된 로그를 볼 수 있습니다. [웹앱에 대한 진단 로깅을 사용하는 방법에 대해 자세히 알아보세요](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log).

## <a name="connection-strings-and-application-settings"></a>연결 문자열 및 응용 프로그램 설정
정보를 안전하게 유지하는 한 가지 옵션은 응용 프로그램에서 사용되는 중요한 정보를 안전하게 저장하는 서비스인 [Azure KeyVault](https://docs.microsoft.com/azure/key-vault/)를 사용하는 것입니다. 또는 이 데이터를 App Service 설정으로 저장할 수 있습니다.

## <a name="dns"></a>DNS
응용 프로그램의 요구 사항에 따라 DNS 구성을 업데이트해야 할 수도 있습니다. 이러한 DNS 설정은 App Service [사용자 지정 도메인 설정](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain)에서 구성할 수 있습니다. 고려할 또 다른 요소는 [기존 사용자 지정 SSL 인증서 바인딩](https://docs.microsoft.com/en-us/azure/app-service/app-service-web-tutorial-custom-ssl)입니다.

## <a name="file-system-and-storage"></a>파일 시스템 및 저장소
응용 프로그램에서 데이터를 유지하는 경우 대신 Azure Storage를 사용하도록 업데이트해야 합니다. Azure Storage는 SMB 프로토콜, Blob Storage, 단순 대기열 및 비 관계형 테이블을 통해 공유하기 위해 파일 공유를 제공하는 서비스입니다. [Azure Storage 파일 공유에 대해 자세히 알아보세요](https://docs.microsoft.com/azure/storage/files/storage-files-introduction).

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [Azure App Service로 ASP.NET 웹 응용 프로그램 마이그레이션](https://aka.ms/azure-webapp-migrate)
