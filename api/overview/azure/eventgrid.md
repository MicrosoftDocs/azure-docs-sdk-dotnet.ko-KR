---
title: .NET용 Azure Event Grid 라이브러리
description: .NET용 Azure Event Grid 라이브러리에 대한 참조
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 04/16/2018
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: aa25f76f041e890de512c67d9380903f81216f62
ms.sourcegitcommit: 9f54e3334fc35c1066d0c591ff85b16d46416aa8
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
---
# <a name="azure-event-grid-libraries-for-net"></a><span data-ttu-id="7044e-103">.NET용 Azure Event Grid 라이브러리</span><span class="sxs-lookup"><span data-stu-id="7044e-103">Azure Event Grid libraries for .NET</span></span>

<span data-ttu-id="7044e-104">Azure Event Grid에서 간단한 HTTP 기반 이벤트 처리를 사용하여 Azure 서비스 및 사용자 지정 원본의 이벤트에 대해 수신 대기하고 대응하는 이벤트 기반 응용 프로그램을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="7044e-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="7044e-105">Azure Event Grid에 대해 [자세히 알아보고](/azure/event-grid/overview), [Azure Blob 저장소 이벤트 자습서](/azure/storage/blobs/storage-blob-event-quickstart-powershell)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7044e-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart-powershell).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="7044e-106">SDK 게시</span><span class="sxs-lookup"><span data-stu-id="7044e-106">Publish SDK</span></span>

<span data-ttu-id="7044e-107">Azure Event Grid 게시 SDK를 사용하여 이벤트를 만들고, 인증하고, 토픽에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="7044e-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

<span data-ttu-id="7044e-108">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7044e-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="7044e-109">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="7044e-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.EventGrid
```

#### <a name="net-core-cli"></a><span data-ttu-id="7044e-110">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="7044e-110">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.EventGrid 
```

### <a name="sample-usage"></a><span data-ttu-id="7044e-111">샘플 사용</span><span class="sxs-lookup"><span data-stu-id="7044e-111">Sample usage</span></span>

<span data-ttu-id="7044e-112">다음 코드는 Azure로 인증하고 사용자 지정 형식(이 예제에서는 `Contoso.Items.ItemsReceivedEvent`)의 `EventGridEvent` 이벤트 `List`를 토픽에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="7044e-112">The following code authenticates with Azure and publishes a `List` of  `EventGridEvent` events of a custom type (in this example, `Contoso.Items.ItemsReceivedEvent` ) to a topic.</span></span> <span data-ttu-id="7044e-113">샘플에 사용된 토픽 키와 엔드포인트 주소는 Azure PowerShell에서 검색이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="7044e-113">The topic key and endpoint address used in the sample can be retrieved from Azure PowerShell:</span></span>

```powershell
$endpoint = (Get-AzureRmEventGridTopic -ResourceGroupName gridResourceGroup -Name <topic-name>).Endpoint
$keys = Get-AzureRmEventGridTopicKey -ResourceGroupName gridResourceGroup -Name <topic-name>
```

```csharp
string topicEndpoint = "https://<topic-name>.<region>-1.eventgrid.azure.net/api/events";
string topicKey = "<topic-key>";
string topicHostname = new Uri(topicEndpoint).Host;

TopicCredentials topicCredentials = new TopicCredentials(topicKey);
EventGridClient client = new EventGridClient(topicCredentials);

client.PublishEventsAsync(topicHostname, GetEventsList()).GetAwaiter().GetResult();
Console.Write("Published events to Event Grid.");

static IList<EventGridEvent> GetEventsList()
{
    List<EventGridEvent> eventsList = new List<EventGridEvent>();
    for (int i = 0; i < 1; i++)
    {
        eventsList.Add(new EventGridEvent()
        {
            Id = Guid.NewGuid().ToString(),
            EventType = "Contoso.Items.ItemReceivedEvent",
            Data = new ContosoItemReceivedEventData()
            {
                ItemUri = "ContosoSuperItemUri"
            },

            EventTime = DateTime.Now,
            Subject = "Door1",
            DataVersion = "2.0"
        });
    }
    return eventsList;
}
```

<span data-ttu-id="7044e-114">이 코드 조각은 [Azure Storage](/azure/storage/blobs/storage-blob-event-overview)에 새 Blob을 만들 때 게시된 이벤트를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="7044e-114">This snippet handles events published when creating a new blob in [Azure Storage](/azure/storage/blobs/storage-blob-event-overview).</span></span>

```csharp
string response = string.Empty;
const string SubscriptionValidationEvent = "Microsoft.EventGrid.SubscriptionValidationEvent";
const string StorageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

string requestContent = await req.Content.ReadAsStringAsync();
EventGridEvent[] eventGridEvents = JsonConvert.DeserializeObject<EventGridEvent[]>(requestContent);

foreach (EventGridEvent eventGridEvent in eventGridEvents)
{
    JObject dataObject = eventGridEvent.Data as JObject;

    // Deserialize the event data into the appropriate type based on event type 
    if (string.Equals(eventGridEvent.EventType, SubscriptionValidationEvent, StringComparison.OrdinalIgnoreCase))
    {
        var eventData = dataObject.ToObject<SubscriptionValidationEventData>();
        log.Info($"Got SubscriptionValidation event data, validation code: {eventData.ValidationCode}, topic: {eventGridEvent.Topic}");

        // Do any additional validation (as required) and then return back the below response
        var responseData = new SubscriptionValidationResponseData();
        responseData.ValidationResponse = eventData.ValidationCode;
        return req.CreateResponse(HttpStatusCode.OK, responseData);
    }

    else if (string.Equals(eventGridEvent.EventType, StorageBlobCreatedEvent, StringComparison.OrdinalIgnoreCase))
    {
        var eventData = dataObject.ToObject<StorageBlobCreatedEventData>();
        log.Info($"Got BlobCreated event data, blob URI {eventData.Url}");
    }
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="7044e-115">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="7044e-115">Explore the client APIs</span></span>](/dotnet/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="7044e-116">관리 SDK</span><span class="sxs-lookup"><span data-stu-id="7044e-116">Management SDK</span></span>

<span data-ttu-id="7044e-117">관리 SDK를 사용하여 Event Grid 인스턴스, 토픽 및 구독을 만들거나 업데이트하거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7044e-117">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

<span data-ttu-id="7044e-118">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7044e-118">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>


#### <a name="visual-studio-package-manager"></a><span data-ttu-id="7044e-119">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="7044e-119">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.EventGrid
```

#### <a name="net-core-cli"></a><span data-ttu-id="7044e-120">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="7044e-120">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.EventGrid
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="7044e-121">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="7044e-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="7044e-122">자세한 정보</span><span class="sxs-lookup"><span data-stu-id="7044e-122">Learn more</span></span>

- [<span data-ttu-id="7044e-123">Event Grid SDK를 사용하여 이벤트 수신</span><span class="sxs-lookup"><span data-stu-id="7044e-123">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
