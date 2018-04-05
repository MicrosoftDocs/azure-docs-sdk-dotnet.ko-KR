---
title: Azure .NET API
description: .NET용 Azure API 개요
keywords: Azure, .NET, SDK, API, NuGet, 라이브러리, 패키지
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 26360a516220ca9d3e8901e60cb23ecbd02863cd
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2018
---
# <a name="azure-net-apis"></a>Azure .NET API

Azure .NET API를 사용하면 Azure 서비스를 사용하고 응용 프로그램 코드에서 Azure 리소스를 관리할 수 있습니다. API는 .NET 프로젝트에서 사용할 [NuGet 패키지](/dotnet/api/overview/azure/)로 사용할 수 있습니다. 

## <a name="manage-azure-resources"></a>Azure 리소스 관리

.NET용 Azure 라이브러리를 사용하면 .NET 응용 프로그램에서 Azure 리소스를 만들고 관리할 수 있습니다.

Azure 리소스를 관리하는 많은 패키지에는 사양에 맞게 리소스를 정확히 구성하는 [흐름](dotnet-sdk-azure-concepts.md) 인터페이스가 있습니다. 예를 들어 Linux VM을 만들려면 다음 코드를 작성합니다.

```csharp
var windowsVM = azure.VirtualMachines.Define(windowsVmName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithNewPrimaryNetwork("10.0.0.0/28")
    .WithPrimaryPrivateIPAddressDynamic()
    .WithNewPrimaryPublicIPAddress(publicIpDnsLabel)
    .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
    .WithAdminUsername(username)
    .WithAdminPassword(password)
    .WithSize(VirtualMachineSizeTypes.StandardD3V2)
    .Create();
 ```

[.NET 서비스 목록](/dotnet/api/overview/azure/)을 검토하여 프로젝트에서 라이브러리를 바로 사용합니다. 그런 다음 [시작 문서](dotnet-sdk-azure-get-started.md)을 참조하고, 인증을 설정하고, 자신의 Azure 구독에 대한 샘플 코드를 실행합니다.  [개념 문서](dotnet-sdk-azure-concepts.md)는 SDK에서 사용하는 규칙과 응용 프로그램 코드를 단순화하는 데 활용하는 방법에 대해 설명합니다. 새 기능, 주요 변경 내용 및 마이그레이션 지침은 [릴리스 정보](dotnet-sdk-azure-release-notes.md)에서 사용할 수 있습니다.

## <a name="consume-azure-services"></a>Azure 서비스 사용

.NET API를 사용하여 Azure 내에서 리소스를 만들고 프로그래밍 방식으로 관리하는 것 외에도 .NET API를 사용하여 응용 프로그램을 이러한 리소스에 연결하고 런타임에 사용할 수 있습니다.  예를 들어 SQL Database에 연결하거나 Azure Storage에 데이터를 저장할 수 있습니다.  [서비스 API의 전체 목록](/dotnet/api/overview/azure/)을 검색하여 특정 Azure 서비스에 사용할 NuGet 패키지를 식별할 수 있습니다.  

## <a name="samples"></a>샘플

다음 샘플에서는 .NET용 Azure 라이브러리를 사용하는 일반적인 자동화 작업에 대해 설명합니다.

- [가상 머신](dotnet-sdk-azure-virtual-machine-samples.md)
- [웹앱](dotnet-sdk-azure-web-apps-samples.md)
- [SQL Database](dotnet-sdk-azure-sql-database-samples.md)

통합된 [참조](/dotnet/api/overview/azure/?view=azure-dotnet)는 서비스 라이브러리와 관리 라이브러리 둘 다의 모든 패키지에서 사용할 수 있습니다. 새 기능, 주요 변경 내용 및 마이그레이션 지침은 [릴리스 정보](dotnet-sdk-azure-release-notes.md)에서 사용할 수 있습니다.

[!include[Contribute and community](includes/contribute.md)]