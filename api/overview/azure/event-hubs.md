---
title: .NET용 Azure Event Hubs 라이브러리
description: .NET용 Azure Event Hubs 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: event-hubs
ms.openlocfilehash: 74c533bef598b90369009d68a759d35d122a368d
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190276"
---
# <a name="azure-event-hubs-libraries-for-net"></a>.NET용 Azure Event Hubs 라이브러리

## <a name="overview"></a>개요

Azure Event Hubs는 확장성이 뛰어난 데이터 스트리밍 플랫폼이면서 이벤트 수집 서비스입니다.

Azure Event Hubs에 대해 자세히 알아보려면 [Event Hubs란?](/azure/event-hubs/event-hubs-what-is-event-hubs) 문서를 참조하세요.  시작하려면 [Event Hubs 프로그래밍 가이드](/azure/event-hubs/event-hubs-programming-guide)를 확인하세요.

## <a name="client-library"></a>클라이언트 라이브러리

Event Hubs 클라이언트를 사용하여 Event Hubs와 메시지를 주고 받습니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.EventHubs)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.EventHubs
```

```bash
dotnet add package Microsoft.Azure.EventHubs
```

### <a name="code-example"></a>코드 예제

다음 코드는 Event Hubs 클라이언트 만들고 허브로 메시지를 보냅니다.

```csharp
EventHubsConnectionStringBuilder connectionStringBuilder = new EventHubsConnectionStringBuilder(eventHubConnectionString)
{
    EntityPath = eventHubEntityPath
};

EventHubClient eventHubClient = EventHubClient.CreateFromConnectionString(connectionStringBuilder.ToString());
string message = $"Message {i}";
Console.WriteLine($"Sending message: {message}");
await eventHubClient.SendAsync(new EventData(Encoding.UTF8.GetBytes(message)));
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/eventhub/client)

## <a name="management-library"></a>관리 라이브러리

Event Hubs 관리 라이브러리를 사용하여 허브 및 소비자 그룹을 만들고 업데이트하며 제거합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.EventHub
```

```bash
dotnet add package Microsoft.Azure.Management.EventHub
```

### <a name="code-example"></a>코드 예제

다음 코드에서는 새 이벤트 허브를 만듭니다.

```csharp
TokenCredentials creds = new TokenCredentials(token);
EventHubManagementClient ehClient = new EventHubManagementClient(creds)
{
    SubscriptionId = subscriptionId
};

EventHubCreateOrUpdateParameters ehParams = new EventHubCreateOrUpdateParameters()
{
    Location = location
};

Console.WriteLine("Creating Event Hub...");
await ehClient.EventHubs.CreateOrUpdateAsync(resourceGroupName, namespaceName, EventHubName, ehParams);
Console.WriteLine("Created Event Hub successfully.");
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/eventhub/management)

## <a name="tutorials"></a>자습서

* [.NET Framework를 사용하여 Azure Event Hubs로 이벤트 전송](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-send)

* [.NET Framework를 사용하여 Azure Event Hubs에서 이벤트 수신](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-receive-eph)

## <a name="samples"></a>샘플

* [Azure Event Hubs 샘플](https://github.com/Azure/azure-event-hubs/tree/master/samples)

앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
