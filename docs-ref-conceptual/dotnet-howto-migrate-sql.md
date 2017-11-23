---
title: "Azure로 SQL Server 데이터베이스 마이그레이션"
description: "온-프레미스 SQL Server에서 Azure로 SQL Server 데이터베이스를 마이그레이션하는 방법에 대해 알아보세요."
keywords: "Azure .NET, ASP.NET, SQL, SQL Server, SQL Database, 마이그레이션, 마이그레이션"
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: sql-database
ms.custom: devcenter
ms.openlocfilehash: 967f034fcd2c2487f6a5709d243ce25fc9b6e85e
ms.sourcegitcommit: c360a22d5bff6eedd714b28b847d2f26b06665f4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2017
---
# <a name="migrate-a-sql-server-database-to-azure"></a><span data-ttu-id="ad647-104">Azure로 SQL Server 데이터베이스 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="ad647-104">Migrate a SQL Server database to Azure</span></span>

<span data-ttu-id="ad647-105">Azure에는 프로덕션 SQL Server 데이터베이스의 마이그레이션을 위한 두 가지 기본 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-105">Azure has two primary options for migrating a production SQL Server database:</span></span>

1. <span data-ttu-id="ad647-106">[Azure VM의 SQL Server](https://azure.microsoft.com/services/virtual-machines/sql-server/): Azure에서 실행되는 Windows Virtual Machine에 설치되고 호스팅되는 SQL Server 인스턴스로, IaaS(Infrastructure as a Service)라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-106">[SQL Server on Azure VMs](https://azure.microsoft.com/services/virtual-machines/sql-server/): A SQL Server instance installed and hosted on a Windows Virtual Machine running in Azure, also known as Infrastructure as a Service (IaaS).</span></span>
2. <span data-ttu-id="ad647-107">[Azure SQL Database](https://azure.microsoft.com/services/sql-database/): 완전히 관리되는 SQL 데이터베이스 Azure 서비스로, PaaS(Platform as a Service)라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-107">[Azure SQL Database](https://azure.microsoft.com/services/sql-database/): A fully managed SQL database Azure service, also known as Platform as a Service (PaaS).</span></span>

<span data-ttu-id="ad647-108">두 가지 모두 장단점이 있으며 마이그레이션하기 전에 평가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-108">Both come with pros and cons that you will need to evaluate before migrating.</span></span>

## <a name="choosing-iaas-or-paas"></a><span data-ttu-id="ad647-109">IaaS 또는 PaaS 선택</span><span class="sxs-lookup"><span data-stu-id="ad647-109">Choosing IaaS or PaaS</span></span>

<span data-ttu-id="ad647-110">먼저 IaaS 또는 PaaS 중 어떤 것이 더 적합한 지 판단해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-110">First, you should determine if IaaS or PaaS is more appropriate for you.</span></span>

<span data-ttu-id="ad647-111">**Azure VM의 SQL Server를 선택하는 경우:**</span><span class="sxs-lookup"><span data-stu-id="ad647-111">**You should choose SQL Server in Azure VMs if:**</span></span>

* <span data-ttu-id="ad647-112">최소한의 변경만으로 데이터베이스 및 응용 프로그램을 "리프트 앤 시프트"할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-112">You are looking to "lift and shift" your database and applications with minimal to no changes.</span></span>
* <span data-ttu-id="ad647-113">데이터베이스 서버와 이 서버가 실행되는 VM을 완전히 제어하려 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-113">You prefer having full control over your database server and the VM it runs on.</span></span>
* <span data-ttu-id="ad647-114">사용하려는 SQL Server 및 Windows Server 라이선스가 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-114">You already have SQL Server and Windows Server licenses that you intend to use.</span></span>

<span data-ttu-id="ad647-115">**Azure SQL Database를 선택하는 경우:**</span><span class="sxs-lookup"><span data-stu-id="ad647-115">**You should choose Azure SQL Database if:**</span></span>

* <span data-ttu-id="ad647-116">Azure에서 응용 프로그램을 현대화하고 다른 PaaS 서비스를 사용하기 위해 마이그레이션하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-116">You are looking to modernize your applications and are migrating to use other PaaS services in Azure.</span></span>
* <span data-ttu-id="ad647-117">데이터베이스 서버와 이 서버가 실행되는 VM을 관리하지 않으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-117">You do not wish to manage your database server and the VM it runs on.</span></span>
* <span data-ttu-id="ad647-118">SQL Server 또는 Windows Server 라이선스에 권한이 없거나 만료된 라이선스를 허용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-118">You do not have SQL Server or Windows Server licenses, or you intend to let licenses you have expire.</span></span>

<span data-ttu-id="ad647-119">다음 표에서는 일련의 시나리오를 기반으로 각 서비스 간의 차이점을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-119">The following table describes differences between each service based on a set of scenarios.</span></span>

| <span data-ttu-id="ad647-120">시나리오</span><span class="sxs-lookup"><span data-stu-id="ad647-120">Scenario</span></span> | <span data-ttu-id="ad647-121">Azure VM의 SQL Server</span><span class="sxs-lookup"><span data-stu-id="ad647-121">SQL Server in Azure VMs</span></span> | <span data-ttu-id="ad647-122">Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="ad647-122">Azure SQL Database</span></span> |
|----------|-------------------------|--------------------|
| <span data-ttu-id="ad647-123">마이그레이션</span><span class="sxs-lookup"><span data-stu-id="ad647-123">Migration</span></span> | <span data-ttu-id="ad647-124">데이터베이스를 최소한으로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-124">Requires minimal changes to your database.</span></span> | <span data-ttu-id="ad647-125">[Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595)에 의해 결정된 대로 Azure SQL에서 사용할 수 없는 기능을 사용하거나 로컬로 설치된 실행 파일처럼 다른 종속성이 있는 경우 데이터베이스를 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-125">May require changes to your database if you use features unavailable in Azure SQL, as determined by the [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595), or if you have other dependencies such as locally installed executables.</span></span>|
| <span data-ttu-id="ad647-126">가용성, 복구 및 업그레이드 관리</span><span class="sxs-lookup"><span data-stu-id="ad647-126">Managing availability, recovery, and upgrades</span></span> | <span data-ttu-id="ad647-127">가용성 및 복구는 수동으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-127">Availability and recovery is configured manually.</span></span> <span data-ttu-id="ad647-128">업그레이드는 [VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)를 사용하여 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-128">Upgrades can be automated with [VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade).</span></span> | <span data-ttu-id="ad647-129">자동으로 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-129">Automatically managed for you.</span></span> |
| <span data-ttu-id="ad647-130">기본 OS 구성</span><span class="sxs-lookup"><span data-stu-id="ad647-130">Underlying OS configuration</span></span> | <span data-ttu-id="ad647-131">수동 구성.</span><span class="sxs-lookup"><span data-stu-id="ad647-131">Manual configuration.</span></span> | <span data-ttu-id="ad647-132">자동으로 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-132">Automatically managed for you.</span></span> |
| <span data-ttu-id="ad647-133">데이터베이스 크기 관리</span><span class="sxs-lookup"><span data-stu-id="ad647-133">Managing database size</span></span> | <span data-ttu-id="ad647-134">SQL Server 인스턴스당 최대 64TB의 저장 용량을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-134">Supports up to 64TB of storage per SQL Server instance.</span></span> | <span data-ttu-id="ad647-135">수평 분할 전까지 4TB의 저장 용량을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-135">Supports 4TB of storage before needing a horizontal partition.</span></span> |
| <span data-ttu-id="ad647-136">비용 관리</span><span class="sxs-lookup"><span data-stu-id="ad647-136">Managing costs</span></span> | <span data-ttu-id="ad647-137">SQL Server 라이선스 비용, Windows Server 라이선스 비용 및 VM 비용(코어, RAM 및 저장소 기준)을 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-137">You must manage SQL Server license costs, Windows Server license costs, and VM costs (based on cores, RAM, and storage).</span></span> | <span data-ttu-id="ad647-138">서비스 비용을 관리해야 합니다(탄력적인 풀을 사용하는 경우 [eDTU 또는 DTU](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), 저장소 및 데이터베이스 수 기준).</span><span class="sxs-lookup"><span data-stu-id="ad647-138">You must manage service costs (based on [eDTUs or DTUs](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), storage, and number of databases if using an elastic pool).</span></span>  <span data-ttu-id="ad647-139">SLA의 비용도 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-139">You must also manage the cost of any SLA.</span></span> |

<span data-ttu-id="ad647-140">이 둘의 차이점에 대해 자세히 알아보려면 [ 클라우드 SQL Server 옵션 선택: Azure VM에서 Azure SQL Database 또는 SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad647-140">To learn more about the differences between the two, read [Choose a cloud SQL Server option: Azure SQL Database or SQL Server on Azure VMs](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).</span></span>

## <a name="get-started"></a><span data-ttu-id="ad647-141">시작</span><span class="sxs-lookup"><span data-stu-id="ad647-141">Get started</span></span>

<span data-ttu-id="ad647-142">다음 단계는 데이터베이스를 마이그레이션하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-142">The next step is to migrate your database.</span></span>  <span data-ttu-id="ad647-143">다음 가이드는 선택한 유형에 따라 유용한 마이그레이션 가이드입니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-143">The following guides are useful migration guides, depending on what you chose:</span></span>

* [<span data-ttu-id="ad647-144">Azure VM에서 SQL Server로 SQL Server 데이터베이스 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="ad647-144">Migrate a SQL Server database to SQL Server in an Azure VM</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [<span data-ttu-id="ad647-145">SQL Server 데이터베이스를 Azure SQL Database로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="ad647-145">Migrate your SQL Server database to Azure SQL Database</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

<span data-ttu-id="ad647-146">또한 다음 링크는 VM을 더 잘 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-146">Additionally, the following links will help you understand VMs better:</span></span>

* [<span data-ttu-id="ad647-147">Azure Virtual Machines의 SQL Server에 대한 고가용성 및 재해 복구</span><span class="sxs-lookup"><span data-stu-id="ad647-147">High availability and disaster recovery for SQL Server in Azure Virtual Machines</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [<span data-ttu-id="ad647-148">Azure Virtual Machines의 SQL Server에 대한 성능 모범 사례</span><span class="sxs-lookup"><span data-stu-id="ad647-148">Performance best practices for SQL Server in Azure Virtual Machines</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [<span data-ttu-id="ad647-149">Azure Virtual Machines의 SQL Server에 대한 응용 프로그램 패턴 및 개발 전략</span><span class="sxs-lookup"><span data-stu-id="ad647-149">Application Patterns and Development Strategies for SQL Server in Azure Virtual Machines</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

<span data-ttu-id="ad647-150">다음 링크는 Azure SQL Database를 더 잘 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-150">And the following links will help you understand Azure SQL Database better:</span></span>

* [<span data-ttu-id="ad647-151">Azure SQL Database 서버 및 데이터베이스 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="ad647-151">Create and manage Azure SQL Database servers and databases</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [<span data-ttu-id="ad647-152">DTU(데이터베이스 트랜잭션 단위) 및 eDTU(탄력적 데이터베이스 트랜잭션 단위)</span><span class="sxs-lookup"><span data-stu-id="ad647-152">Database Transaction Units (DTUs) and elastic Database Transaction Units (eDTUs)</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [<span data-ttu-id="ad647-153">Azure SQL Database 리소스 제한</span><span class="sxs-lookup"><span data-stu-id="ad647-153">Azure SQL Database resource limits</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="faq"></a><span data-ttu-id="ad647-154">FAQ</span><span class="sxs-lookup"><span data-stu-id="ad647-154">FAQ</span></span>

* <span data-ttu-id="ad647-155">**Azure VM 또는 Azure SQL Database에서 SQL Server와 함께 SQL Server Management Studio 및 SQL Server Reporting Services(SSRS)와 같은 도구를 계속 사용할 수 있습니까?**</span><span class="sxs-lookup"><span data-stu-id="ad647-155">**Can I still use tools such as SQL Server Management Studio and SQL Server Reporting Services (SSRS) with SQL Server in Azure VMs or Azure SQL Database?**</span></span>

    <span data-ttu-id="ad647-156">예!</span><span class="sxs-lookup"><span data-stu-id="ad647-156">Yes!</span></span> <span data-ttu-id="ad647-157">모든 Microsoft SQL 도구는 두 서비스 모두에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-157">All Microsoft SQL tooling works with both services.</span></span> <span data-ttu-id="ad647-158">SSRS는 Azure SQL Database의 일부가 아니기 때문에 Azure VM에서 실행한 다음 데이터베이스 인스턴스를 가리키도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-158">SSRS is not part of Azure SQL Database, though, and it's recommended that you run it in an Azure VM and then point it to your database instance.</span></span>
    
* <span data-ttu-id="ad647-159">**PaaS로 전환하고 싶지만 데이터베이스가 호환될지 확실하지 않습니다. 유용한 도구가 있습니까?**</span><span class="sxs-lookup"><span data-stu-id="ad647-159">**I want to go PaaS but I'm not sure if my database is compatible. Are there tools to help?**</span></span>

    <span data-ttu-id="ad647-160">예.</span><span class="sxs-lookup"><span data-stu-id="ad647-160">Yes.</span></span> <span data-ttu-id="ad647-161">[Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595)는 Azure SQL Database로 마이그레이션 시 사용되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-161">The [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595) is a tool that is used as a part of migrating to Azure SQL Database.</span></span>  <span data-ttu-id="ad647-162">[Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/)는 IaaS 또는 PaaS에 사용할 수 있는 미리 보기 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-162">The [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) is a preview service which you can use for either IaaS or PaaS.</span></span>

* <span data-ttu-id="ad647-163">**비용을 추정할 수 있습니까?**</span><span class="sxs-lookup"><span data-stu-id="ad647-163">**Can I estimate costs?**</span></span>

    <span data-ttu-id="ad647-164">예.</span><span class="sxs-lookup"><span data-stu-id="ad647-164">Yes.</span></span>  <span data-ttu-id="ad647-165">[Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/)는 VM 및 데이터베이스 서비스를 포함한 모든 Azure 서비스 비용을 계산하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad647-165">The [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/) can be used for estimating costs for all Azure services, including VMs and database services.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad647-166">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ad647-166">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ad647-167">올바른 Azure 호스팅 옵션 선택</span><span class="sxs-lookup"><span data-stu-id="ad647-167">Choose the right Azure hosting option</span></span>](dotnet-howto-choose-migration.md)