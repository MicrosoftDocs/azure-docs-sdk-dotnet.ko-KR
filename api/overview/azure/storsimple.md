---
title: .NET용 Azure StorSimple 라이브러리
description: .NET용 Azure StorSimple 라이브러리에 대한 참조
ms.date: 10/27/2017
ms.topic: reference
ms.service: storsimple
ms.openlocfilehash: ecaa1acb0d988f7312645c2e6ed8f3289e51237c
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190366"
---
# <a name="azure-storsimple-libraries-for-net"></a><span data-ttu-id="e41d1-103">.NET용 Azure StorSimple 라이브러리</span><span class="sxs-lookup"><span data-stu-id="e41d1-103">Azure StorSimple libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="e41d1-104">개요</span><span class="sxs-lookup"><span data-stu-id="e41d1-104">Overview</span></span>

<span data-ttu-id="e41d1-105">Microsoft Azure StorSimple은 물리적 iSCSI 또는 SMB 인터페이스를 클라우드 기반 저장소에 제공하는 엔터프라이즈 저장소 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="e41d1-105">Microsoft Azure StorSimple is an enterprise storage solution that provides physical iSCSI or SMB interfaces to cloud-based storage.</span></span> 

<span data-ttu-id="e41d1-106">[Azure StorSimple](/azure/storsimple/)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e41d1-106">Learn more about [Azure StorSimple](/azure/storsimple/).</span></span>    

## <a name="management-library"></a><span data-ttu-id="e41d1-107">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="e41d1-107">Management library</span></span>

<span data-ttu-id="e41d1-108">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e41d1-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="e41d1-109">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="e41d1-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.StorSimple.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.StorSimple.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="e41d1-110">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="e41d1-110">Explore the management APIs</span></span>](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a><span data-ttu-id="e41d1-111">샘플</span><span class="sxs-lookup"><span data-stu-id="e41d1-111">Samples</span></span>

<span data-ttu-id="e41d1-112">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e41d1-112">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package