---
title: 올바른 Azure 호스팅 옵션 선택
description: 어떤 Azure 마이그레이션 경로가 ASP.NET 웹 응용 프로그램에 적합한지 알아봅니다.
author: CESARDELATORRE
ms.author: cesardl
ms.date: 11/15/2017
ms.openlocfilehash: 7c0d10436efa86c3d4a60f80e2eebd935ee01cee
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190616"
---
# <a name="choose-the-right-azure-hosting-option"></a>올바른 Azure 호스팅 옵션 선택

이 문서는 기존 .NET Framework 응용 프로그램을 온-프레미스에서 Azure로 마이그레이션할 때 Azure의 여러 선택 항목을 여러 가지 고려 사항과 비교 내용을 제공합니다.

기존.NET 응용 프로그램을 Azure로 마이그레이션할 때 고려해야 할 기본 영역은 다음과 같습니다.

1.  계산 선택 항목
2.  데이터베이스 선택 항목
3.  네트워킹 및 보안 고려 사항
4.  인증 및 권한 부여 고려 사항

## <a name="compute-choices"></a>계산 선택 항목

기존 .NET Framework 응용 프로그램을 Azure로 마이그레이션하는 경우 여러 가지 선택 사항이 있습니다.  그러나 .NET Framework는 Windows에 따라 다르기 때문에 다음 선택 사항은 Windows 기반 계산 서비스로 제한됩니다.

다음 표는 기존 .NET 응용 프로그램에 적합한 컴퓨팅 마이그레이션 경로를 선택하는 데 도움이 되는 몇 가지 비교 및 권장 사항을 보여줍니다.

