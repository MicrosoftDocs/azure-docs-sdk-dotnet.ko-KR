---
title: "Azure Virtual Machine으로 ASP.NET 웹 응용 프로그램 마이그레이션"
description: "ASP.NET 웹 응용 프로그램을 온-프레미스에서 Azure Virtual Machine으로 마이그레이션하는 방법에 대해 알아봅니다."
keywords: "Azure.NET, ASP.NET, VM, 가상 머신, 마이그레이션, 마이그레이션"
author: camsoper
manager: wpickett
ms.author: casoper
ms.date: 11/15/2017
ms.topic: article
ms.technology: azure
ms.devlang: dotnet
ms.service: virtual-machines
ms.custom: devcenter
ms.openlocfilehash: 718d91b98180a7584f78a2383d430c4700743306
ms.sourcegitcommit: c360a22d5bff6eedd714b28b847d2f26b06665f4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2017
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="73e8b-104">Azure Virtual Machine으로 ASP.NET 웹 응용 프로그램 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="73e8b-104">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="73e8b-105">이 문서에서는 ASP.NET 웹 응용 프로그램을 온-프레미스에서 Azure Virtual Machine으로 마이그레이션하는 방법에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-105">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="get-started"></a><span data-ttu-id="73e8b-106">시작</span><span class="sxs-lookup"><span data-stu-id="73e8b-106">Get Started</span></span>

