---
title: .NET용 Azure Data Lake Store 라이브러리
description: .NET용 Azure Data Lake Store 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: data-lake-store
ms.openlocfilehash: 8e55a21d84eae2ef4104c8253adec2cbc4b008e5
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190566"
---
# <a name="azure-data-lake-store-libraries-for-net"></a>.NET용 Azure Data Lake Store 라이브러리

## <a name="overview"></a>개요

Azure 데이터 레이크 저장소는 빅 데이터 분석 작업을 위한 엔터프라이즈 수준 하이퍼 스케일 리포지토리입니다. Azure 데이터 레이크를 사용하면 작동 및 예비 분석에 대해 한 곳에서 모든 크기, 형식 및 수집 속도의 데이터를 캡처할 수 있습니다.

자세히 알아보려면 [Azure Data Lake Store의 개요](/azure/data-lake-store/data-lake-store-overview)를 참조하세요.

## <a name="client-library"></a>클라이언트 라이브러리

클라이언트 라이브러리를 사용하여 Data Lake Store 계정에 폴더를 만들고, 파일을 업로드하며, 파일을 다운로드하는 등 Data Lake Store에서 파일 시스템 작업을 수행합니다.  .NET에서 Data Lake Store를 사용하는 방법에 대한 자세한 자습서는 [.NET SDK를 사용한 Azure Data Lake Store에서의 파일 시스템 작업](/azure/data-lake-store/data-lake-store-data-operations-net-sdk)을 참조하세요.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.DataLake.Store
```
### <a name="authentication"></a>인증

* 애플리케이션에 대한 최종 사용자 인증의 경우 [.NET SDK를 사용한 Data Lake Store의 최종 사용자 인증](/azure/data-lake-store/data-lake-store-end-user-authenticate-net-sdk)을 참조하세요.
* 애플리케이션에 대한 서비스 간 인증의 경우 [.NET SDK를 사용한 Data Lake Store의 서비스 간 인증](/azure/data-lake-store/data-lake-store-service-to-service-authenticate-net-sdk)을 참조하세요.

### <a name="code-example"></a>코드 예제

다음 코드 조각은 이는 서비스에 요청을 발급하는 데 사용되는 Data Lake Store 파일 시스템 클라이언트 개체를 만듭니다.

```csharp
// Create client objects
AdlsClient client = AdlsClient.CreateClient(_adlsAccountName, adlCreds);
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/datalakestore/client)


## <a name="management-library"></a>관리 라이브러리

관리 라이브러리를 사용하여 빅 데이터 리포지토리에 연결하고 관리합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.DataLake.Store)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.DataLake.Store
```

```bash
dotnet add package Microsoft.Azure.Management.DataLake.Store
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/datalakestore/management)


## <a name="samples"></a>샘플

* [Azure Data Lake .NET 클라이언트 예제](https://azure.microsoft.com/resources/samples/data-lake-dotnet-client/)

앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
