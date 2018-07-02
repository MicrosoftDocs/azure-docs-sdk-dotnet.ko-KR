---
title: .NET용 Azure Monitor 라이브러리
description: .NET용 Azure Monitor 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Monitor
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/27/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 7b86b752a354b5ab6f8482b81ecba3b08b8a9442
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065883"
---
# <a name="azure-monitor-libraries-for-net"></a><span data-ttu-id="9ea28-104">.NET용 Azure Monitor 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9ea28-104">Azure Monitor libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="9ea28-105">개요</span><span class="sxs-lookup"><span data-stu-id="9ea28-105">Overview</span></span>

<span data-ttu-id="9ea28-106">성능을 추적하고 보안을 유지하며 추세를 파악하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ea28-106">Azure Monitor helps you track performance, maintain security, and identify trends.</span></span>

<span data-ttu-id="9ea28-107">[Azure Monitor](/azure/monitoring-and-diagnostics/)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9ea28-107">Learn more about [Azure Monitor](/azure/monitoring-and-diagnostics/).</span></span>   

## <a name="management-library"></a><span data-ttu-id="9ea28-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9ea28-108">Management library</span></span>

<span data-ttu-id="9ea28-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Monitor.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="9ea28-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Monitor.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="9ea28-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="9ea28-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Monitor.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Monitor.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="9ea28-111">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="9ea28-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a><span data-ttu-id="9ea28-112">샘플</span><span class="sxs-lookup"><span data-stu-id="9ea28-112">Samples</span></span>

<span data-ttu-id="9ea28-113">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9ea28-113">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package