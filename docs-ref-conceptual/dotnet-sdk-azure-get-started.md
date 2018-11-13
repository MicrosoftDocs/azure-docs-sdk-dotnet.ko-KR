---
title: Azure 및 .NET 시작
description: Azure 및.NET에 대해 알아야 할 기본 사항을 알아봅니다.
ms.date: 09/19/2018
ms.openlocfilehash: 63587d7d5ccb79eee47185ff1f3ccb9cbd09c0ea
ms.sourcegitcommit: 0de939648fa01698016fed633200f8eb07c96eb7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51276583"
---
# <a name="get-started-with-azure-and-net"></a>Azure 및 .NET 시작

이 문서는 .NET 개발자가 Azure 서비스를 사용하여 응용 프로그램을 개발하기 위해 숙지해야 할 핵심 개념과 서비스에 대한 개요를 제공합니다.

## <a name="key-concepts"></a>주요 개념

**Azure 계정**: Azure 계정은 [Azure 포털](https://portal.azure.com) 또는 [Cloud Shell](https://shell.azure.com)과 같은 Azure 서비스에 로그인하는 데 사용하는 자격 증명입니다. Azure 계정이 없으면 [무료 계정을 만들](https://azure.microsoft.com/free/dotnet/) 수 있습니다.

**Azure 구독**: 구독은 Azure 리소스가 생성되는 청구 플랜입니다. 구독은 개별 구독 또는 회사에서 관리하는 엔터프라이즈 구독일 수 있습니다. Azure 계정에 여러 구독을 연결할 수 있습니다. 이 경우 리소스를 만들 때 올바른 구독을 선택하고 있는지 확인합니다. 자세한 내용은 [계정, 구독 및 청구 이해](https://docs.microsoft.com/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing)를 참조합니다.

> [!TIP]
> Visual Studio 구독이 있다면 [활성화를 대기하고 있는 월간 Azure 크레딧](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)이 있습니다.

**리소스 그룹**:리소스 그룹은 Azure 리소스를 관리용 그룹으로 조직하는 방법입니다. Azure에서 생성된 리소스는 컴퓨터의 폴더에 파일을 저장하는 것과 마찬가지로 리소스 그룹에 저장됩니다.

**호스팅**: Azure에서 코드를 실행하려면 사용자 제공 코드 실행을 지원하는 서비스에서 호스팅되어야 합니다.

**관리되는 서비스**: Azure는 Azure에 데이터 또는 정보를 제공하는 일부 서비스를 제공하며 Azure의 구현은 적절한 동작을 취합니다. 한 가지 예는 Azure Blob Storage로서, 파일을 제공하고 Azure가 파일의 읽기, 쓰기 및 지속을 처리합니다.

## <a name="choosing-a-hosting-option"></a>호스팅 옵션 선택

Azure 내 호스팅은 세 가지 범주로 나눌 수 있습니다.

* **IaaS(서비스 제공 인프라)** 를 사용하여 연결된 네트워크 및 저장소 구성 요소와 함께 필요한 가상 머신을 프로비전합니다. 그런 다음 해당 VM에 배치하려는 모든 소프트웨어 및 응용 프로그램을 배포합니다. 이 모델은 Microsoft에서 인프라를 관리한다는 점을 제외하고는 기존 온-프레미스 환경과 가장 가깝습니다. 운영 체제, 사용자 지정 소프트웨어 및 보안 업데이트를 포함하여 개별 VM을 여전히 관리합니다.

* **PaaS(서비스 제공 플랫폼)** 는 VM 또는 네트워킹 리소스를 관리할 필요 없이 응용 프로그램을 배포할 수 있는 관리되는 호스팅 환경을 제공합니다. 예를 들어, 개별 VM을 만드는 대신, 인스턴스 수를 지정하기만 하면 서비스가 필요한 리소스를 프로비전, 구성 및 관리합니다. Azure App Service는 PaaS 서비스의 예제입니다.
  
* **FaaS(서비스 제공 함수)**: 일반적으로 서버리스 컴퓨팅이라고 불리는 FaaS는 PaaS보다 호스팅 환경에 대한 관심을 추상화합니다. 계산 인스턴스를 만들고 해당 인스턴스에 코드를 배포하는 대신, 사용자가 코드를 배포하면 서비스가 코드를 자동으로 실행합니다. 계산 리소스를 관리할 필요가 없습니다. 플랫폼은 트래픽을 처리하는 데 필요한 수준까지 코드를 원활하게 확장하거나 축소할 수 있으며 코드가 실행 중일 때만 비용을 지불합니다. Azure Function은 FaaS 서비스입니다.

일반적으로 응용 프로그램이 FaaS 및 PaaS 모델을 선호할수록 클라우드에서 실행하면 더 많은 이점을 얻을 수 있습니다. 다음은 Azure 내에서 선택하는 일반적인 세 가지 호스팅 옵션의 요약 및 선택 기준입니다.

* [Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is): 웹 응용 프로그램 또는 서비스를 호스트하려는 경우 우선 App Service를 고려합니다. App Service 및 ASP.NET, WCF 및 ASP.NET Core 앱을 시작하려면 [Azure 에서 ASP.NET Core 웹 앱 만들기](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet)를 참조합니다.

* [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview): Azure Functions는 이벤트 구동 워크플로에 적합합니다. 웹 후크에 대한 응답, 큐 또는 BLOB 저장소의 항목 처리, 타이머 등의 예가 있습니다. Azure Functions를 사용하려면 [Visual Studio를 사용하여 첫 번째 함수 만들기](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)를 참조합니다.

* [Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/): App Service가 특정 종속성으로 인해 기존 응용 프로그램을 호스팅해야하는 필요성을 충족시키지 못하는 경우, 가상 머신이 가장 쉽게 시작할 수 있는 곳입니다. 가상 머신과 ASP.NET 또는 WCF를 시작하려면 [Azure 가상 머신에 ASP.NET 앱 배포](https://tutorials.visualstudio.com/aspnet-vm/intro)를 참조하십시오.

> [!TIP]
> Azure 서비스의 자세한 목록은 [Azure 계산 옵션 개요](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-overview#azure-compute-options)를 참조합니다. 서비스 선택에 대한 자세한 내용은 [Azure 계산 서비스에 대한 의사 결정 트리](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree)를 참조합니다.

## <a name="choosing-a-data-storage-service"></a>데이터 저장소 서비스 선택

Azure는 필요에 따라 데이터를 저장하기 위한 몇 가지 서비스를 제공합니다. .NET 개발자를 위한 가장 일반적인 데이터 서비스는 다음과 같습니다.

* [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/): 이미 SQL Server를 사용하는 응용 프로그램을 클라우드로 마이그레이션하려는 경우 Azure SQL 데이터베이스를 자연스럽게 시작할 수 있습니다. 시작하려면 [자습서: SQL Database를 사용하여 Azure에서 ASP.NET 앱 빌드](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase)를 참조합니다.

* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/): Azure Cosmos DB는 클라우드를 위해 설계된 최신 데이터베이스입니다. 아직 특정 데이터베이스 종속성이 없는 새 응용 프로그램을 시작할 때는 Azure Cosmos DB를 고려해 보세요. Cosmos DB는 자동 크기 조정, 예측 가능한 성능, 빠른 응답 시간, 스키마 제약 없는 데이터에 대한 쿼리 기능 등이 중요한 경우 새로운 웹, 모바일, 게임 및 IoT 응용 프로그램에 적합한 솔루션입니다. 시작하려면 [빠른 시작: SQL API 및 Azure Portal을 사용하여 Azure Cosmos DB가 있는 .NET 웹앱 빌드](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet)를 참조합니다.

* [Azure Blob Storage](https://docs.microsoft.com/azure/storage/): Azure Blob Storage는 이미지, 파일 및 스트림을 같은 큰 이진 개체를 저장하고 검색하는 데 최적화되었습니다. 개체 저장소를 사용하면 매우 많은 양의 구조화되지 않은 데이터를 관리할 수 있습니다. 시작하려면 [빠른 시작: .NET을 사용하여 개체 저장소에 blob 만들기](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-dotnet)를 참조합니다.

> [!TIP]
> 자세한 내용은 [올바른 데이터 저장소 선택](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview)을 참조하세요.

## <a name="connecting-to-azure-services"></a>Azure 서비스에 연결

Visual Studio를 사용한다면 프로젝트에 특정 Azure 서비스에 대한 지원을 추가할 수 있습니다.  Visual Studio의 **연결된 서비스** 대화에서 프로젝트에 필요한 참조, 연결 코드 및 구성 설정을 쉽게 추가하는 방법을 제공합니다.  다음과 같은 일부 자주 사용되는 Azure 서비스는 기본적으로 지원됩니다. [Storage](/azure/vs-azure-tools-connected-services-storage), [Azure Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) 인증, [Azure Key Vault](/azure/key-vault/vs-key-vault-add-connected-service) 및 [Computer Vision](/azure/cognitive-services/computer-vision/vs-computer-vision-connected-service)과 같은 [Cognitive Services](/azure/cognitive-services/)  타사 서비스를 비롯한 더 많은 서비스는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?term=connected%20service&target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Relevance)에서 확장으로 이용할 수 있습니다.

## <a name="diagnosing-problems-in-the-cloud"></a>클라우드에서 문제 진단
응용 프로그램을 Azure에 배포하면, 개발 중에 작동하지만 Azure에서는 실행되지 않는 경우가 있을 수 있습니다. 다음과 같은 문제 진단 시작에 적절한 두 지점이 있습니다.

* **Visual Studio에서 원격 디버그**: Azure 계산 서비스(이 문서에서 설명하는 서비스 포함)의 대부분은 Visual Studio로 원격 디버깅을 지원하고 로그를 수집합니다. 응용 프로그램에서 Visual Studio의 기능을 탐색하려면 Visual Studio의 빠른 실행 도구 모음(오른쪽 위 모서리에 있음)에 '클라우드 탐색기'를 입력하여 클라우드 탐색기 도구 창을 연 다음 트리에서 응용 프로그램을 찾습니다. 자세한 내용은 [Visual Studio를 사용하여 Azure App Service에서 웹앱 문제 해결](https://docs.microsoft.com/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug)을 참조합니다.

* **Application Insights**: [Application Insights](https://docs.microsoft.com/azure/application-insights/)는 응용 프로그램의 진단 데이터, 원격 분석 및 성능 데이터를 자동으로 캡처하는 완벽한 응용 프로그램 성능 모니터링(APM) 솔루션입니다. 앱에 대한 진단 데이터 수집을 시작 하려면 [ASP.NET 웹 응용 프로그램 모니터링 시작](https://docs.microsoft.com/azure/application-insights/quick-monitor-portal)을 참조합니다.

## <a name="next-steps"></a>다음 단계

* [Azure에 ASP.NET Core 첫 웹앱 배포](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet)
* [.NET 용 Azure API에서 인증하기에 대해 알아봅니다.](dotnet-sdk-azure-authenticate.md)
* [클라우드 앱에서 오류를 진단합니다.](https://blogs.msdn.microsoft.com/webdev/2018/02/07/diagnosing-errors-on-your-cloud-apps)
* [.NET 개발자용 Azure 빠른 시작 가이드](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook) 무료 전자책을 다운로드합니다.
