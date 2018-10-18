---
title: .NET용 Azure Monitor 라이브러리
description: .NET용 Azure Monitor 라이브러리에 대한 참조
ms.date: 10/27/2017
ms.topic: reference
ms.service: monitoring-alerts
ms.openlocfilehash: dbfeb845edf513cf2b4ce102ecdae7d008076641
ms.sourcegitcommit: 1cf4550df8ed3236d838f561f6177d14d89b5e44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348185"
---
# <a name="azure-monitor-libraries-for-net"></a>.NET용 Azure Monitor 라이브러리

## <a name="overview"></a>개요

성능을 추적하고 보안을 유지하며 추세를 파악하는 데 도움을 줍니다.

[Azure Monitor](/azure/monitoring-and-diagnostics/)에 대해 자세히 알아봅니다.   

## <a name="management-library"></a>관리 라이브러리

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Monitor.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Monitor.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.Monitor.Fluent
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package