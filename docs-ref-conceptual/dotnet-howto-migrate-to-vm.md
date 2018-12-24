---
title: Azure Virtual Machine으로 ASP.NET 웹 애플리케이션 마이그레이션
description: ASP.NET 웹 애플리케이션을 온-프레미스에서 Azure Virtual Machine으로 마이그레이션하는 방법에 대해 알아봅니다.
ms.date: 11/15/2017
ms.service: virtual-machines
ms.openlocfilehash: b33bffdf774688d9d7eb5947f1a080b021ba259c
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190706"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>Azure Virtual Machine으로 ASP.NET 웹 애플리케이션 마이그레이션

이 문서에서는 ASP.NET 웹 애플리케이션을 온-프레미스에서 Azure Virtual Machine으로 마이그레이션하는 방법에 대한 개요를 제공합니다.

## <a name="quickstart"></a>빠른 시작

가상 머신을 만들고 여기에 앱을 게시하는 방법에 대해 알아봅니다. [Azure VM에 게시](https://tutorials.visualstudio.com/aspnet-vm/intro)

## <a name="get-started"></a>시작

이 자습서에서는 가상 머신을 생성(또는 마이그레이션)하고 웹 애플리케이션을 게시하고 Azure에서 애플리케이션을 지원하는 데 필요한 기타 작업을 수행하는 단계를 보여줍니다.

- 다음 두 옵션 중 하나를 사용하여 Azure에서 ASP.NET 애플리케이션용 가상 머신을 만듭니다.
    - [ASP.NET 응용 프로그램용 새 가상 머신 만들기](https://go.microsoft.com/fwlink/?linkid=863237)
    - [기존 온-프레미스 가상 머신 마이그레이션](https://docs.microsoft.com/azure/site-recovery/tutorial-migrate-on-premises-to-azure)
- [Visual Studio를 사용하여 앱 게시](https://go.microsoft.com/fwlink/?linkid=863240)
- [VM용 보안 가상 네트워크 만들기](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [응용 프로그램용 CI/CD 파이프라인 만들기](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [고가용성 및 확장성을 위해 VM 확장 집합으로 이동](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a>고려 사항

### <a name="benefits"></a>이점

가상 머신은 애플리케이션을 온-프레미스에서 클라우드로 마이그레이션하는 가장 쉬운 방법을 제공합니다.  이를 통해 애플리케이션이 온-프레미스를 사용하는 것과 동일한 환경을 복제할 수 있지만, 사용자의 데이터 센터를 관리할 필요가 없습니다.  Virtual Machine Scale Sets는 Virtual Machines에서 실행되는 애플리케이션을 위해 고가용성 및 확장성을 제공합니다.

### <a name="virtual-machine-size"></a>Virtual Machine 크기

워크로드에 가장 최적화된 가상 머신 크기 및 유형을 선택합니다.  자세한 내용은 [Azure에서 Windows 가상 머신에 대한 크기](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)를 참조하세요.

### <a name="maintenance"></a>유지 관리

온-프레미스 머신처럼 가상 머신<sup>&#42;</sup>을 유지 관리하고 업데이트할 책임이 있습니다.  [Azure App Service](https://docs.microsoft.com/azure/app-service/)와 같은 PaaS(Platform as a Service) 환경 또는 [컨테이너](https://docs.microsoft.com/azure/app-service/containers/)에서 응용 프로그램을 실행할 수 있는 경우, 그럴 필요가 없습니다.

*<sup>&#42;</sup>[가상 머신 확장 집합을 위한 자동 OS 업그레이드](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)는 현재 미리 보기 서비스로서 사용할 수 있습니다.*

### <a name="virtual-networks"></a>Virtual Network

Azure Virtual Network를 사용하여 다음을 수행할 수 있습니다.
- 제어하는 하이브리드 인프라 구축
- 자체 IP 주소 및 DNS 서버 가져오기
- 애플리케이션에 대해 격리되고 매우 안전한 환경 만들기
- 몇 가지 [연결 옵션](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti) 방법 중 하나를 사용하여 온-프레미스 네트워크에 VM 연결
- [ExpressRoute](https://azure.microsoft.com/services/expressroute/)를 사용하여 온-프레미스 네트워크에 가상 머신 통합

시작하려면 [Virtual Network 설명서](https://docs.microsoft.com/azure/virtual-network/)를 참조하세요.

### <a name="active-directory"></a>Active Directory
많은 애플리케이션이 인증 및 ID 관리를 위해 Active Directory를 사용합니다.  
- Azure AD Connect는 온-프레미스 디렉터리와 Azure Active Directory를 통합하도록 해줍니다.  시작하려면 [Azure Active Directory와 온-프레미스 디렉터리 통합](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)을 참조하세요.  
- 또는 [ExpressRoute](https://azure.microsoft.com/services/expressroute/)를 사용하면 애플리케이션에서 온-프레미스 Active Directory에 액세스할 수 있습니다.

### <a name="sql-databases"></a>SQL Database

애플리케이션이 온-프레미스 데이터베이스를 사용하는 경우 앱은 기본적으로 이 데이터베이스와 통신할 수 없습니다. 다음 중 하나가 가능합니다.
- 애플리케이션에서 온-프레미스를 실행하는 데이터베이스에 액세스할 수 있도록 해주는 하이브리드 네트워크를 구성합니다.  
- Azure로 데이터베이스를 마이그레이션합니다.  자세한 내용은 [Azure로 SQL Server 데이터베이스 마이그레이션](dotnet-howto-migrate-sql.md)을 참조하세요.

### <a name="high-availability-and-scalability"></a>고가용성 및 확장성 

#### <a name="virtual-machine-scale-sets"></a>Virtual Machine Scale Sets
애플리케이션의 가용성이 높은지 그리고 확장할 수 있는지 확인하고 VM 이미지를 Azure Virtual Machine Scale Set로 마이그레이션하여 애플리케이션의 가용성과 확장성을 높일 수 있습니다.  VM Scale Sets는 이미 구성한 기존 VM을 사용하거나 애플리케이션으로 이미지를 빌드하기 위해 빌드 파이프라인을 설정하는 기능을 제공합니다.  

시작하려면 [가상 머신 확장 집합에 애플리케이션 배포](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)를 참조하세요.

#### <a name="centralized-logging"></a>중앙 집중식 로깅
여러 인스턴스에서 애플리케이션을 실행하는 경우 [Azure Storage](https://docs.microsoft.com/azure/storage/)와 같은 중앙 위치에 로그를 저장하는 것이 좋습니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [Azure로 SQL Server 데이터베이스 마이그레이션](dotnet-howto-migrate-sql.md)