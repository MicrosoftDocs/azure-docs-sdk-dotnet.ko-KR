---
title: Azure에서 .NET을 사용하는 메시지 및 IoT에 대한 자습서 | Microsoft Docs
description: .NET 및 Azure 서비스를 사용하여 클라우드 응용 프로그램 간 및 디바이스와 클라우드 간에 메시지를 보냅니다.
ms.date: 10/19/2017
ms.openlocfilehash: 92cb78b34706a453630dbf36913d53400962ff25
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190776"
---
# <a name="net-tutorials-for-enterprise-messaging-and-internet-of-things-iot"></a><span data-ttu-id="c0e5f-103">엔터프라이즈 메시지 및 IoT(사물 인터넷)에 대한 .NET 자습서</span><span class="sxs-lookup"><span data-stu-id="c0e5f-103">.NET tutorials for enterprise messaging and Internet of Things (IoT)</span></span>

<span data-ttu-id="c0e5f-104">다음 테이블은 Azure 서비스를 사용하여 .NET 코드에서 응용 프로그램 및 디바이스 간에 메시지 보내기 및 읽기에 대한 자세한 자습서에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e5f-104">The following table links to in-depth tutorials for sending and reading messages between applications and devices in from your .NET code using Azure services.</span></span>

<span data-ttu-id="c0e5f-105">샘플 소스 코드는 [Azure 서비스 샘플](https://azure.microsoft.com/resources/samples/?platform=dotnet) 목록을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0e5f-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>


| | |
|---|---|
| <span data-ttu-id="c0e5f-106">**Service Bus**</span><span class="sxs-lookup"><span data-stu-id="c0e5f-106">**Service Bus**</span></span> | |
| <span data-ttu-id="c0e5f-107">[Service Bus 큐를 사용하는 방법][1]</span><span class="sxs-lookup"><span data-stu-id="c0e5f-107">[How to use Service Bus queues][1]</span></span> | <span data-ttu-id="c0e5f-108">큐를 만들고, 메시지를 보내고 받고, 큐를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e5f-108">Create queues, send and receive messages, and delete queues.</span></span> | 
| <span data-ttu-id="c0e5f-109">[Service Bus 토픽 및 구독을 사용하는 방법][2]</span><span class="sxs-lookup"><span data-stu-id="c0e5f-109">[How to use Service Bus topics and subscriptions][2]</span></span> | <span data-ttu-id="c0e5f-110">Service Bus를 통해 통신 모델 게시/구독을 사용하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c0e5f-110">Learn how to use publish/subscribe communication model with Service Bus.</span></span>
| <span data-ttu-id="c0e5f-111">[AMQP 1.0을 사용하여 .NET에서 Service Bus 사용][3]</span><span class="sxs-lookup"><span data-stu-id="c0e5f-111">[Using Service Bus from .NET with AMQP 1.0][3]</span></span> | <span data-ttu-id="c0e5f-112">Service Bus 애플리케이션에서 AMQP를 사용하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c0e5f-112">Learn how to use AMQP in you Service Bus applications.</span></span>
|<span data-ttu-id="c0e5f-113">**IoT Hub**</span><span class="sxs-lookup"><span data-stu-id="c0e5f-113">**IoT Hub**</span></span>|
| <span data-ttu-id="c0e5f-114">[IoT Hub에 시뮬레이션된 장치 연결][4]</span><span class="sxs-lookup"><span data-stu-id="c0e5f-114">[Connect a simulated device to your IoT Hub][4]</span></span> | <span data-ttu-id="c0e5f-115">디바이스 ID를 만들고, 메시지를 보내고, IoT Hub에서 원격 분석을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e5f-115">Create a device identity, send messages, and process telemetry from your IoT Hub.</span></span> |   
| <span data-ttu-id="c0e5f-116">[장치-클라우드 메시지 처리][5]</span><span class="sxs-lookup"><span data-stu-id="c0e5f-116">[Process device-to-cloud messages][5]</span></span> | <span data-ttu-id="c0e5f-117">시뮬레이션된 디바이스에서 메시지를 보내고 클라우드에서 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e5f-117">Send messages from a simulated device and process them in the cloud.</span></span> |
|<span data-ttu-id="c0e5f-118">**이벤트 허브**</span><span class="sxs-lookup"><span data-stu-id="c0e5f-118">**Event Hub**</span></span>|
| <span data-ttu-id="c0e5f-119">[이벤트 허브로 이벤트 보내기][6]</span><span class="sxs-lookup"><span data-stu-id="c0e5f-119">[Send events to an Event Hub][6]</span></span> | <span data-ttu-id="c0e5f-120">콘솔 애플리케이션에서 Event Hub로 이벤트를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c0e5f-120">Send events to Event hub from a console application.</span></span>
| <span data-ttu-id="c0e5f-121">[Event Hubs에서 이벤트 수신][7]</span><span class="sxs-lookup"><span data-stu-id="c0e5f-121">[Receive events from Event Hubs][7]</span></span> | <span data-ttu-id="c0e5f-122">메시지를 수신하고 동시에 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e5f-122">Receive messages and process them in parallel.</span></span>


[1]: /azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues
[2]: /azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions
[3]: /azure/service-bus-messaging/service-bus-amqp-dotnet
[4]: /azure/iot-hub/iot-hub-csharp-csharp-getstarted
[5]: /azure/iot-hub/iot-hub-csharp-csharp-process-d2c
[6]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-send
[7]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph


