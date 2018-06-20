---
title: Azure로 SQL Server 데이터베이스 마이그레이션
description: 온-프레미스 SQL Server에서 Azure로 SQL Server 데이터베이스를 마이그레이션하는 방법에 대해 알아보세요.
keywords: Azure .NET, ASP.NET, SQL, SQL Server, SQL Database, 마이그레이션, 마이그레이션
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: sql-database
ms.custom: devcenter
ms.openlocfilehash: d118d39e2168686c851f0daa6cb611f0a0c9d2fc
ms.sourcegitcommit: dbec35008347b581dd238b882354300e427bec70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2018
ms.locfileid: "29728494"
---
## <a name="migrate-a-sql-server-database-to-azure"></a>Azure로 SQL Server 데이터베이스 마이그레이션

이 짧은 아티클은 SQL Server 데이터베이스를 Azure로 마이그레이션하기 위한 두 가지 옵션의 간략한 개요를 제공합니다.

Azure에는 프로덕션 SQL Server 데이터베이스의 마이그레이션을 위한 두 가지 기본 옵션이 있습니다.

1. [Azure VM의 SQL Server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): Azure에서 실행되는 Windows Virtual Machine에 설치되고 호스팅되는 SQL Server 인스턴스로, IaaS(Infrastructure as a Service)라고도 합니다.
2. [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview): 완전히 관리되는 SQL 데이터베이스 Azure 서비스로, PaaS(Platform as a Service)라고도 합니다.

두 가지 모두 장단점이 있으며 마이그레이션하기 전에 평가해야 합니다.

## <a name="get-started"></a>시작하기

다음 마이그레이션 가이드는 사용하는 서비스에 따라 유용합니다.

* [Azure VM에서 SQL Server로 SQL Server 데이터베이스 마이그레이션](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [SQL Server 데이터베이스를 Azure SQL Database로 마이그레이션](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

또한 개념 콘텐츠에 대한 다음 링크는 VM을 더 잘 이해하는 데 도움이 됩니다.

* [Azure Virtual Machines의 SQL Server에 대한 고가용성 및 재해 복구](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Azure Virtual Machines의 SQL Server에 대한 성능 모범 사례](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Azure Virtual Machines의 SQL Server에 대한 응용 프로그램 패턴 및 개발 전략](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

다음 링크는 Azure SQL Database를 더 잘 이해하는 데 도움이 됩니다.

* [Azure SQL Database 서버 및 데이터베이스 만들기 및 관리](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [DTU(데이터베이스 트랜잭션 단위) 및 eDTU(탄력적 데이터베이스 트랜잭션 단위)](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [Azure SQL Database 리소스 제한](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a>IaaS 또는 PaaS 선택

데이터베이스를 마이그레이션할 위치를 평가할 때 IaaS 또는 PaaS 중 더 적절한 기능을 결정해야 합니다.

**Azure VM의 SQL Server를 선택하는 경우:**

* 최소한의 변경만으로 데이터베이스 및 응용 프로그램을 "리프트 앤 시프트"할 수 있습니다.
* 데이터베이스 서버와 이 서버가 실행되는 VM을 완전히 제어하려 합니다.
* 사용하려는 SQL Server 및 Windows Server 라이선스가 이미 있습니다.

**Azure SQL Database를 선택하는 경우:**

* Azure에서 응용 프로그램을 현대화하고 다른 PaaS 서비스를 사용하기 위해 마이그레이션하려고 합니다.
* 데이터베이스 서버와 이 서버가 실행되는 VM을 관리하지 않으려고 합니다.
* SQL Server 또는 Windows Server 라이선스에 권한이 없거나 만료된 라이선스를 허용하려고 합니다.

다음 표에서는 일련의 시나리오를 기반으로 각 서비스 간의 차이점을 설명합니다.

| 시나리오 | Azure VM의 SQL Server | Azure SQL Database |
|----------|-------------------------|--------------------|
| 마이그레이션 | 데이터베이스를 최소한으로 변경해야 합니다. | [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595)에 의해 결정된 대로 Azure SQL에서 사용할 수 없는 기능을 사용하거나 로컬로 설치된 실행 파일처럼 다른 종속성이 있는 경우 데이터베이스를 변경해야 할 수 있습니다.|
| 가용성, 복구 및 업그레이드 관리 | 가용성 및 복구는 수동으로 구성됩니다. 업그레이드는 [VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)를 사용하여 자동화할 수 있습니다. | 자동으로 관리합니다. |
| 기본 OS 구성 | 수동 구성. | 자동으로 관리합니다. |
| 데이터베이스 크기 관리 | SQL Server 인스턴스당 최대 64TB의 저장 용량을 지원합니다. | 수평 분할 전까지 4TB의 저장 용량을 지원합니다. |
| 비용 관리 | SQL Server 라이선스 비용, Windows Server 라이선스 비용 및 VM 비용(코어, RAM 및 저장소 기준)을 관리해야 합니다. | 서비스 비용을 관리해야 합니다(탄력적인 풀을 사용하는 경우 [eDTU 또는 DTU](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), 저장소 및 데이터베이스 수 기준).  SLA의 비용도 관리해야 합니다. |

이 둘의 차이점에 대해 자세히 알아보려면 클라우드 SQL Server 옵션 선택: [Azure VM에서 Azure SQL Database 또는 SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)를 참고하세요.

## <a name="faq"></a>FAQ

* **Azure VM 또는 Azure SQL Database에서 SQL Server와 함께 SQL Server Management Studio 및 SQL Server Reporting Services(SSRS)와 같은 도구를 계속 사용할 수 있습니까?**

    예! 모든 Microsoft SQL 도구는 두 서비스 모두에서 작동합니다. SSRS는 Azure SQL Database의 일부가 아니기 때문에 Azure VM에서 실행한 다음 데이터베이스 인스턴스를 가리키도록 하는 것이 좋습니다.
    
* **PaaS로 전환하고 싶지만 데이터베이스가 호환될지 확실하지 않습니다. 유용한 도구가 있습니까?**

    예. [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595)는 Azure SQL Database로 마이그레이션 시 사용되는 도구입니다.  [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/)는 IaaS 또는 PaaS에 사용할 수 있는 미리 보기 서비스입니다.

* **비용을 추정할 수 있습니까?**

    예.  [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/)는 VM 및 데이터베이스 서비스를 포함한 모든 Azure 서비스 비용을 계산하는 데 사용할 수 있습니다.
    
## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [올바른 Azure 호스팅 옵션 선택](dotnet-howto-choose-migration.md)
