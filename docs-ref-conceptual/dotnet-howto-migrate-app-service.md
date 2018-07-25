---
title: .NET 웹 앱 또는 서비스를 Azure App Service로 마이그레이션
description: .NET 웹 앱 또는 서비스를 온-프레미스에서 Azure App Service로 마이그레이션하는 방법에 대해 알아봅니다.
keywords: Azure.NET, ASP.NET, WCF, App Service, Web App, 마이그레이션, 마이그레이션
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 07/16/2018
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: app-service
ms.custom: devcenter
ms.openlocfilehash: 643d758af8f90f22791d3b7deb18ae6233067ef0
ms.sourcegitcommit: 779c1b202d3670cfa0b9428c89f830cad9ec7e9d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39135721"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a>.NET 웹 앱 또는 서비스를 Azure App Service로 마이그레이션 

[App Service](https://docs.microsoft.com/azure/app-service/app-service-web-overview#why-use-web-apps)는 확장 가능한 웹 사이트와 웹 응용 프로그램 호스팅을 위해 최적화된 완전히 관리되는 계산 플랫폼 서비스입니다. 이 문서는 기존 애플리케이션을 Azure App Service로 리프트 앤드 시프트하는 방법, 고려할 수정 사항 및 클라우드로 이전하기 위한 추가 리소스에 대한 정보를 제공합니다. 대부분의 ASP.NET 웹 사이트(Webforms, MVC) 및 서비스(Web API, WCF)는 변경 없이 Azure App Service로 바로 이동할 수 있습니다. 일부는 사소한 변경이 필요할 수 있으며 약간의 리팩터링이 필요할 수도 있습니다.

시작할 준비가 되셨습니까? [Azure App Service에 ASP.NET + SQL 응용 프로그램 게시](https://go.microsoft.com/fwlink/?linkid=863214)

## <a name="considerations"></a>고려 사항

### <a name="on-premises-resources-including-sql-server"></a>온-프레미스 리소스 (예: SQL Server)

마이그레이션하거나 변경해야 할 수 있으므로 온-프레미스 리소스에 대한 액세스를 확인합니다. 다음은 온-프레미스 리소스에 대한 액세스를 완화하기 위한 옵션입니다.

* [Azure Virtual Network](https://docs.microsoft.com/en-us/azure/app-service/web-sites-integrate-with-vnet)를 사용하여 App Service를 온-프레미스 리소스에 연결할 VPN을 만듭니다.
* [Azure Relay](https://docs.microsoft.com/en-us/azure/service-bus-relay/relay-what-is-it)를 사용하여 방화벽을 변경하지 않고 온-프레미스 서비스를 클라우드에 안전하게 노출합니다.
* [SQL database](https://go.microsoft.com/fwlink/?linkid=863217)의 Azure에 대한 종속성과 같은 종속성을 마이그레이션합니다.
* 클라우드의 서비스로서의 플랫폼 기능을 사용하여 종속성을 줄입니다. 예를 들어, 온-프레미스 메일 서버에 연결하는 것보다 [SendGrid](https://docs.microsoft.com/en-us/azure/sendgrid-dotnet-how-to-send-email) 사용을 고려해 봅니다. 

### <a name="port-bindings"></a>포트 바인딩

Azure App Service는 HTTP 트래픽에는 포트 80, HTTPS 트래픽에는 포트 443을 지원합니다.

WCF의 경우 다음 바인딩이 지원됩니다.

바인딩 | 메모
--------|--------
BasicHttp | 
WSHttp | 
WSDualHttpBinding | [웹 소켓 지원](https://docs.microsoft.com/azure/app-service/web-sites-configure)을 활성화해야 합니다.
NetHttpBinding | [웹 소켓 지원](https://docs.microsoft.com/azure/app-service/web-sites-configure)이 콜백 계약에 대해 활성화되어야 합니다.
NetHttpsBinding | [웹 소켓 지원](https://docs.microsoft.com/azure/app-service/web-sites-configure)이 콜백 계약에 대해 활성화되어야 합니다.
BasicHttpContextBinding |
WebHttpBinding |
WSHttpContextBinding |

### <a name="authentication"></a>인증

Azure App Service는 기본적으로 익명 인증을 지원하며 의도하는 경우 폼 인증을 지원합니다. Windows 인증은 Azure Active Directory 및 ADFS와 통합해야만 사용할 수 있습니다. [온-프레미스 디렉터리와 Azure Active Directory를 통합하는 방법에 대해 알아보세요](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

### <a name="assemblies-in-the-gac-global-assembly-cache"></a>GAC 어셈블리(전역 어셈블리 캐시) 

지원되지 않습니다. 필요한 어셈블리를 앱의 `\bin` 폴더에 복사하는 것이 좋습니다. 서버에 설치된 사용자 지정 .MSI(예: PDF 생성기 등)는 사용할 수 없습니다.  

### <a name="iis-settings"></a>IIS 설정
기존에는 응용 프로그램에서 applicationHost.config를 통해 구성하던 모든 것을 이제 Azure Portal을 통해 구성할 수 있습니다. 이는 AppPool 비트 수, 웹 소켓 활성화/비활성화, 관리되는 파이프라인 버전, .NET Framework 버전(2.0/4.0) 등에 적용됩니다. [응용 프로그램 설정](https://docs.microsoft.com/azure/app-service/web-sites-configure)을 수정하려면 [Azure Portal](https://portal.azure.com)로 이동하고 웹앱의 블레이드를 연 다음 **응용 프로그램 설정** 탭을 선택합니다.

#### <a name="iis5-compatibility-mode"></a>IIS5 호환 모드
IIS5 호환 모드는 지원되지 않습니다. Azure App Service에서 각 웹 앱과 그 아래의 모든 응용 프로그램은 특정 [응용 프로그램 풀](http://technet.microsoft.com/en-us/library/cc735247(v=WS.10).aspx) 집합으로 동일한 작업자 프로세스에서 실행됩니다.

#### <a name="iis7-schema-compliance"></a>IIS7+ 스키마 준수  
Azure App Service IIS 스키마의 일부 요소와 특성이 정의되지 있지 않습니다. 문제가 발생하는 경우 [XDT 변환](http://azure.microsoft.com/documentation/articles/web-sites-transform-extend/) 사용을 고려합니다.

#### <a name="single-application-pool-per-site"></a>사이트당 하나의 응용 프로그램 풀  
Azure App Service에서 각 웹 앱과 그 아래의 모든 응용 프로그램은 동일한 응용 프로그램 풀에서 실행됩니다. 일반적인 설정을 사용하여 단일 응용 프로그램 풀을 설정하거나 각 응용 프로그램에 대한 별도의 웹 앱을 만드는 것이 좋습니다.

### <a name="com-and-com-components"></a>COM 및 COM+ 구성 요소  
Azure App Service에서는 플랫폼에 COM 구성 요소를 등록할 수 없습니다. 앱이 COM 구성 요소를 사용하는 경우, 이러한 관리 코드로 다시 작성하고 사이트나 응용 프로그램을 사용하여 배포합니다.  

### <a name="physical-directories"></a>물리적 디렉터리 
Azure App Service는 물리적 드라이브 액세스를 허용하지 않습니다. SMB를 통해 파일에 액세스하려면 [Azure Files](https://docs.microsoft.com/azure/storage/files/storage-files-introduction)를 사용해야 할 수 있습니다. [Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction)는 HTTPS 통한 액세스를 위해 파일을 저장할 수 있습니다.  

### <a name="isapi-filters"></a>ISAPI 필터  
Azure App Service는 ISAPI 필터의 사용을 지원할 수는 있지만 ISAPI DLL은 귀하의 사이트를 사용하여 배포되어야 하며 web.config를 통해 등록되어야 합니다.  

### <a name="https-bindings-and-ssl"></a>HTTPS 바인딩 및 SSL 
HTTPS 바인딩은 마이그레이션되지 않으며, 귀하의 웹 사이트와 연결된 SSL 인증서도 마이그레이션되지 않습니다. 하지만 사이트 마이그레이션이 완료된 후 [SSL 인증서를 수동으로 업로드할 수 있습니다](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-ssl).  

### <a name="sharepoint-and-frontpage"></a>SharePoint 및 FrontPage 
SharePoint 및 FrontPage Server Extensions(FPSE)는 지원되지 않습니다.

### <a name="web-site-size"></a>웹 사이트 크기  
무료 사이트는 1GB 콘텐츠로 크기가 제한됩니다. 귀하의 사이트가 1GB 보다 큰 경우, 유료 SKU로 업그레이드해야 합니다. [App Service 가격 책정](https://azure.microsoft.com/pricing/details/app-service/windows/)을 참조하세요. 

### <a name="database-size"></a>데이터베이스 크기  
SQL Server 데이터베이스에 대한 현재의 [SQL Database 가격 책정](http://azure.microsoft.com/pricing/details/sql-database)을 확인합니다.  

### <a name="azure-active-directory-aad-integration"></a>Azure Active Directory(AAD) 통합  
AAD는 무료 앱으로 작동하지 않습니다. AAD를 사용하려면 앱 SKU를 업그레이드해야 합니다. [App Service 가격 책정](https://azure.microsoft.com/pricing/details/app-service/windows/)을 참조하세요.

### <a name="monitoring-and-diagnostics"></a>모니터링 및 진단
모니터링 및 진단을 위해 현재 온-프레미스 솔루션은 클라우드에서 작동하지 않을 수 있습니다. 그러나 Azure는 앱의 문제를 식별하고 디버깅할 수 있도록 로깅, 모니터링 및 진단을 위한 도구를 제공합니다. 구성에서 웹앱에 대해 쉽게 진단하고 Azure Application Insights에 기록된 로그를 볼 수 있습니다. [웹앱에 대한 진단 로깅을 사용하는 방법에 대해 자세히 알아보세요](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="connection-strings-and-application-settings"></a>연결 문자열 및 응용 프로그램 설정
응용 프로그램에서 사용되는 중요한 정보를 안전하게 저장하는 서비스인 [Azure KeyVault](https://docs.microsoft.com/azure/key-vault/)를 사용하는 것이 좋습니다. 또는 이 데이터를 App Service 설정으로 저장할 수 있습니다.

### <a name="dns"></a>DNS
응용 프로그램의 요구 사항에 따라 DNS 구성을 업데이트해야 할 수도 있습니다. 이러한 DNS 설정은 App Service [사용자 지정 도메인 설정](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain)에서 구성할 수 있습니다. 

## <a name="azure-app-service-with-windows-containers"></a>Windows 컨테이너를 사용하는 Azure App Service
앱을 App Service로 직접 마이그레이션할 수 없는 경우 GAC, COM 구성 요소, MSI, .NET FX API, DirectX 등의 사용을 활성화하는 Windows 컨테이너를 사용하는 App Service를 사용하는 것이 좋습니다.

## <a name="additional-reading"></a>추가 참조 자료

* [앱이 App Service에 적합한지 판단하는 방법](https://azure.microsoft.com/downloads/migration-assistant/)
* [클라우드로 데이터베이스 이동](https://go.microsoft.com/fwlink/?linkid=863217)
* [Azure 웹 앱 샌드박스 세부 정보 및 제한 사항](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [Azure App Service로 ASP.NET 웹 응용 프로그램 마이그레이션](https://aka.ms/azure-webapp-migrate)
