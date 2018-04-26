---
title: .NET용 Azure Notification Hubs 라이브러리
description: .NET용 Azure Notification Hubs 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Notification Hubs
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: notification-hubs
ms.custom: devcenter, svc-overview
ms.openlocfilehash: f863bf9d5d63129e04dd31ba96b3e803bead87bc
ms.sourcegitcommit: 4c42de7e066b6aa0a5b5df02cce4d1d245aa558d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2018
---
# <a name="azure-notification-hubs-libraries-for-net"></a>.NET용 Azure Notification Hubs 라이브러리

Azure Notification Hubs는 사용하기 쉬운 다중 플랫폼의 확장된 푸시 엔진을 제공합니다. 단일 플랫폼 간 API 호출을 통해 클라우드 또는 온-프레미스 백 엔드에서 모든 모바일 플랫폼으로 개인 설정된 대상 푸시 알림을 쉽게 보낼 수 있습니다.

## <a name="client-library"></a>클라이언트 라이브러리

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs)를 직접 설치합니다.

> [!NOTE]
> [NuGet 패키지의 새 미리 보기 버전](https://www.nuget.org/packages/Microsoft.Azure.NotificationHubs/2.0.0-preview1)은 .NET Standard를 지원하며 Notifications Hubs의 백 엔드 용도로 .NET Core를 사용할 수 있습니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.NotificationHubs
```

### <a name="code-example"></a>코드 예제

이 예제에서는 알림 허브에 연결하고 Windows 푸시 알림 서비스(WNS) 메시지를 보냅니다.

```csharp
NotificationHubClient hub = NotificationHubClient
                                .CreateClientFromConnectionString("<connection string with full access>", "<hub name>");
string toast = @"<toast><visual><binding template=""ToastText01""><text id=""1"">Hello from a .NET App!</text></binding></visual></toast>";
await hub.SendWindowsNativeNotificationAsync(toast);
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/notificationhubs/client)


## <a name="management-library"></a>관리 라이브러리

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.NotificationHubs)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.NotificationHubs
```

```bash
dotnet add package Microsoft.Azure.Management.NotificationHubs
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/notificationhubs/management)

## <a name="samples"></a>샘플

- [Windows Universal 시작](https://github.com/Azure/azure-notificationhubs-samples/tree/master/dotnet/GetStartedWindowsUniversal)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
