---
title: .NET용 Azure IoT 라이브러리
description: .NET용 Azure IoT 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: iot-hub
ms.openlocfilehash: 54182d8fabec0d3aee3ca3b58c7315bdf43cc24e
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190186"
---
# <a name="azure-iot-libraries-for-net"></a>.NET용 Azure IoT 라이브러리

## <a name="overview"></a>개요

[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/)는 수백만의 장치와 솔루션 백 엔드 간에서 안정적이고 안전한 양방향 통신이 가능하도록 완전히 관리되는 서비스입니다.

IoT 솔루션에서 디바이스 및 데이터 원본은 단순한 네트워크 연결 센서부터 강력한 독립 실행형 컴퓨팅 디바이스에 이르기까지 다양할 수 있습니다. 디바이스에 따라 처리 기능, 메모리, 통신 대역폭 및 통신 프로토콜 지원이 제한될 수 있습니다. IoT [디바이스 SDK](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks)를 통해 다양한 디바이스 및 백 엔드 응용 프로그램에 대한 클라이언트 응용 프로그램을 구현할 수 있습니다.

.NET용 디바이스 SDK는 Azure IoT Hub에 연결되고 .NET을 실행하는 디바이스의 구축을 지원합니다.

.NET용 서비스 SDK는 클라우드에서 제어 디바이스를 관리 및 허용하고 .NET을 사용하는 백 엔드 응용 프로그램의 구축을 지원합니다.

[Azure IoT에 대한 자세한 정보](https://docs.microsoft.com/azure/iot-hub/).


## <a name="client-library"></a>클라이언트 라이브러리

.NET IoT 디바이스 클라이언트를 사용하여 IoT Hub에 연결하고 메시지를 보냅니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지]( https://www.nuget.org/packages/Microsoft.Azure.Devices.Client)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Devices.Client
```

```bash
dotnet add package Microsoft.Azure.Devices.Client
```
### <a name="code-examples"></a>코드 예제 

이 예제에서는 IoT Hub에 연결하고 초당 하나의 메시지를 보냅니다.

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
> [클라이언트 API 탐색](/dotnet/api/overview/azure/iot/client)

## <a name="samples"></a>샘플

- [제네릭 웹 서비스 및 Event Hub 시나리오](https://azure.microsoft.com/resources/samples/event-hubs-dotnet-importfromweb/)

Azure IoT 업샘플(upsample)의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=iot-hub)을 봅니다.

자세한 지침은 [Azure IoT Hub 개발자 가이드](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide)를 확인합니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
