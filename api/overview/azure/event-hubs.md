---
title: .NET용 Azure Event Hubs 라이브러리
description: .NET용 Azure Event Hubs 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Event Hubs
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: event-hubs
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 5502ae24574c7883c34522ae18ca81bb516a33d2
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065313"
---
# <a name="azure-event-hubs-libraries-for-net"></a><span data-ttu-id="bed0b-104">.NET용 Azure Event Hubs 라이브러리</span><span class="sxs-lookup"><span data-stu-id="bed0b-104">Azure Event Hubs libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="bed0b-105">개요</span><span class="sxs-lookup"><span data-stu-id="bed0b-105">Overview</span></span>

<span data-ttu-id="bed0b-106">Azure Event Hubs는 확장성이 뛰어난 데이터 스트리밍 플랫폼이면서 이벤트 수집 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="bed0b-106">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service.</span></span>

<span data-ttu-id="bed0b-107">Azure Event Hubs에 대해 자세히 알아보려면 [Event Hubs란?](/azure/event-hubs/event-hubs-what-is-event-hubs) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bed0b-107">To learn more about Azure Event Hubs, read the article [What is Event Hubs?](/azure/event-hubs/event-hubs-what-is-event-hubs).</span></span>  <span data-ttu-id="bed0b-108">시작하려면 [Event Hubs 프로그래밍 가이드](/azure/event-hubs/event-hubs-programming-guide)를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="bed0b-108">To get started, check out the [Event Hubs Programming Guide](/azure/event-hubs/event-hubs-programming-guide).</span></span>

## <a name="client-library"></a><span data-ttu-id="bed0b-109">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="bed0b-109">Client library</span></span>

<span data-ttu-id="bed0b-110">Event Hubs 클라이언트를 사용하여 Event Hubs와 메시지를 주고 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bed0b-110">Use the Event Hubs client to send and receive messages to and from Event Hubs.</span></span>

<span data-ttu-id="bed0b-111">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.EventHubs)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="bed0b-111">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.EventHubs) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="bed0b-112">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="bed0b-112">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.EventHubs
```

```bash
dotnet add package Microsoft.Azure.EventHubs
```

### <a name="code-example"></a><span data-ttu-id="bed0b-113">코드 예제</span><span class="sxs-lookup"><span data-stu-id="bed0b-113">Code Example</span></span>

<span data-ttu-id="bed0b-114">다음 코드는 Event Hubs 클라이언트 만들고 허브로 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bed0b-114">The following code creates an Event Hubs client and sends a message to the hub.</span></span>

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
> [<span data-ttu-id="bed0b-115">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="bed0b-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/eventhub/client)

## <a name="management-library"></a><span data-ttu-id="bed0b-116">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="bed0b-116">Management library</span></span>

<span data-ttu-id="bed0b-117">Event Hubs 관리 라이브러리를 사용하여 허브 및 소비자 그룹을 만들고 업데이트하며 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="bed0b-117">Use the Event Hubs management library to create, update, and remove hubs and consumer groups.</span></span>

<span data-ttu-id="bed0b-118">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="bed0b-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.EventHub) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="bed0b-119">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="bed0b-119">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.EventHub
```

```bash
dotnet add package Microsoft.Azure.Management.EventHub
```

### <a name="code-example"></a><span data-ttu-id="bed0b-120">코드 예제</span><span class="sxs-lookup"><span data-stu-id="bed0b-120">Code Example</span></span>

<span data-ttu-id="bed0b-121">다음 코드에서는 새 이벤트 허브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bed0b-121">The following code creates a new event hub.</span></span>

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
> [<span data-ttu-id="bed0b-122">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="bed0b-122">Explore the management APIs</span></span>](/dotnet/api/overview/azure/eventhub/management)

## <a name="tutorials"></a><span data-ttu-id="bed0b-123">자습서</span><span class="sxs-lookup"><span data-stu-id="bed0b-123">Tutorials</span></span>

* [<span data-ttu-id="bed0b-124">.NET Framework를 사용하여 Azure Event Hubs로 이벤트 전송</span><span class="sxs-lookup"><span data-stu-id="bed0b-124">Send events to Azure Event Hubs using the .NET Framework</span></span>](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-send)

* [<span data-ttu-id="bed0b-125">.NET Framework를 사용하여 Azure Event Hubs에서 이벤트 수신</span><span class="sxs-lookup"><span data-stu-id="bed0b-125">Receive events from Azure Event Hubs using the .NET Framework</span></span>](/azure/event-hubs/event-hubs-dotnet-framework-getstarted-receive-eph)

## <a name="samples"></a><span data-ttu-id="bed0b-126">샘플</span><span class="sxs-lookup"><span data-stu-id="bed0b-126">Samples</span></span>

* [<span data-ttu-id="bed0b-127">Azure Event Hubs 샘플</span><span class="sxs-lookup"><span data-stu-id="bed0b-127">Azure Event Hubs Samples</span></span>](https://github.com/Azure/azure-event-hubs/tree/master/samples)

<span data-ttu-id="bed0b-128">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="bed0b-128">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
