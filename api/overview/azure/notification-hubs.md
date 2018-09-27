---
title: .NET용 Azure Notification Hubs 라이브러리
description: .NET용 Azure Notification Hubs 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: notification-hubs
ms.openlocfilehash: 197ca22527a475b43b45149a40e96e5a027739ad
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190266"
---
# <a name="azure-notification-hubs-libraries-for-net"></a><span data-ttu-id="cc08b-103">.NET용 Azure Notification Hubs 라이브러리</span><span class="sxs-lookup"><span data-stu-id="cc08b-103">Azure Notification Hubs libraries for .NET</span></span>

<span data-ttu-id="cc08b-104">Azure Notification Hubs는 사용하기 쉬운 다중 플랫폼의 확장된 푸시 엔진을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cc08b-104">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="cc08b-105">단일 플랫폼 간 API 호출을 통해 클라우드 또는 온-프레미스 백 엔드에서 모든 모바일 플랫폼으로 개인 설정된 대상 푸시 알림을 쉽게 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc08b-105">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

## <a name="client-library"></a><span data-ttu-id="cc08b-106">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="cc08b-106">Client library</span></span>

<span data-ttu-id="cc08b-107">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cc08b-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

> [!NOTE]
> <span data-ttu-id="cc08b-108">[NuGet 패키지의 새 미리 보기 버전](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1)은 .NET Standard를 지원하며 Notifications Hubs의 백 엔드 용도로 .NET Core를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc08b-108">A [new preview version of the NuGet package](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1) now supports .NET Standard, which allows using .NET core for backend use of Notifications Hubs</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="cc08b-109">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="cc08b-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a><span data-ttu-id="cc08b-110">코드 예제</span><span class="sxs-lookup"><span data-stu-id="cc08b-110">Code Example</span></span>

<span data-ttu-id="cc08b-111">이 예제에서는 알림 허브에 연결하고 Windows 푸시 알림 서비스(WNS) 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="cc08b-111">This example connects to a Notification Hub and sends a Windows Push Notification Service (WNS) message.</span></span>

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="cc08b-112">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="cc08b-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/client)


## <a name="management-library"></a><span data-ttu-id="cc08b-113">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="cc08b-113">Management library</span></span>

<span data-ttu-id="cc08b-114">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cc08b-114">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="cc08b-115">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="cc08b-115">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="cc08b-116">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="cc08b-116">Explore the management APIs</span></span>](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a><span data-ttu-id="cc08b-117">샘플</span><span class="sxs-lookup"><span data-stu-id="cc08b-117">Samples</span></span>

- [<span data-ttu-id="cc08b-118">Windows Universal 시작</span><span class="sxs-lookup"><span data-stu-id="cc08b-118">Getting Started with Windows Universal</span></span>](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
