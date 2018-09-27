---
title: .NET용 Azure Service Bus 라이브러리
description: .NET용 Azure Service Bus 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: service-bus
ms.openlocfilehash: 506be9a669a2418f2437271d128a963e351442e7
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190876"
---
# <a name="azure-service-bus-libraries-for-net"></a><span data-ttu-id="047a8-103">.NET용 Azure Service Bus 라이브러리</span><span class="sxs-lookup"><span data-stu-id="047a8-103">Azure Service Bus libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="047a8-104">개요</span><span class="sxs-lookup"><span data-stu-id="047a8-104">Overview</span></span>

<span data-ttu-id="047a8-105">[Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)는 응용 프로그램 사이에서 각 응용 프로그램이 확장성 및 복구 기능 개선을 위해 메시지를 교환할 수 있게 해주는 메시징 인프라입니다.</span><span class="sxs-lookup"><span data-stu-id="047a8-105">[Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) is a messaging infrastructure that sits between applications allowing them to exchange messages for improved scale and resiliency.</span></span>

## <a name="client-library"></a><span data-ttu-id="047a8-106">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="047a8-106">Client library</span></span>

<span data-ttu-id="047a8-107">Visual Studio [패키지 관리자 콘솔][PackageManager]에서 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.ServiceBus)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="047a8-107">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.ServiceBus) directly from the Visual Studio [Package Manager console][PackageManager].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="047a8-108">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="047a8-108">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.ServiceBus
```

### <a name="code-example"></a><span data-ttu-id="047a8-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="047a8-109">Code Example</span></span>

<span data-ttu-id="047a8-110">이 예제에서는 Service Bus 큐로 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="047a8-110">This example sends a message to a Service Bus queue.</span></span>

```csharp
// using Microsoft.Azure.ServiceBus;
// Microsoft.Azure.ServiceBus 2.0.0 (stable)

byte[] messageBody = System.Text.Encoding.Unicode.GetBytes("Hello, world!");
ServiceBusConnectionStringBuilder builder = new ServiceBusConnectionStringBuilder(connectionString);
QueueClient client = new QueueClient(builder, ReceiveMode.PeekLock);
client.SendAsync(new Message(messageBody));
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="047a8-111">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="047a8-111">Explore the client APIs</span></span>](/dotnet/api/overview/azure/servicebus/client)


## <a name="management-library"></a><span data-ttu-id="047a8-112">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="047a8-112">Management library</span></span>

<span data-ttu-id="047a8-113">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="047a8-113">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ServiceBus.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="047a8-114">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="047a8-114">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ServiceBus.Fluent
```

#### <a name="net-core-cli"></a><span data-ttu-id="047a8-115">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="047a8-115">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.ServiceBus.Fluent
```

### <a name="code-example"></a><span data-ttu-id="047a8-116">코드 예제</span><span class="sxs-lookup"><span data-stu-id="047a8-116">Code Example</span></span>

<span data-ttu-id="047a8-117">이 예제는 최대 1024MB 크기인 Service Bus 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="047a8-117">This example creates a Service Bus queue with a maximum size of 1024 MB.</span></span>

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
> [<span data-ttu-id="047a8-118">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="047a8-118">Explore the management APIs</span></span>](/dotnet/api/overview/azure/servicebus/management)

## <a name="samples"></a><span data-ttu-id="047a8-119">샘플</span><span class="sxs-lookup"><span data-stu-id="047a8-119">Samples</span></span>

- [<span data-ttu-id="047a8-120">Service Bus 큐 기본 - .Net</span><span class="sxs-lookup"><span data-stu-id="047a8-120">Service Bus Queue Basics - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-basic-features/)
- [<span data-ttu-id="047a8-121">Service Bus 큐 고급 기능 - .Net</span><span class="sxs-lookup"><span data-stu-id="047a8-121">Service Bus Queue Advanced Features - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-queue-with-advanced-features/)
- [<span data-ttu-id="047a8-122">Service Bus 게시/구독 기본 - .Net</span><span class="sxs-lookup"><span data-stu-id="047a8-122">Service Bus Publish/Subscribe Basics - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-basic-features/)
- [<span data-ttu-id="047a8-123">Service Bus 게시/구독 고급 기능 - .Net</span><span class="sxs-lookup"><span data-stu-id="047a8-123">Service Bus Publish/Subscribe Advanced Features - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-publish-subscribe-with-advanced-features/)
- [<span data-ttu-id="047a8-124">클레임 기반 권한 부여를 포함하는 Service Bus - .Net</span><span class="sxs-lookup"><span data-stu-id="047a8-124">Service Bus with Claims-Based Authorization - .Net</span></span>](https://azure.microsoft.com/resources/samples/service-bus-dotnet-manage-with-claims-based-authorization/)

<span data-ttu-id="047a8-125">Azure Service Bus 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?term=service+bus)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="047a8-125">View the [complete list](https://azure.microsoft.com/resources/samples/?term=service+bus) of Azure Service Bus samples.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
