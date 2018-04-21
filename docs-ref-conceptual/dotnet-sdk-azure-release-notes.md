---
title: .NET용 Azure 관리 라이브러리 릴리스 정보 | Microsoft Docs
description: .NET용 Azure 관리 라이브러리에 대한 새 기능과 주요 변경 내용을 확인합니다.
keywords: Azure, .NET, API, 참조, 정보, 업데이트, 사용 중단
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 48ff29507268f6b38acb24217801cf7b0227e444
ms.sourcegitcommit: e1a0e91988bb849c75e9583a80e3e6d712083785
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2018
---
# <a name="release-notes"></a><span data-ttu-id="053c6-104">릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="053c6-104">Release Notes</span></span> 

## <a name="feature-availability-and-road-map-as-of-version-100"></a><span data-ttu-id="053c6-105">1.0.0 버전 기준 기능 가용성 및 로드맵</span><span class="sxs-lookup"><span data-stu-id="053c6-105">Feature Availability and Road Map as of Version 1.0.0</span></span> ##
### <a name="april-26-2017"></a><span data-ttu-id="053c6-106">2017년 4월 26일</span><span class="sxs-lookup"><span data-stu-id="053c6-106">April 26, 2017</span></span>

<table>
  <tr>
    <th align="left"><span data-ttu-id="053c6-107">서비스 | 기능</span><span class="sxs-lookup"><span data-stu-id="053c6-107">Service | feature</span></span></th>
    <th align="left"><span data-ttu-id="053c6-108">GA로 사용 가능</span><span class="sxs-lookup"><span data-stu-id="053c6-108">Available as GA</span></span></th>
    <th align="left"><span data-ttu-id="053c6-109">미리 보기로 사용 가능</span><span class="sxs-lookup"><span data-stu-id="053c6-109">Available as Preview</span></span></th>
    <th align="left"><span data-ttu-id="053c6-110">서비스 예정</span><span class="sxs-lookup"><span data-stu-id="053c6-110">Coming soon</span></span></th>
  </tr>
  <tr>
    <td><span data-ttu-id="053c6-111">컴퓨팅</span><span class="sxs-lookup"><span data-stu-id="053c6-111">Compute</span></span></td>
    <td><span data-ttu-id="053c6-112">가상 머신 및 VM 확장</span><span class="sxs-lookup"><span data-stu-id="053c6-112">Virtual machines and VM extensions</span></span><br><span data-ttu-id="053c6-113">가상 머신 크기 집합</span><span class="sxs-lookup"><span data-stu-id="053c6-113">Virtual machine scale sets</span></span><br><span data-ttu-id="053c6-114">관리 디스크</span><span class="sxs-lookup"><span data-stu-id="053c6-114">Managed disks</span></span></td>
    <td></td>
    <td valign="top"><span data-ttu-id="053c6-115">Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="053c6-115">Azure container services</span></span><br><span data-ttu-id="053c6-116">Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="053c6-116">Azure container registry</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="053c6-117">Storage</span><span class="sxs-lookup"><span data-stu-id="053c6-117">Storage</span></span></td>
    <td><span data-ttu-id="053c6-118">Storage 계정</span><span class="sxs-lookup"><span data-stu-id="053c6-118">Storage accounts</span></span></td>
    <td></td>
    <td><span data-ttu-id="053c6-119">암호화</span><span class="sxs-lookup"><span data-stu-id="053c6-119">Encryption</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="053c6-120">SQL Database</span><span class="sxs-lookup"><span data-stu-id="053c6-120">SQL Database</span></span></td>
    <td><span data-ttu-id="053c6-121">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="053c6-121">Databases</span></span><br><span data-ttu-id="053c6-122">방화벽</span><span class="sxs-lookup"><span data-stu-id="053c6-122">Firewalls</span></span><br><span data-ttu-id="053c6-123">탄력적 풀</span><span class="sxs-lookup"><span data-stu-id="053c6-123">Elastic pools</span></span></td>
    <td></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="053c6-124">네트워킹</span><span class="sxs-lookup"><span data-stu-id="053c6-124">Networking</span></span></td>
    <td><span data-ttu-id="053c6-125">가상 네트워크</span><span class="sxs-lookup"><span data-stu-id="053c6-125">Virtual networks</span></span><br><span data-ttu-id="053c6-126">네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="053c6-126">Network interfaces</span></span><br><span data-ttu-id="053c6-127">IP 주소</span><span class="sxs-lookup"><span data-stu-id="053c6-127">IP addresses</span></span><br><span data-ttu-id="053c6-128">Routing Table</span><span class="sxs-lookup"><span data-stu-id="053c6-128">Routing table</span></span><br><span data-ttu-id="053c6-129">네트워크 보안 그룹</span><span class="sxs-lookup"><span data-stu-id="053c6-129">Network security groups</span></span><br><span data-ttu-id="053c6-130">DNS</span><span class="sxs-lookup"><span data-stu-id="053c6-130">DNS</span></span><br><span data-ttu-id="053c6-131">Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="053c6-131">Traffic managers</span></span></td>
    <td valign="top"><span data-ttu-id="053c6-132">부하 분산 장치</span><span class="sxs-lookup"><span data-stu-id="053c6-132">Load balancers</span></span><br><span data-ttu-id="053c6-133">응용 프로그램 게이트웨이</span><span class="sxs-lookup"><span data-stu-id="053c6-133">Application gateways</span></span></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="053c6-134">더 많은 서비스</span><span class="sxs-lookup"><span data-stu-id="053c6-134">More services</span></span></td>
    <td><span data-ttu-id="053c6-135">리소스 관리자</span><span class="sxs-lookup"><span data-stu-id="053c6-135">Resource Manager</span></span><br><span data-ttu-id="053c6-136">Key Vault</span><span class="sxs-lookup"><span data-stu-id="053c6-136">Key Vault</span></span><br><span data-ttu-id="053c6-137">Redis</span><span class="sxs-lookup"><span data-stu-id="053c6-137">Redis</span></span><br><span data-ttu-id="053c6-138">CDN</span><span class="sxs-lookup"><span data-stu-id="053c6-138">CDN</span></span><br><span data-ttu-id="053c6-139">Batch</span><span class="sxs-lookup"><span data-stu-id="053c6-139">Batch</span></span></td>
    <td valign="top"><span data-ttu-id="053c6-140">App Service - Web Apps</span><span class="sxs-lookup"><span data-stu-id="053c6-140">App service - Web apps</span></span><br><span data-ttu-id="053c6-141">Functions</span><span class="sxs-lookup"><span data-stu-id="053c6-141">Functions</span></span><br><span data-ttu-id="053c6-142">Service Bus</span><span class="sxs-lookup"><span data-stu-id="053c6-142">Service bus</span></span></td>
    <td valign="top"><span data-ttu-id="053c6-143">모니터</span><span class="sxs-lookup"><span data-stu-id="053c6-143">Monitor</span></span><br><span data-ttu-id="053c6-144">Graph RBAC</span><span class="sxs-lookup"><span data-stu-id="053c6-144">Graph RBAC</span></span><br><span data-ttu-id="053c6-145">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="053c6-145">Azure Cosmos DB</span></span><br><span data-ttu-id="053c6-146">Scheduler</span><span class="sxs-lookup"><span data-stu-id="053c6-146">Scheduler</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="053c6-147">기본 사항</span><span class="sxs-lookup"><span data-stu-id="053c6-147">Fundamentals</span></span></td>
    <td><span data-ttu-id="053c6-148">인증 - 코어</span><span class="sxs-lookup"><span data-stu-id="053c6-148">Authentication - core</span></span></td>
    <td><span data-ttu-id="053c6-149">비동기 메서드</span><span class="sxs-lookup"><span data-stu-id="053c6-149">Async methods</span></span></td>
    <td valign="top"></td>
  </tr>
</table>

> [!WARNING] 
> <span data-ttu-id="053c6-150">*미리 보기* 기능은 라이브러리의 문서 주석에 플래그가 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="053c6-150">*Preview* features are flagged in documentation comments in libraries.</span></span> <span data-ttu-id="053c6-151">이러한 기능은 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="053c6-151">These features are subject to change.</span></span> <span data-ttu-id="053c6-152">나중에 어떤 방식으로든 수정(또는 제거)될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="053c6-152">They can be modified in any way (or even removed) in the future.</span></span>

[!include[Contribute and community](includes/contribute.md)]
