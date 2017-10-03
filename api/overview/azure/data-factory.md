---
title: ".NET용 Azure Data Factory 라이브러리"
description: ".NET용 Azure Data Factory 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Data Factory
author: camsoper
ms.author: casoper
manager: douge
ms.date: 09/22/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: data-factory
ms.custom: devcenter
ms.openlocfilehash: 6f1a1cf9ac8189af59ff4e3f42dc1d8fb9620ea2
ms.sourcegitcommit: f35939d37f67485b3667739b02621e317db3e391
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2017
---
# <a name="azure-data-factory-libraries-for-net"></a>.NET용 Azure Data Factory 라이브러리

## <a name="overview"></a>개요

Azure Data Factory는 클라우드 기반 데이터 통합 서비스입니다. 이를 통해 클라우드에서 데이터 기반 워크플로를 만들어 데이터 이동 및 데이터 변환을 오케스트레이션하고 자동화할 수 있습니다.

자세히 알아보려면 [Azure Data Factory 소개](/azure/data-factory/data-factory-introduction)를 참조하세요.

## <a name="management-library---data-factory-v2-preview"></a>관리 라이브러리 - Data Factory V2(미리 보기)

관리 라이브러리를 사용하여 Data Factory V2(미리 보기)에서 데이터 기반 워크플로(파이프라인)를 만들고 예약합니다.  자세한 내용은 [.NET SDK를 사용하여 데이터 팩터리 및 파이프라인 만들기](/azure/data-factory/quickstart-create-data-factory-dot-net)를 참조하세요.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactory)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
# Get the most recent prerelease package
Install-Package Microsoft.Azure.Management.DataFactory -Prerelease
```

```bash
# Be sure to include the most recent version from the NuGet package page
dotnet add package Microsoft.Azure.Management.DataFactory --version 0.2.0-preview
```

### <a name="code-example"></a>코드 예제

다음 예제에서는 관리 라이브러리를 사용하여 데이터 팩터리를 만듭니다.

```csharp
/*
using Microsoft.Azure.Management.ResourceManager;
using Microsoft.Azure.Management.DataFactory;
using Microsoft.Azure.Management.DataFactory.Models;
*/

DataFactoryManagementClient client = new DataFactoryManagementClient(tokenCredentials) { SubscriptionId = subscriptionId };
Factory dataFactory = new Factory
{
    Location = region,
    Identity = new FactoryIdentity()
};
client.Factories.CreateOrUpdate(resourceGroup, dataFactoryName, dataFactory);
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/microsoft.azure.management.datafactory)

## <a name="management-library---data-factory-v1"></a>관리 라이브러리 - Data Factory V1

관리 라이브러리를 사용하여 Data Factory 버전 1에서 데이터 기반 워크플로(파이프라인)를 만들고 예약합니다.  자세한 내용은 [Data Factory 버전 1](/azure/data-factory/v1/data-factory-introduction)의 설명서를 검토하세요.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataFactories)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.DataFactories
```

```bash
dotnet add package Microsoft.Azure.Management.DataFactories
```

### <a name="code-example"></a>코드 예제

다음 예제에서는 관리 라이브러리를 사용하여 데이터 팩터리를 만듭니다.

```csharp
DataFactoryManagementClient client = new DataFactoryManagementClient(aadTokenCredentials, resourceManagerUri);
client.DataFactories.CreateOrUpdate(resourceGroupName,
    new DataFactoryCreateOrUpdateParameters()
    {
        DataFactory = new DataFactory()
        {
            Name = dataFactoryName,
            Location = "westus",
            Properties = new DataFactoryProperties()
        }
    }
);
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/datafactories/management)

## <a name="samples"></a>샘플

* [MyDriving - Azure IOT 및 모바일 응용 프로그램 예제](https://azure.microsoft.com/resources/samples/mydriving/): 데이터 팩터리를 사용하여 자세한 정보를 얻습니다.

앱에서 사용할 수 있는 [.NET 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)를 추가로 탐색합니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
