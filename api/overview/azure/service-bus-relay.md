---
title: .NET용 Azure Service Bus Relay 라이브러리
description: .NET용 Azure Service Bus Relay 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Service Bus Relay
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: service-bus
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 1a869d5939e357c98ec417e6474f711b9ac8c466
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
ms.locfileid: "23566164"
---
# <a name="azure-service-bus-relay-libraries-for-net"></a><span data-ttu-id="88bb4-104">.NET용 Azure Service Bus Relay 라이브러리</span><span class="sxs-lookup"><span data-stu-id="88bb4-104">Azure Service Bus Relay libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="88bb4-105">개요</span><span class="sxs-lookup"><span data-stu-id="88bb4-105">Overview</span></span>

<span data-ttu-id="88bb4-106">Azure Relay 서비스는 방화벽 연결을 열거나 회사 네트워크 인프라를 주입식으로 변경하지 않고도 회사 엔터프라이즈 네트워크 내에 있는 서비스를 공용 클라우드에 안전하게 노출할 수 있게 함으로써 하이브리드 응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="88bb4-106">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="88bb4-107">릴레이는 다양한 전송 프로토콜 및 웹 서비스 표준을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="88bb4-107">Relay supports a variety of different transport protocols and web services standards.</span></span>
          
<span data-ttu-id="88bb4-108">[Azure Relay](/azure/service-bus-relay/relay-what-is-it)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="88bb4-108">Learn more about [Azure Relay](/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="client-library"></a><span data-ttu-id="88bb4-109">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="88bb4-109">Client library</span></span>

<span data-ttu-id="88bb4-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Relay)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="88bb4-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Relay) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="88bb4-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="88bb4-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Relay
```

```bash
dotnet add package Microsoft.Azure.Relay
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="88bb4-112">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="88bb4-112">Explore the client APIs</span></span>](/dotnet/api/overview/azure/relay/client)

## <a name="samples"></a><span data-ttu-id="88bb4-113">샘플</span><span class="sxs-lookup"><span data-stu-id="88bb4-113">Samples</span></span>

<span data-ttu-id="88bb4-114">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="88bb4-114">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package