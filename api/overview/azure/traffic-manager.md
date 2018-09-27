---
title: .NET용 Azure Traffic Manager 라이브러리
description: .NET용 Azure Traffic Manager 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: traffic-manager
ms.openlocfilehash: a75b5c566496f73475d24d62288a00c7d5775168
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190826"
---
# <a name="azure-traffic-manager-libraries-for-net"></a>.NET용 Azure Traffic Manager 라이브러리

## <a name="overview"></a>개요

Microsoft Azure Traffic Manager를 사용하면 다양한 데이터 센터에서 서비스 엔드포인트에 대한 사용자 트래픽의 배포를 제어할 수 있습니다. Traffic Manager에서 지원되는 서비스 엔드포인트는 Azure VM, Web Apps 및 클라우드 서비스를 포함합니다. 또한 외부, Azure가 아닌 엔드포인트로 Traffic Manager를 사용할 수 있습니다.

[Azure Traffic Manager](/azure/traffic-manager/traffic-manager-overview)에 대해 자세히 알아보세요.  

## <a name="management-library"></a>관리 라이브러리

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.TrafficManager.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.TrafficManager.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.TrafficManager.Fluent
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/trafficmanager/management)

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package