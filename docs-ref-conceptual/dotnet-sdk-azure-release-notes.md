---
title: .NET용 Azure 관리 라이브러리 릴리스 정보 | Microsoft Docs
description: .NET용 Azure 관리 라이브러리에 대한 새 기능과 주요 변경 내용을 확인합니다.
ms.date: 10/19/2017
ms.openlocfilehash: dac9dee9c25fc349dedd50d6007f25c7d15b0928
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190676"
---
# <a name="release-notes"></a><span data-ttu-id="6ef49-103">릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="6ef49-103">Release Notes</span></span> 

## <a name="feature-availability-and-road-map-as-of-version-100"></a><span data-ttu-id="6ef49-104">1.0.0 버전 기준 기능 가용성 및 로드맵</span><span class="sxs-lookup"><span data-stu-id="6ef49-104">Feature Availability and Road Map as of Version 1.0.0</span></span> ##
### <a name="april-26-2017"></a><span data-ttu-id="6ef49-105">2017년 4월 26일</span><span class="sxs-lookup"><span data-stu-id="6ef49-105">April 26, 2017</span></span>

<table>
  <tr>
    <th align="left"><span data-ttu-id="6ef49-106">서비스 | 기능</span><span class="sxs-lookup"><span data-stu-id="6ef49-106">Service | feature</span></span></th>
    <th align="left"><span data-ttu-id="6ef49-107">GA로 사용 가능</span><span class="sxs-lookup"><span data-stu-id="6ef49-107">Available as GA</span></span></th>
    <th align="left"><span data-ttu-id="6ef49-108">미리 보기로 사용 가능</span><span class="sxs-lookup"><span data-stu-id="6ef49-108">Available as Preview</span></span></th>
    <th align="left"><span data-ttu-id="6ef49-109">서비스 예정</span><span class="sxs-lookup"><span data-stu-id="6ef49-109">Coming soon</span></span></th>
  </tr>
  <tr>
    <td><span data-ttu-id="6ef49-110">컴퓨팅</span><span class="sxs-lookup"><span data-stu-id="6ef49-110">Compute</span></span></td>
    <td><span data-ttu-id="6ef49-111">가상 머신 및 VM 확장</span><span class="sxs-lookup"><span data-stu-id="6ef49-111">Virtual machines and VM extensions</span></span><br><span data-ttu-id="6ef49-112">가상 머신 크기 집합</span><span class="sxs-lookup"><span data-stu-id="6ef49-112">Virtual machine scale sets</span></span><br><span data-ttu-id="6ef49-113">관리 디스크</span><span class="sxs-lookup"><span data-stu-id="6ef49-113">Managed disks</span></span></td>
    <td></td>
    <td valign="top"><span data-ttu-id="6ef49-114">Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="6ef49-114">Azure container services</span></span><br><span data-ttu-id="6ef49-115">Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="6ef49-115">Azure container registry</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="6ef49-116">Storage</span><span class="sxs-lookup"><span data-stu-id="6ef49-116">Storage</span></span></td>
    <td><span data-ttu-id="6ef49-117">Storage 계정</span><span class="sxs-lookup"><span data-stu-id="6ef49-117">Storage accounts</span></span></td>
    <td></td>
    <td><span data-ttu-id="6ef49-118">암호화</span><span class="sxs-lookup"><span data-stu-id="6ef49-118">Encryption</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="6ef49-119">SQL Database</span><span class="sxs-lookup"><span data-stu-id="6ef49-119">SQL Database</span></span></td>
    <td><span data-ttu-id="6ef49-120">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="6ef49-120">Databases</span></span><br><span data-ttu-id="6ef49-121">방화벽</span><span class="sxs-lookup"><span data-stu-id="6ef49-121">Firewalls</span></span><br><span data-ttu-id="6ef49-122">탄력적 풀</span><span class="sxs-lookup"><span data-stu-id="6ef49-122">Elastic pools</span></span></td>
    <td></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="6ef49-123">네트워킹</span><span class="sxs-lookup"><span data-stu-id="6ef49-123">Networking</span></span></td>
    <td><span data-ttu-id="6ef49-124">가상 네트워크</span><span class="sxs-lookup"><span data-stu-id="6ef49-124">Virtual networks</span></span><br><span data-ttu-id="6ef49-125">네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="6ef49-125">Network interfaces</span></span><br><span data-ttu-id="6ef49-126">IP 주소</span><span class="sxs-lookup"><span data-stu-id="6ef49-126">IP addresses</span></span><br><span data-ttu-id="6ef49-127">Routing Table</span><span class="sxs-lookup"><span data-stu-id="6ef49-127">Routing table</span></span><br><span data-ttu-id="6ef49-128">네트워크 보안 그룹</span><span class="sxs-lookup"><span data-stu-id="6ef49-128">Network security groups</span></span><br><span data-ttu-id="6ef49-129">DNS</span><span class="sxs-lookup"><span data-stu-id="6ef49-129">DNS</span></span><br><span data-ttu-id="6ef49-130">Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="6ef49-130">Traffic managers</span></span></td>
    <td valign="top"><span data-ttu-id="6ef49-131">부하 분산 장치</span><span class="sxs-lookup"><span data-stu-id="6ef49-131">Load balancers</span></span><br><span data-ttu-id="6ef49-132">애플리케이션 게이트웨이</span><span class="sxs-lookup"><span data-stu-id="6ef49-132">Application gateways</span></span></td>
    <td valign="top"></td>
  </tr>
  <tr>
    <td><span data-ttu-id="6ef49-133">더 많은 서비스</span><span class="sxs-lookup"><span data-stu-id="6ef49-133">More services</span></span></td>
    <td><span data-ttu-id="6ef49-134">리소스 관리자</span><span class="sxs-lookup"><span data-stu-id="6ef49-134">Resource Manager</span></span><br><span data-ttu-id="6ef49-135">Key Vault</span><span class="sxs-lookup"><span data-stu-id="6ef49-135">Key Vault</span></span><br><span data-ttu-id="6ef49-136">Redis</span><span class="sxs-lookup"><span data-stu-id="6ef49-136">Redis</span></span><br><span data-ttu-id="6ef49-137">CDN</span><span class="sxs-lookup"><span data-stu-id="6ef49-137">CDN</span></span><br><span data-ttu-id="6ef49-138">Batch</span><span class="sxs-lookup"><span data-stu-id="6ef49-138">Batch</span></span></td>
    <td valign="top"><span data-ttu-id="6ef49-139">App Service - Web Apps</span><span class="sxs-lookup"><span data-stu-id="6ef49-139">App service - Web apps</span></span><br><span data-ttu-id="6ef49-140">Functions</span><span class="sxs-lookup"><span data-stu-id="6ef49-140">Functions</span></span><br><span data-ttu-id="6ef49-141">Service Bus</span><span class="sxs-lookup"><span data-stu-id="6ef49-141">Service bus</span></span></td>
    <td valign="top"><span data-ttu-id="6ef49-142">모니터</span><span class="sxs-lookup"><span data-stu-id="6ef49-142">Monitor</span></span><br><span data-ttu-id="6ef49-143">Graph RBAC</span><span class="sxs-lookup"><span data-stu-id="6ef49-143">Graph RBAC</span></span><br><span data-ttu-id="6ef49-144">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6ef49-144">Azure Cosmos DB</span></span><br><span data-ttu-id="6ef49-145">Scheduler</span><span class="sxs-lookup"><span data-stu-id="6ef49-145">Scheduler</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="6ef49-146">기본 사항</span><span class="sxs-lookup"><span data-stu-id="6ef49-146">Fundamentals</span></span></td>
    <td><span data-ttu-id="6ef49-147">인증 - 코어</span><span class="sxs-lookup"><span data-stu-id="6ef49-147">Authentication - core</span></span></td>
    <td><span data-ttu-id="6ef49-148">비동기 메서드</span><span class="sxs-lookup"><span data-stu-id="6ef49-148">Async methods</span></span></td>
    <td valign="top"></td>
  </tr>
</table>

> [!WARNING] 
> <span data-ttu-id="6ef49-149">*미리 보기* 기능은 라이브러리의 문서 주석에 플래그가 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef49-149">*Preview* features are flagged in documentation comments in libraries.</span></span> <span data-ttu-id="6ef49-150">이러한 기능은 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef49-150">These features are subject to change.</span></span> <span data-ttu-id="6ef49-151">나중에 어떤 방식으로든 수정(또는 제거)될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ef49-151">They can be modified in any way (or even removed) in the future.</span></span>

[!include[Contribute and community](includes/contribute.md)]
