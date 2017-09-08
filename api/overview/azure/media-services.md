---
title: ".NET용 Azure Media Services 라이브러리"
description: ".NET용 Azure Media Services 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Media Services
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/21/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: ee852258819e75867888f4a5fa1cbd72c7f91685
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-media-services-libraries-for-net"></a>.NET용 Azure Media Services 라이브러리

## <a name="overview"></a>개요

Microsoft Azure Media Services는 개발자가 확장 가능한 미디어 관리 및 배달 응용 프로그램을 빌드할 수 있는 확장 가능한 클라우드 기반 플랫폼입니다. Media Services는 다양한 클라이언트(예: TV, PC 및 모바일 장치)로의 주문형 및 라이브 스트리밍 배달을 위해 비디오 또는 오디오 콘텐츠를 안전하게 업로드, 저장, 인코딩 및 패키지할 수 있는 REST API를 기반으로 합니다. 

자세한 내용은 [개요](/azure/media-services/media-services-overview) 및 [.NET 시작](/azure/media-services/media-services-dotnet-how-to-use)을 참조하세요. 

## <a name="client-library"></a>클라이언트 라이브러리

Azure Media Services .NET SDK 라이브러리를 사용하면 .NET을 사용하여 Media Services를 프로그래밍할 수 있습니다. Azure Media Services 클라이언트 라이브러리를 사용하여 Media Services API에 대해 연결, 인증 및 개발을 수행합니다.  

자세한 내용은 [.NET SDK를 사용한 주문형 콘텐츠 배달 시작](/azure/media-services/media-services-dotnet-get-started)을 참조하세요.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/windowsazure.mediaservices)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package windowsazure.mediaservices
```

### <a name="code-example"></a>코드 예제

다음 코드 예제에서는 미디어 서비스 .NET SDK를 사용하여 다음 작업을 수행합니다.

- 인코딩 작업을 만듭니다.
- 미디어 인코더 표준 인코더에 대한 참조를 가져옵니다.
- 적응 스트리밍 사전 설정을 사용하도록 지정합니다.
- 작업에 단일 인코딩을 추가합니다.
- 인코딩할 입력 자산을 지정합니다.
- 인코딩된 자산을 수신하는 출력 자산을 만듭니다.
- 작업을 제출합니다.


```csharp
/* Include this 'using' directive:
using Microsoft.WindowsAzure.MediaServices.Client;
*/

CloudMediaContext context = new CloudMediaContext(new Uri(mediaServiceRESTAPIEndpoint), tokenProvider);

// Get an uploaded asset.
IAsset asset = context.Assets.FirstOrDefault();

// Encode and generate the output using the "Adaptive Streaming" preset.
// Declare a new job.
IJob job = context.Jobs.Create("Media Encoder Standard Job");
// Get a media processor reference, and pass to it the name of the 
// processor to use for the specific task.
IMediaProcessor processor = context.MediaProcessors.Where(p => p.Name == mediaProcessorName)
    .ToList().OrderBy(p => new Version(p.Version)).LastOrDefault();
if (processor == null) 
{
    throw new ArgumentException(string.Format("Unknown media processor", mediaProcessorName));
}

// Create a task with the encoding details, using a string preset.
// In this case "Adaptive Streaming" preset is used.
ITask task = job.Tasks.AddNew("My encoding task", processor, "Adaptive Streaming", TaskOptions.None);

// Specify the input asset to be encoded.
task.InputAssets.Add(asset);
// Add an output asset to contain the results of the job. 
// This output is specified as AssetCreationOptions.None, which 
// means the output asset is not encrypted. 
task.OutputAssets.AddNew("Output asset", AssetCreationOptions.None);

job.Submit();
job.GetExecutionProgressTask(CancellationToken.None).Wait();
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/mediaservices/client)

## <a name="samples"></a>샘플

- [Apple FairPlay로 보호되는 HLS 콘텐츠 스트림](https://azure.microsoft.com/resources/samples/media-services-dotnet-dynamic-encryption-with-fairplay/)
- [.NET SDK 확장을 사용하여 Azure Media Services 자산에 Blob 복사](https://azure.microsoft.com/resources/samples/media-services-dotnet-copy-blob-into-asset/)
- [.NET SDK를 사용하여 Azure Media Services로 라이브 스트림 인코딩 및 제공](https://azure.microsoft.com/resources/samples/media-services-dotnet-encode-live-stream-with-ams-clear/)

Azure Media Service 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=media-services)을 봅니다.


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