|                 | Azure VM | Azure App Service | Windows 컨테이너 |
|-----------------|-----------|-------------------|--------------------|
|사용하는 경우      |<ul><li>응용 프로그램은 서버 및 로컬 .msi 설치에 크게 의존합니다.</li><li>가장 쉬운 응용 프로그램 마이그레이션 경로가 필요합니다.</li></ul>|앱은 서버에 의존하지 않으며, 데이터베이스 서버에 액세스하는 순수한 ASP.NET 웹앱(MVC, WebForm) 또는 N 계층 앱(Web API, WCf)입니다. |<ul><li>응용 프로그램은 원본 서버에 종속되지만 이러한 종속성이 Docker Windows 이미지에도 포함될 수 있습니다.</li><li>[Cloud DevOps-Ready](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-devops/reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications)가 되도록 앱을 현대화</li></ul>|
|장점 및 혜택  |<ul><li>가장 쉬운 마이그레이션 경로</li><li>친숙한 환경. 배포 환경은 온-프레미스 서버와 아주 유사한 VM입니다.</li></ul> |지속적인 PaaS 유지 관리, Azure에서 앱을 관리하고 확장하는 가장 간단한 방법입니다. |<ul><li>미래를 대비한 Cloud DevOps-Ready에는 앱 컨테이너에 포함된 종속성이 있습니다.</li><li>.NET / C# 코드를 다시 고려할 필요가 거의 없습니다.</li></ul> |
|단점             |IaaS. 유지 관리 비용이 많이 듭니다. 네트워킹, 부하 분산 장치, 스케일 아웃, IIS 관리 등에 대한 VM 인프라를 관리해야 합니다. |<ul><li>모든 앱이 [지원](http://www.migratetoazure.net/ReadinessAssessment)되지 않음</li><li>일부 앱은 리팩토링되어야 할 수 있으며 약간 재구성되더라도 Azure App Service를 지원합니다.</li></ul> |<ul><li>Docker의 기술 습득 곡선</li><li>일부 코드 및 앱 구성 설정 변경</li></ul>|
|요구 사항 |온-프레미스용 앱과 동일한 요구 사항을 가진 Windows Server VM | [Azure App Service의 호환성 분석](https://www.migratetoazure.net/Resources)에서 지정된 Microsoft Azure Websites 요구 사항. |<ul><li>[컨테이너가 있는 Windows Server 2016 - Azure VM](https://azuremarketplace.microsoft.com/marketplace/apps/Microsoft.WindowsServer?tab=Overview)<br />또는</li><li>[Azure Container Service(AKS)](https://azure.microsoft.com/services/container-service/) (즉 Kubernetes orchestrator)<br />또는<li>[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) 오케스트레이터</li></ul> |
|마이그레이션하는 방법 |[Azure Virtual Machines로 마이그레이션](https://go.microsoft.com/fwlink/?linkid=862531) 참조 | [Azure App Service 마이그레이션](https://go.microsoft.com/fwlink/?linkid=862532) 참조 | [Azure 및 Windows Containers eBook을 사용하여 기존 .NET 앱 현대화](https://aka.ms/liftandshiftwithcontainersebook)에 설명된 고려 사항, 시나리오 및 연습을 따르세요. |

 다음 순서도 다이어그램은 기존 .NET Framework 응용 프로그램에 대해 Azure로 마이그레이션을 계획할 때 의사 결정 트리를 보여줍니다. 옵션 A는 실행 가능하면 시도하여 수행할 수 있는 첫 번째 옵션이지만, 옵션 B가 가장 실행하기 쉬운 경로입니다.

![호스팅 의사 결정 트리를 보여주는 순서도](media/dotnet-howto-choose-migration/decision-tree.png)

## <a name="database-choices"></a>데이터베이스 선택 항목

관계형 데이터베이스를 Azure로 마이그레이션하는 경우 여러 가지 선택 항목이 있습니다. [Azure로 SQL Server 데이터베이스 마이그레이션](https://go.microsoft.com/fwlink/?linkid=862533)을 참조하여 기존.NET 응용 프로그램에 적합한 데이터베이스 마이그레이션 경로를 선택합니다.

## <a name="networking-and-security-considerations"></a>네트워킹 및 보안 고려 사항

Microsoft Azure와 같은 공용 클라우드에 응용 프로그램을 배포하는 경우 [Azure와 온-프레미스 사이의 DMZ](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) 또는 [Azure와 인터넷 사이의 DMZ](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz)와 같은 [네트워크 DMZ를 생성하여](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/) 특정 네트워크를 격리하고 보호할 수 있습니다. DMZ는 [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)로 구현할 수 있습니다.
Azure Virtual Network를 사용하여 다음을 수행할 수 있습니다.

- 제어하는 하이브리드 인프라 구축
- 자체 IP 주소 및 DNS 서버 가져오기
- IPSec VPN 또는 ExpressRoute로 연결 보호
- 서브넷 간 트래픽에 대한 세부적인 제어 확보
- 가상 어플라이언스가 포함된 고급 네트워크 토폴로지 만들기
- 응용 프로그램에 대해 격리되고 매우 안전한 환경 실현
 
자체 가상 네트워크 구축을 시작하려면 [Azure Virtual Network 설명서](https://docs.microsoft.com/azure/virtual-network/)를 참조하세요.

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>Azure로 마이그레이션할 때 인증 및 권한 부여 고려 사항

클라우드로 이동하는 조직의 가장 큰 관심사는 보안입니다. 대부분의 회사는 보안 모델을 설계하고 개발하는 데 상당한 시간, 비용 및 엔지니어링을 투자했으며, ID 저장소 및 Single Sign-On 솔루션과 같은 기존 투자를 활용할 수 있어야 합니다.

온-프레미스를 실행하는 많은 기존 엔터프라이즈 B2E .NET 응용 프로그램은 인증 및 ID 관리를 위해 Active Directory를 사용합니다.  Azure AD Connect는 온-프레미스 디렉터리와 Azure Active Directory를 통합하도록 해줍니다.  시작하려면 [Azure Active Directory와 온-프레미스 디렉터리 통합](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)을 참조하세요.

Azure Active Directory에 관련된 추가 계획은 [하이브리드 ID 솔루션에 대한 ID 요구 사항](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs)을 참조하세요.

다른 인증 프로토콜 선택 사항은 소비자 관련 응용 프로그램에서 일반적인 [OAuth ](https://en.wikipedia.org/wiki/OAuth) 및 [OpenID](https://en.wikipedia.org/wiki/OpenID)입니다.  OAuth를 사용하여 IdentityServer4로 래핑된 ASP.NET Identity SQL 데이터베이스와 같은 자율적인 ID 데이터베이스를 사용할 때는 일반적으로 온-프레미스 데이터베이스 또는 디렉토리에 대한 연결이 필요하지 않습니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [Azure App Service로 ASP.NET 웹 응용 프로그램 마이그레이션](dotnet-howto-migrate-app-service.md)