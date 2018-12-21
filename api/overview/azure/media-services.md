---
title: .NET용 Azure Media Services 라이브러리
description: .NET용 Azure Media Services 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: media-services
ms.openlocfilehash: cbb37d5d80c152ef53dba14c83cf2a2695e6b0f0
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190586"
---
# <a name="azure-media-services-libraries-for-net"></a><span data-ttu-id="220fd-103">.NET용 Azure Media Services 라이브러리</span><span class="sxs-lookup"><span data-stu-id="220fd-103">Azure Media Services libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="220fd-104">개요</span><span class="sxs-lookup"><span data-stu-id="220fd-104">Overview</span></span>

<span data-ttu-id="220fd-105">Microsoft Azure Media Services는 개발자가 확장 가능한 미디어 관리 및 배달 애플리케이션을 빌드할 수 있는 확장 가능한 클라우드 기반 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-105">Microsoft Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="220fd-106">Media Services는 다양한 클라이언트(예: TV, PC 및 모바일 디바이스)로의 주문형 및 라이브 스트리밍 배달을 위해 비디오 또는 오디오 콘텐츠를 안전하게 업로드, 저장, 인코딩 및 패키지할 수 있는 REST API를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-106">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span> 

<span data-ttu-id="220fd-107">자세한 내용은 [개요](/azure/media-services/media-services-overview) 및 [.NET 시작](/azure/media-services/media-services-dotnet-how-to-use)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="220fd-107">To learn more, see [Overview](/azure/media-services/media-services-overview) and [Getting started with .NET](/azure/media-services/media-services-dotnet-how-to-use).</span></span> 

## <a name="client-library"></a><span data-ttu-id="220fd-108">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="220fd-108">Client library</span></span>

<span data-ttu-id="220fd-109">Azure Media Services .NET SDK 라이브러리를 사용하면 .NET을 사용하여 Media Services를 프로그래밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-109">The Azure Media Services .NET SDK library enables you to program against Media Services using .NET.</span></span> <span data-ttu-id="220fd-110">Azure Media Services 클라이언트 라이브러리를 사용하여 Media Services API에 대해 연결, 인증 및 개발을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-110">Use the Azure Media Services client library to connect, authenticate, and develop against Media Services APIs.</span></span>  

<span data-ttu-id="220fd-111">자세한 내용은 [.NET SDK를 사용한 주문형 콘텐츠 배달 시작](/azure/media-services/media-services-dotnet-get-started)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="220fd-111">For more information, see [Get started with delivering content on demand using .NET SDK](/azure/media-services/media-services-dotnet-get-started).</span></span>

<span data-ttu-id="220fd-112">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/windowsazure.mediaservices)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-112">Install the [NuGet package](https://www.nuget.org/packages/windowsazure.mediaservices) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="220fd-113">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="220fd-113">Visual Studio Package Manager</span></span>

```powershell
Install-Package windowsazure.mediaservices
```

### <a name="code-example"></a><span data-ttu-id="220fd-114">코드 예제</span><span class="sxs-lookup"><span data-stu-id="220fd-114">Code Example</span></span>

<span data-ttu-id="220fd-115">다음 코드 예제에서는 Media Services .NET SDK를 사용하여 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-115">The following code example uses Media Services .NET SDK to perform the following tasks:</span></span>

- <span data-ttu-id="220fd-116">인코딩 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-116">Create an encoding job.</span></span>
- <span data-ttu-id="220fd-117">미디어 인코더 표준 인코더에 대한 참조를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-117">Get a reference to the Media Encoder Standard encoder.</span></span>
- <span data-ttu-id="220fd-118">적응 스트리밍 사전 설정을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-118">Specify to use the Adaptive Streaming preset.</span></span>
- <span data-ttu-id="220fd-119">작업에 단일 인코딩을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-119">Add a single encoding task to the job.</span></span>
- <span data-ttu-id="220fd-120">인코딩할 입력 자산을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-120">Specify the input asset to be encoded.</span></span>
- <span data-ttu-id="220fd-121">인코딩된 자산을 수신하는 출력 자산을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-121">Create an output asset to receive the encoded asset.</span></span>
- <span data-ttu-id="220fd-122">작업을 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-122">Submit the job.</span></span>


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
> [<span data-ttu-id="220fd-123">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="220fd-123">Explore the client APIs</span></span>](/dotnet/api/overview/azure/mediaservices/client)

## <a name="samples"></a><span data-ttu-id="220fd-124">샘플</span><span class="sxs-lookup"><span data-stu-id="220fd-124">Samples</span></span>

- [<span data-ttu-id="220fd-125">Apple FairPlay로 보호되는 HLS 콘텐츠 스트림</span><span class="sxs-lookup"><span data-stu-id="220fd-125">Stream your HLS content Protected with Apple FairPlay</span></span>](https://azure.microsoft.com/resources/samples/media-services-dotnet-dynamic-encryption-with-fairplay/)
- [<span data-ttu-id="220fd-126">.NET SDK 확장을 사용하여 Azure Media Services 자산에 Blob 복사</span><span class="sxs-lookup"><span data-stu-id="220fd-126">Copy blob into an Azure Media Services asset using .NET SDK Extensions</span></span>](https://azure.microsoft.com/resources/samples/media-services-dotnet-copy-blob-into-asset/)
- [<span data-ttu-id="220fd-127">.NET SDK를 사용하여 Azure Media Services로 라이브 스트림 인코딩 및 제공</span><span class="sxs-lookup"><span data-stu-id="220fd-127">Encode and Deliver a Live Stream with Azure Media Services using .NET SDK</span></span>](https://azure.microsoft.com/resources/samples/media-services-dotnet-encode-live-stream-with-ams-clear/)

<span data-ttu-id="220fd-128">Azure Media Services 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=media-services)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="220fd-128">View the [complete list](https://azure.microsoft.com/resources/samples/?platform=dotnet&service=media-services) of Azure Media Services samples.</span></span>


[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
