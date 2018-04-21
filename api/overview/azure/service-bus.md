---
title: .NET용 Azure Service Bus 라이브러리
description: .NET용 Azure Service Bus 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Service Bus
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: service-bus
ms.custom: devcenter, svc-overview
ms.openlocfilehash: f2795a123a7b92237b0aea672298ce9339fd0830
ms.sourcegitcommit: e1a0e91988bb849c75e9583a80e3e6d712083785
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2018
---
# <a name="azure-service-bus-libraries-for-net"></a>.NET용 Azure Service Bus 라이브러리

## <a name="overview"></a>개요

[Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)는 응용 프로그램 사이에서 각 응용 프로그램이 확장성 및 복구 기능 개선을 위해 메시지를 교환할 수 있게 해주는 메시징 인프라입니다.

## <a name="client-library"></a>클라이언트 라이브러리

Visual Studio [패키지 관리자 콘솔][PackageManager]에서 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.ServiceBus)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.ServiceBus
```

### <a name="code-example"></a>코드 예제

이 예제에서는 Service Bus 큐로 메시지를 보냅니다.

```csharp
// using Microsoft.Azure.ServiceBus;
// Microsoft.Azure.ServiceBus 2.0.0 (stable)

byte[] messageBody = System.Text.Encoding.Unicode.GetBytes("Hello, world!");
ServiceBusConnectionStringBuilder builder = new ServiceBusConnectionStringBuilder(connectionString);
QueueClient client = new QueueClient(builder, ReceiveMode.PeekLock);
client.SendAsync(new Message(messageBody));
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/servicebus/client)


## <a name="management-library"></a>관리 라이브러리

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.ServiceBus.Fluent
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Management.ServiceBus.Fluent
```

### <a name="code-example"></a>코드 예제

이 예제는 최대 1024MB 크기인 Service Bus 큐를 만듭니다.

```csharp
// using Microsoft.Azure.Management.ServiceBus.Fluent;
// using Microsoft.Azure.Management.ServiceBus.Fluent.Models;

using (ServiceBusManagementClient client = new ServiceBusManagementClient(credentials))
{
    client.SubscriptionId = subscriptionId;
    QueueInner parameters = new QueueInner
    {
        MaxSizeInMegabytes = 1024
    };
    await client.Queues.CreateOrUpdateAsync(resourceGroupName, namespaceName, queueName, parameters);
}
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/servicebus/management)

## <a name="samples"></a>샘플

- [Service Bus 큐 기본 - .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-basic-features/)
- [Service Bus 큐 고급 기능 - .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-advanced-features/)
- [Service Bus 게시/구독 기본 - .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-basic-features/)
- [Service Bus 게시/구독 고급 기능 - .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-advanced-features/)
- [클레임 기반 권한 부여를 포함하는 Service Bus - .Net](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-with-claims-based-authorization/)

Azure Service Bus 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?term=service+bus)을 봅니다.


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
