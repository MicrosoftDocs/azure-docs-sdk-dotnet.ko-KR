---
title: .NET용 Azure IoT 라이브러리
description: .NET용 Azure IoT 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, IoT
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: iot-hub
ms.custom: devcenter, svc-overview
ms.openlocfilehash: af823e910acedd4f204034b12a31ba61fd53e090
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065273"
---
# <a name="azure-iot-libraries-for-net"></a><span data-ttu-id="a73f5-104">.NET용 Azure IoT 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a73f5-104">Azure IoT libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="a73f5-105">개요</span><span class="sxs-lookup"><span data-stu-id="a73f5-105">Overview</span></span>

<span data-ttu-id="a73f5-106">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/)는 수백만의 장치와 솔루션 백 엔드 간에서 안정적이고 안전한 양방향 통신이 가능하도록 완전히 관리되는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-106">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is a fully managed service that enables reliable and secure bi-directional communications between millions of devices and a solution back end.</span></span>

<span data-ttu-id="a73f5-107">IoT 솔루션에서 장치 및 데이터 원본은 단순한 네트워크 연결 센서부터 강력한 독립 실행형 컴퓨팅 장치에 이르기까지 다양할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-107">Devices and data sources in an IoT solution can range from a simple network-connected sensor to a powerful, standalone computing device.</span></span> <span data-ttu-id="a73f5-108">장치에 따라 처리 기능, 메모리, 통신 대역폭 및 통신 프로토콜 지원이 제한될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-108">Devices may have limited processing capability, memory, communication bandwidth, and communication protocol support.</span></span> <span data-ttu-id="a73f5-109">IoT [장치 SDK](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks)를 통해 다양한 장치 및 백 엔드 응용 프로그램에 대한 클라이언트 응용 프로그램을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-109">The IoT [device SDKs](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks) enable you to implement client applications for a wide variety of devices and back-end applications.</span></span>

<span data-ttu-id="a73f5-110">.NET용 장치 SDK는 Azure IoT Hub에 연결되고 .NET을 실행하는 장치의 구축을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-110">The device SDK for .NET facilitates building devices running .NET that connect to Azure IoT Hub.</span></span>

<span data-ttu-id="a73f5-111">.NET용 서비스 SDK는 클라우드에서 제어 장치를 관리 및 허용하고 .NET을 사용하는 백 엔드 응용 프로그램의 구축을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-111">The service SDK for .NET facilitates building back-end applications using .NET that manage and allow controlling devices from the Cloud.</span></span>

<span data-ttu-id="a73f5-112">[Azure IoT에 대한 자세한 정보](https://docs.microsoft.com/azure/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="a73f5-112">[Learn more about Azure IoT](https://docs.microsoft.com/azure/iot-hub/).</span></span>


## <a name="client-library"></a><span data-ttu-id="a73f5-113">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a73f5-113">Client library</span></span>

<span data-ttu-id="a73f5-114">.NET IoT 장치 클라이언트를 사용하여 IoT Hub에 연결하고 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-114">Use the .NET IoT devices client to connect and send messages to your IoT Hub.</span></span>

<span data-ttu-id="a73f5-115">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-115">Install the [NuGet package]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="a73f5-116">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="a73f5-116">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Devices.Client
```

```bash
dotnet add package Microsoft.Azure.Devices.Client
```
### <a name="code-examples"></a><span data-ttu-id="a73f5-117">코드 예제</span><span class="sxs-lookup"><span data-stu-id="a73f5-117">Code Examples</span></span> 

<span data-ttu-id="a73f5-118">이 예제에서는 IoT Hub에 연결하고 초당 하나의 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-118">This example connects to the IoT Hub and sends one message per second.</span></span>

```csharp
string deviceKey = "<deviceKey>";
string deviceId = "<deviceId>";
string iotHubHostName = "<IoTHubHostname>";
DeviceAuthenticationWithRegistrySymmetricKeyvar deviceAuthentication = new DeviceAuthenticationWithRegistrySymmetricKey(deviceId, deviceKey);

DeviceClient deviceClient = DeviceClient.Create(iotHubHostName, deviceAuthentication, TransportType.Mqtt);

while (true)
{
    double currentTemperature = 20 + Rand.NextDouble() * 15;
    double currentHumidity = 60 + Rand.NextDouble() * 20;

    var telemetryDataPoint = new
    {
        messageId = _messageId++,
        deviceId = deviceId,
        temperature = currentTemperature,
        humidity = currentHumidity
    };
    string messageString = JsonConvert.SerializeObject(telemetryDataPoint);
    Message message = new Message(Encoding.ASCII.GetBytes(messageString));
    message.Properties.Add("temperatureAlert", (currentTemperature > 30) ? "true" : "false");

    await deviceClient.SendEventAsync(message);
    Console.WriteLine("{0} > Sending message: {1}", DateTime.Now, messageString);

    await Task.Delay(1000);
}
```


> [!div class="nextstepaction"]
> [<span data-ttu-id="a73f5-119">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="a73f5-119">Explore the client APIs</span></span>](/dotnet/api/overview/azure/iot/client)

## <a name="samples"></a><span data-ttu-id="a73f5-120">샘플</span><span class="sxs-lookup"><span data-stu-id="a73f5-120">Samples</span></span>

- [<span data-ttu-id="a73f5-121">제네릭 웹 서비스 및 Event Hub 시나리오</span><span class="sxs-lookup"><span data-stu-id="a73f5-121">Generic Web Service to Event Hub scenario</span></span>](https://azure.microsoft.com/resources/samples/event-hubs-dotnet-importfromweb/)

<span data-ttu-id="a73f5-122">Azure IoT 업샘플(upsample)의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-122">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub) of Azure IoT Upsamples.</span></span>

<span data-ttu-id="a73f5-123">자세한 지침은 [Azure IoT Hub 개발자 가이드](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide)를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a73f5-123">View the [Azure IoT Hub developer guide](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide) for more guidance.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
