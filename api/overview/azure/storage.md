---
title: "Azure .NET 저장소 API"
description: ".NET용 Azure Storage 라이브러리에 대한 참조"
keywords: "Azure, .NET, SDK, API, 저장소, Blob"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/17/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 4e494952b48bfbf3b10f9af9936648634353db78
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-storage-apis-for-net"></a>.NET용 Azure Storage API

## <a name="overview"></a>개요

[Azure Storage](https://review.docs.microsoft.com/en-us/azure/storage/storage-introduction)를 사용하여 .NET 응용 프로그램의 파일, Blob(개체) 데이터, 키-값 쌍 및 메시지를 읽고 씁니다.

Azure Storage를 시작하려면 [.NET을 사용하여 Azure Blob 저장소 시작](/azure/storage/storage-dotnet-how-to-use-blobs)을 참조하세요.

## <a name="client-library"></a>클라이언트 라이브러리

[연결 문자열](/azure/storage/storage-create-storage-account#manage-your-storage-account)을 사용하여 Azure Storage 계정에 연결한 다음, 클라이언트 라이브러리의 클래스와 메서드를 사용하여 Blob, 테이블, 파일 또는 큐 저장소를 사용합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/WindowsAzure.Storage)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package WindowsAzure.Storage
```

### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package WindowsAzure.Storage
```

### <a name="code-example"></a>코드 예제

이 예제에서는 기존 저장소 계정의 새 컨테이너에 새 Blob을 만듭니다.

```csharp
/* Include these "using" directives...
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Blob;
*/

string storageConnectionString = "DefaultEndpointsProtocol=https;"
    + "AccountName=[Storage Account Name]"
    + ";AccountKey=[Storage Account Key]"
    + ";EndpointSuffix=core.windows.net";

CloudStorageAccount account = CloudStorageAccount.Parse(storageConnectionString);
CloudBlobClient serviceClient = account.CreateCloudBlobClient();

// Create container. Name must be lower case.
Console.WriteLine("Creating container...");
var container = serviceClient.GetContainerReference("mycontainer");
container.CreateIfNotExistsAsync().Wait();

// write a blob to the container
CloudBlockBlob blob = container.GetBlockBlobReference("helloworld.txt");
blob.UploadTextAsync("Hello, World!").Wait();
```

> [!div class="nextstepactions"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/storage/client)

## <a name="management-apis"></a>관리 API

관리 API를 사용하여 Azure Storage 계정 및 연결 키를 만들고 관리합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Storage.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Storage.Fluent
```

#### <a name="net-core-cli"></a>.NET Core CLI

````bash
dotnet add package Microsoft.Azure.Management.Storage.Fluent
````

### <a name="code-example"></a>코드 예제

이 예제에서는 저장소 계정을 만듭니다.

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Management.Storage.Fluent
*/

IStorageAccount storage = azure.StorageAccounts.Define(storageAccountName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .Create();
```

> [!div class="nextstepactions"]
> [관리 API 탐색](/dotnet/api/overview/azure/storage/management)

## <a name="samples"></a>샘플

* [.NET에서 Azure Blob Storage 시작(영문)](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/) 
* [.NET에서 Azure Queue Storage 시작(영문)](https://azure.microsoft.com/resources/samples/storage-queue-dotnet-getting-started/)

Azure Storage 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=storage)을 봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package