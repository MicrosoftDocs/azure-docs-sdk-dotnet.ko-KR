---
title: .NET용 Azure Event Grid 라이브러리
description: .NET용 Azure Event Grid 라이브러리에 대한 참조
ms.date: 04/16/2018
ms.topic: reference
ms.service: event-grid
ms.openlocfilehash: 5b19f8aa8b28b3e4aef528da051b6e7d177f1a2f
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190396"
---
# <a name="azure-event-grid-libraries-for-net"></a>.NET용 Azure Event Grid 라이브러리

Azure Event Grid에서 간단한 HTTP 기반 이벤트 처리를 사용하여 Azure 서비스 및 사용자 지정 원본의 이벤트에 대해 수신 대기하고 대응하는 이벤트 기반 응용 프로그램을 작성합니다.

Azure Event Grid에 대해 [자세히 알아보고](/azure/event-grid/overview), [Azure Blob 저장소 이벤트 자습서](/azure/storage/blobs/storage-blob-event-quickstart-powershell)를 시작합니다. 

## <a name="client-sdk"></a>Client SDK

Azure Event Grid Client SDK를 사용하여 이벤트를 만들고, 인증하고, 토픽에 게시합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.EventGrid
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.EventGrid 
```

### <a name="publish-events"></a>이벤트 게시

다음 코드는 Azure로 인증하고 사용자 지정 형식(이 예제에서는 `Contoso.Items.ItemsReceivedEvent`)의 `EventGridEvent` 이벤트 `List`를 토픽에 게시합니다. 샘플에 사용된 토픽 키와 엔드포인트 주소는 Azure PowerShell에서 검색이 가능합니다.

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

### <a name="consume-events"></a>이벤트 사용

이 코드 조각에는 Blob Storage와 같이 다른 Azure 서비스에서 트리거된 이벤트 뿐만 아니라 사용자 지정 이벤트 `Contoso.Items.ItemsReceived`을(를) 비롯한 이벤트가 사용됩니다.

```csharp
string response = string.Empty;
string requestContent = await req.Content.ReadAsStringAsync();

EventGridSubscriber eventGridSubscriber = new EventGridSubscriber();

// Optionally add one or more custom event type mappings
eventGridSubscriber.AddOrUpdateCustomEventMapping("Contoso.Items.ItemReceived", typeof(ContosoItemReceivedEventData));

var events = eventGridSubscriber.DeserializeEventGridEvents(requestContent);            
 
foreach (EventGridEvent receivedEvent in events)
{
    if (receivedEvent.Data is SubscriptionValidationEventData)
    {
        SubscriptionValidationEventData eventData = (SubscriptionValidationEventData)receivedEvent.Data;
        log.Info($"Got SubscriptionValidation event data, validationCode: {eventData.ValidationCode},  validationUrl: {eventData.ValidationUrl}, topic: {eventGridEvent.Topic}");
        // Handle subscription validation
    }
    else if (receivedEvent.Data is StorageBlobCreatedEventData)
    {
        StorageBlobCreatedEventData eventData = (StorageBlobCreatedEventData)receivedEvent.Data;
        log.Info($"Got BlobCreated event data, blob URI {eventData.Url}");
        // Handle StorageBlobCreatedEventData
    }
    else if (receivedEvent.Data is ContosoItemReceivedEventData)
    {
        ContosoItemReceivedEventData eventData = (ContosoItemReceivedEventData)receivedEvent.Data;
    }
}
```

> [!div class="nextstepaction"]
> [게시 API 탐색](/dotnet/api/overview/azure/eventgrid/publish)

## <a name="management-sdk"></a>관리 SDK

관리 SDK를 사용하여 Event Grid 인스턴스, 토픽 및 구독을 만들거나 업데이트하거나 삭제합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Network.Fluent)를 직접 설치합니다.


#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.EventGrid
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Management.EventGrid
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a>자세한 정보

- [Event Grid SDK를 사용하여 이벤트 수신](/azure/event-grid/receive-events)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