<span data-ttu-id="73e8b-107">이 자습서에서는 가상 머신을 생성(또는 마이그레이션)하고 웹 응용 프로그램을 게시하고 Azure에서 응용 프로그램을 지원하는 데 필요한 기타 작업을 수행하는 단계를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-107">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="73e8b-108">다음 두 옵션 중 하나를 사용하여 Azure에서 ASP.NET 응용 프로그램용 가상 머신을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-108">Create a virtual machine for your ASP.NET application in Azure using one of the following two options:</span></span>
    - [<span data-ttu-id="73e8b-109">ASP.NET 응용 프로그램용 새 가상 머신 만들기</span><span class="sxs-lookup"><span data-stu-id="73e8b-109">Create a new virtual machine for ASP.NET Applications</span></span>](https://go.microsoft.com/fwlink/?linkid=863237)
    - [<span data-ttu-id="73e8b-110">기존 온-프레미스 가상 머신 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="73e8b-110">Migrate an existing on-premises virtual machine</span></span>](https://docs.microsoft.com/azure/site-recovery/tutorial-migrate-on-premises-to-azure)
- [<span data-ttu-id="73e8b-111">Visual Studio를 사용하여 앱 게시</span><span class="sxs-lookup"><span data-stu-id="73e8b-111">Publish your app using Visual Studio</span></span>](https://go.microsoft.com/fwlink/?linkid=863240)
- [<span data-ttu-id="73e8b-112">VM용 보안 가상 네트워크 만들기</span><span class="sxs-lookup"><span data-stu-id="73e8b-112">Create a secure virtual network for your VMs</span></span>](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [<span data-ttu-id="73e8b-113">응용 프로그램용 CI/CD 파이프라인 만들기</span><span class="sxs-lookup"><span data-stu-id="73e8b-113">Create a CI/CD pipeline for your application</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [<span data-ttu-id="73e8b-114">고가용성 및 확장성을 위해 VM 확장 집합으로 이동</span><span class="sxs-lookup"><span data-stu-id="73e8b-114">Move to a VM scale set for high availability and scalability</span></span>](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a><span data-ttu-id="73e8b-115">고려 사항</span><span class="sxs-lookup"><span data-stu-id="73e8b-115">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="73e8b-116">이점</span><span class="sxs-lookup"><span data-stu-id="73e8b-116">Benefits</span></span>

<span data-ttu-id="73e8b-117">가상 머신은 응용 프로그램을 온-프레미스에서 클라우드로 마이그레이션하는 가장 쉬운 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-117">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span>  <span data-ttu-id="73e8b-118">이를 통해 응용 프로그램이 온-프레미스를 사용하는 것과 동일한 환경을 복제할 수 있지만, 사용자의 데이터 센터를 관리할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-118">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span>  <span data-ttu-id="73e8b-119">Virtual Machine Scale Sets는 Virtual Machines에서 실행되는 응용 프로그램을 위해 고가용성 및 확장성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-119">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="73e8b-120">Virtual Machine 크기</span><span class="sxs-lookup"><span data-stu-id="73e8b-120">Virtual Machine Size</span></span>

<span data-ttu-id="73e8b-121">워크로드에 가장 최적화된 가상 머신 크기 및 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-121">Choose the virtual machine size and type that is best optimized for your workload.</span></span>  <span data-ttu-id="73e8b-122">자세한 내용은 [Azure에서 Windows 가상 머신에 대한 크기](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73e8b-122">See [sizes for Windows virtual machines in Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) for more information.</span></span>

### <a name="maintenance"></a><span data-ttu-id="73e8b-123">유지 관리</span><span class="sxs-lookup"><span data-stu-id="73e8b-123">Maintenance</span></span>

<span data-ttu-id="73e8b-124">온-프레미스 머신처럼 가상 머신<sup>&#42;</sup>을 유지 관리하고 업데이트할 책임이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-124">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span>  <span data-ttu-id="73e8b-125">[Azure App Service](https://docs.microsoft.com/azure/app-service/)와 같은 PaaS(Platform as a Service) 환경 또는 [컨테이너](https://docs.microsoft.com/azure/app-service/containers/)에서 응용 프로그램을 실행할 수 있는 경우, 그럴 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-125">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](https://docs.microsoft.com/azure/app-service/) or in a [container](https://docs.microsoft.com/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="73e8b-126">*<sup>&#42;</sup>[가상 머신 확장 집합을 위한 자동 OS 업그레이드](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)는 현재 미리 보기 서비스로서 사용할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="73e8b-126">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="73e8b-127">Virtual Network</span><span class="sxs-lookup"><span data-stu-id="73e8b-127">Virtual Networks</span></span>

<span data-ttu-id="73e8b-128">Azure Virtual Network를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-128">Azure Virtual Networks enable you to:</span></span>
- <span data-ttu-id="73e8b-129">제어하는 하이브리드 인프라 구축</span><span class="sxs-lookup"><span data-stu-id="73e8b-129">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="73e8b-130">자체 IP 주소 및 DNS 서버 가져오기</span><span class="sxs-lookup"><span data-stu-id="73e8b-130">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="73e8b-131">응용 프로그램에 대해 격리되고 매우 안전한 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="73e8b-131">Create an isolated and highly-secure environment for your applications</span></span>
- <span data-ttu-id="73e8b-132">몇 가지 [연결 옵션](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti) 방법 중 하나를 사용하여 온-프레미스 네트워크에 VM 연결</span><span class="sxs-lookup"><span data-stu-id="73e8b-132">Connect your VM to your on-premises network using one of several [connectivity options](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="73e8b-133">[ExpressRoute](https://azure.microsoft.com/services/expressroute/)를 사용하여 온-프레미스 네트워크에 가상 머신 통합</span><span class="sxs-lookup"><span data-stu-id="73e8b-133">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="73e8b-134">시작하려면 [Virtual Network 설명서](https://docs.microsoft.com/azure/virtual-network/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73e8b-134">To get started, see the [Virtual Network documentation](https://docs.microsoft.com/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="73e8b-135">Active Directory</span><span class="sxs-lookup"><span data-stu-id="73e8b-135">Active Directory</span></span>
<span data-ttu-id="73e8b-136">많은 응용 프로그램이 인증 및 ID 관리를 위해 Active Directory를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-136">Many applications use Active Directory for authentication and identity management.</span></span>  
- <span data-ttu-id="73e8b-137">Azure AD Connect는 온-프레미스 디렉터리와 Azure Active Directory를 통합하도록 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-137">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span>  <span data-ttu-id="73e8b-138">시작하려면 [Azure Active Directory와 온-프레미스 디렉터리 통합](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73e8b-138">To get started, see [Integrate your on-premises directories with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span></span>  
- <span data-ttu-id="73e8b-139">또는 [ExpressRoute](https://azure.microsoft.com/services/expressroute/)를 사용하면 응용 프로그램에서 온-프레미스 Active Directory에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-139">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="73e8b-140">SQL Database</span><span class="sxs-lookup"><span data-stu-id="73e8b-140">SQL Databases</span></span>

<span data-ttu-id="73e8b-141">응용 프로그램이 온-프레미스 데이터베이스를 사용하는 경우 앱은 기본적으로 이 데이터베이스와 통신할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-141">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="73e8b-142">다음 중 하나가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-142">You can either:</span></span>
- <span data-ttu-id="73e8b-143">응용 프로그램에서 온-프레미스를 실행하는 데이터베이스에 액세스할 수 있도록 해주는 하이브리드 네트워크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-143">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>  
- <span data-ttu-id="73e8b-144">Azure로 데이터베이스를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-144">Migrate your database to the Azure.</span></span>  <span data-ttu-id="73e8b-145">자세한 내용은 [Azure로 SQL Server 데이터베이스 마이그레이션](dotnet-howto-migrate-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73e8b-145">See [Migrate your SQL Server database to Azure](dotnet-howto-migrate-sql.md) for more information.</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="73e8b-146">고가용성 및 확장성 </span><span class="sxs-lookup"><span data-stu-id="73e8b-146">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="73e8b-147">가상 컴퓨터 확장 집합</span><span class="sxs-lookup"><span data-stu-id="73e8b-147">Virtual Machine Scale Sets</span></span>
<span data-ttu-id="73e8b-148">응용 프로그램의 가용성이 높은지 그리고 확장할 수 있는지 확인하고 VM 이미지를 Azure Virtual Machine Scale Set로 마이그레이션하여 응용 프로그램의 가용성과 확장성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-148">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span>  <span data-ttu-id="73e8b-149">VM Scale Sets는 이미 구성한 기존 VM을 사용하거나 응용 프로그램으로 이미지를 빌드하기 위해 빌드 파이프라인을 설정하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-149">VM Scale Sets provide the ability to use an existing VM you’ve already configured or set up a build pipeline to build an image with your application.</span></span>  

<span data-ttu-id="73e8b-150">시작하려면 [가상 머신 확장 집합에 응용 프로그램 배포](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73e8b-150">To get started, see [Deploy your application on virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="73e8b-151">중앙 집중식 로깅</span><span class="sxs-lookup"><span data-stu-id="73e8b-151">Centralized Logging</span></span>
<span data-ttu-id="73e8b-152">여러 인스턴스에서 응용 프로그램을 실행하는 경우 [Azure Storage](https://docs.microsoft.com/azure/storage/)와 같은 중앙 위치에 로그를 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="73e8b-152">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](https://docs.microsoft.com/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="73e8b-153">다음 단계</span><span class="sxs-lookup"><span data-stu-id="73e8b-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73e8b-154">Azure로 SQL Server 데이터베이스 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="73e8b-154">Migrate a SQL Server database to Azure</span></span>](dotnet-howto-migrate-sql.md)