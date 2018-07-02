---
title: .NET용 Azure StorSimple 라이브러리
description: .NET용 Azure StorSimple 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, StorSimple
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/27/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: storsimple
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 818c48a0f45812841eb0e8c3928b59f6681892cf
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065903"
---
# <a name="azure-storsimple-libraries-for-net"></a>.NET용 Azure StorSimple 라이브러리

## <a name="overview"></a>개요

Microsoft Azure StorSimple은 물리적 iSCSI 또는 SMB 인터페이스를 클라우드 기반 저장소에 제공하는 엔터프라이즈 저장소 솔루션입니다. 

[Azure StorSimple](/azure/storsimple/)에 대해 자세히 알아봅니다.    

## <a name="management-library"></a>관리 라이브러리

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.StorSimple.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.StorSimple.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.StorSimple.Fluent
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/monitor/management)

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package