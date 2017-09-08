---
title: "Azure에서 .NET을 사용하는 메시지 및 IoT에 대한 자습서 | Microsoft Docs"
description: ".NET 및 Azure 서비스를 사용하여 클라우드 응용 프로그램 간 및 장치와 클라우드 간에 메시지를 보냅니다."
author: camsoper
manager: douge
ms.assetid: 2ce6ea06-7b0b-45e6-8ca0-44e4e4030b82
ms.devlang: dotnet
ms.topic: article
ms.service: Azure
ms.technology: Azure
ms.date: 4/10/2017
ms.author: casoper
ms.openlocfilehash: 0c3e81231ac88b2418778b83ecabcbb553608e24
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="net-tutorials-for-enterprise-messaging-and-internet-of-things-iot"></a>엔터프라이즈 메시지 및 IoT(사물 인터넷)에 대한 .NET 자습서

다음 테이블은 Azure 서비스를 사용하여 .NET 코드에서 응용 프로그램 및 장치 간에 메시지 보내기 및 읽기에 대한 자세한 자습서에 연결합니다.

샘플 소스 코드는 [Azure 서비스 샘플](https://azure.microsoft.com/resources/samples/?platform=dotnet) 목록을 참조하세요.


| | |
|---|---|
| **Service Bus** | |
| [Service Bus 큐를 사용하는 방법][1] | 큐를 만들고, 메시지를 보내고 받고, 큐를 삭제합니다. | 
| [Service Bus 토픽 및 구독을 사용하는 방법][2] | Service Bus를 통해 통신 모델 게시/구독을 사용하는 방법을 알아봅니다.
| [AMQP 1.0을 사용하여 .NET에서 Service Bus 사용][3] | Service Bus 응용 프로그램에서 AMQP를 사용하는 방법을 알아봅니다.
|**IoT 허브**|
| [IoT Hub에 시뮬레이션된 장치 연결][4] | 장치 ID를 만들고, 메시지를 보내고, IoT Hub에서 원격 분석을 처리합니다. |   
| [장치-클라우드 메시지 처리][5] | 시뮬레이션된 장치에서 메시지를 보내고 클라우드에서 처리합니다. |
|**이벤트 허브**|
| [이벤트 허브로 이벤트 보내기][6] | 콘솔 응용 프로그램에서 이벤트 허브로 이벤트를 보냅니다.
| [Event Hubs에서 이벤트 수신][7] | 메시지를 수신하고 동시에 처리합니다.


[1]: /azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues
[2]: /azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions
[3]: /azure/service-bus-messaging/service-bus-amqp-dotnet
[4]: /azure/iot-hub/iot-hub-csharp-csharp-getstarted
[5]: /azure/iot-hub/iot-hub-csharp-csharp-process-d2c
[6]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-send
[7]: /azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph


