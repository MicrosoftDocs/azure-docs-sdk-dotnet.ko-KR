---
title: .NET용 Azure Application Insights 라이브러리
description: .NET용 Azure Application Insights 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: application-insights
ms.openlocfilehash: 10b65f536c6461959b0be9b8f9bd3ec56a307bea
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190842"
---
# <a name="azure-application-insights-libraries-for-net"></a>.NET용 Azure Application Insights 라이브러리

## <a name="overview"></a>개요

Application Insights는 웹 개발자를 위해 강력한 임시 분석 기능을 갖춘 확장 가능한 모니터링 및 진단 서비스입니다. Application Insights 네임스페이스의 클래스를 사용하여 원격 분석 수집을 구성하고, 모니터링하려는 애플리케이션에서 모든 사용자 지정 원격 분석을 보낼 수 있습니다.

## <a name="client-library"></a>클라이언트 라이브러리

.NET용 Application Insight Client SDK를 사용하면 나중의 분석을 위해 이벤트, 집계 데이터, 예외, 종속성 및 메트릭을 Azure에 로깅할 수 있습니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.ApplicationInsights )를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.ApplicationInsights 
```

```bash
dotnet add package Microsoft.ApplicationInsights 
```

### <a name="example"></a>예

이 예제에서는 사용자 지정 이벤트를 Application Insights로 추적합니다.

```csharp
TelemetryClient client = new TelemetryClient();
client.TrackEvent("MyCustomEvent");
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/insights/client)



## <a name="samples"></a>샘플

- [OpenSchema를 사용한 Application Insight Analytics(영문)](https://azure.microsoft.com/resources/samples/guidance-appinsights-openschema/)

Azure Application Insights 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?service=application-insights&platform=dotnet)을 봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
