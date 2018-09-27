---
title: .NET용 Azure Monitor 라이브러리
description: .NET용 Azure Monitor 라이브러리에 대한 참조
ms.date: 10/27/2017
ms.topic: reference
ms.service: multiple
ms.openlocfilehash: b81786590eb96a45da3ae08cecb8d11cf4c40bee
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190416"
---
# <a name="azure-monitor-libraries-for-net"></a><span data-ttu-id="f0ff0-103">.NET용 Azure Monitor 라이브러리</span><span class="sxs-lookup"><span data-stu-id="f0ff0-103">Azure Monitor libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="f0ff0-104">개요</span><span class="sxs-lookup"><span data-stu-id="f0ff0-104">Overview</span></span>

<span data-ttu-id="f0ff0-105">성능을 추적하고 보안을 유지하며 추세를 파악하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0ff0-105">Azure Monitor helps you track performance, maintain security, and identify trends.</span></span>

<span data-ttu-id="f0ff0-106">[Azure Monitor](/azure/monitoring-and-diagnostics/)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f0ff0-106">Learn more about [Azure Monitor](/azure/monitoring-and-diagnostics/).</span></span>   

## <a name="management-library"></a><span data-ttu-id="f0ff0-107">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="f0ff0-107">Management library</span></span>

<span data-ttu-id="f0ff0-108">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Monitor.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ff0-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Monitor.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="f0ff0-109">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="f0ff0-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Monitor.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Monitor.Fluent
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="f0ff0-110">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="f0ff0-110">Explore the management APIs</span></span>](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a><span data-ttu-id="f0ff0-111">샘플</span><span class="sxs-lookup"><span data-stu-id="f0ff0-111">Samples</span></span>

<span data-ttu-id="f0ff0-112">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f0ff0-112">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package