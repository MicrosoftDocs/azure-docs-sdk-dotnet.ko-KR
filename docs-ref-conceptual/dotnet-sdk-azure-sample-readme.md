---
title: ".NET용 Azure 관리 라이브러리 샘플 지침"
description: ".NET용 Azure 관리 라이브러리를 사용하여 리소스를 만들고 업데이트하는 샘플 코드를 가져옵니다."
keywords: "Azure, .NET, SDK, API, 샘플, 예제"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: cf5195bbc64ae39917355e3b775afa0c46604c4a
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
---
# <a name="azure-management-libraries-for-net-sample-instructions"></a><span data-ttu-id="9cba6-104">.NET용 Azure 관리 라이브러리 샘플 지침</span><span class="sxs-lookup"><span data-stu-id="9cba6-104">Azure management libraries for .NET sample instructions</span></span>

<span data-ttu-id="9cba6-105">이 문서에서는 .NET용 Azure 관리 라이브러리 샘플을 실행하는 데 필요한 필수 구성 요소 및 인증에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba6-105">This article describes the prerequisites and authentication required for running the samples for the Azure management libraries for .NET.</span></span>

## <a name="prerequisties"></a><span data-ttu-id="9cba6-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="9cba6-106">Prerequisties</span></span> 

* <span data-ttu-id="9cba6-107">[Visual Studio 2017](https://www.visualstudio.com/vs/) 또는 [.NET Core SDK](https://www.microsoft.com/net/download/core)</span><span class="sxs-lookup"><span data-stu-id="9cba6-107">[Visual Studio 2017](https://www.visualstudio.com/vs/) or [.NET Core SDK](https://www.microsoft.com/net/download/core)</span></span>
* <span data-ttu-id="9cba6-108">[Microsoft Azure 구독](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="9cba6-108">A [Microsoft Azure subscription](https://azure.microsoft.com/free/)</span></span>
* [<span data-ttu-id="9cba6-109">Git 명령줄 클라이언트</span><span class="sxs-lookup"><span data-stu-id="9cba6-109">Git command line client</span></span>](https://git-scm.com/)
* [<span data-ttu-id="9cba6-110">Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="9cba6-110">Azure PowerShell</span></span>](/powershell/azure/install-azurerm-ps)

## <a name="authentication-for-all-samples"></a><span data-ttu-id="9cba6-111">모든 샘플에 대한 인증</span><span class="sxs-lookup"><span data-stu-id="9cba6-111">Authentication for all samples</span></span>

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="running-the-samples"></a><span data-ttu-id="9cba6-112">샘플 실행</span><span class="sxs-lookup"><span data-stu-id="9cba6-112">Running the samples</span></span>

<span data-ttu-id="9cba6-113">Git를 사용하여 샘플을 복제한 후에는 Visual Studio에서 샘플을 열고 IDE를 사용하여 샘플을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba6-113">Once you have used Git to clone the sample, you can open the sample in Visual Studio and run the sample using the IDE.</span></span>  <span data-ttu-id="9cba6-114">또는 .NET Core SDK를 사용하고 다음과 같이 명령줄에서 샘플을 빌드하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba6-114">Alternatively, use the .NET Core SDK to build and run the sample from the command line, like this:</span></span>

```cmd
git clone https://github.com/Azure-Samples/app-service-dotnet-configure-deployment-sources-for-web-apps.git
cd app-service-dotnet-configure-deployment-sources-for-web-apps
dotnet restore
dotnet run
```