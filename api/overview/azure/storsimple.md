---
title: .NET용 Azure StorSimple 라이브러리
description: .NET용 Azure StorSimple 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, StorSimple
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/27/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: storsimple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: dcb6732bf1eded6852a3185546a09c96cfe84eca
ms.sourcegitcommit: 64c9e16e42894e8db8ed088487e55c5e0edd6861
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2017
ms.locfileid: "23639651"
---
# <a name="azure-storsimple-libraries-for-net"></a><span data-ttu-id="82cda-104">.NET용 Azure StorSimple 라이브러리</span><span class="sxs-lookup"><span data-stu-id="82cda-104">Azure StorSimple libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="82cda-105">개요</span><span class="sxs-lookup"><span data-stu-id="82cda-105">Overview</span></span>

<span data-ttu-id="82cda-106">Microsoft Azure StorSimple은 물리적 iSCSI 또는 SMB 인터페이스를 클라우드 기반 저장소에 제공하는 엔터프라이즈 저장소 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="82cda-106">Microsoft Azure StorSimple is an enterprise storage solution that provides physical iSCSI or SMB interfaces to cloud-based storage.</span></span> 

<span data-ttu-id="82cda-107">[Azure StorSimple](/azure/storsimple/)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="82cda-107">Learn more about [Azure StorSimple](/azure/storsimple/).</span></span>    

## <a name="management-library"></a><span data-ttu-id="82cda-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="82cda-108">Management library</span></span>

<span data-ttu-id="82cda-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="82cda-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="82cda-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="82cda-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.StorSimple.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.StorSimple.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="82cda-111">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="82cda-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a><span data-ttu-id="82cda-112">샘플</span><span class="sxs-lookup"><span data-stu-id="82cda-112">Samples</span></span>

<span data-ttu-id="82cda-113">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="82cda-113">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package