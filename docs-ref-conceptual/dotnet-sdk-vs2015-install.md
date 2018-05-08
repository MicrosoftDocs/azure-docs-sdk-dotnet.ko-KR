---
title: Azure Tools for Visual Studio 2015
description: Visual Studio 2015에서 Azure .NET 라이브러리를 사용하여 시작하는 도구를 가져옵니다.
keywords: Azure .NET SDK, VS2015, Visual Studio 2015
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 5046781a16b5b330b95c4ad36e8a8187126fef4e
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2018
---
# <a name="azure-tools-for-visual-studio-2015"></a><span data-ttu-id="c197a-104">Azure Tools for Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="c197a-104">Azure tools for Visual Studio 2015</span></span>

<span data-ttu-id="c197a-105">**Azure SDK for Visual Studio 2015** 및 **Service Fabric SDK and Tools for Visual Studio 2015**를 설치하는 가장 빠르고 쉬운 방법은 [웹 플랫폼 설치 관리자](https://www.microsoft.com/web/downloads/platform.aspx)를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-105">The quickest and easiest way to install the **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** is using the [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).</span></span>  <span data-ttu-id="c197a-106">Microsoft 웹 플랫폼 설치 관리자는 Azure Tools for Visual Studio 2015를 포함하여 Microsoft 웹 플랫폼 구성 요소 일부의 다운로드, 설치 및 업데이트를 간소화하는 무료 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-106">The Microsoft Web Platform Installer is a free tool that streamlines downloading, installing, and updating some of the components of the Microsoft Web Platform, including Azure tools for Visual Studio 2015.</span></span>  <span data-ttu-id="c197a-107">이러한 SDK는 [Azure 다운로드 페이지](https://azure.microsoft.com/downloads/)에서 개별 구성 요소로 다운로드하여 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-107">These SDKs can also be downloaded and installed as individual components from the [Azure Downloads page](https://azure.microsoft.com/downloads/).</span></span> 

## <a name="using-the-web-platform-installer"></a><span data-ttu-id="c197a-108">웹 플랫폼 설치 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="c197a-108">Using the Web Platform Installer</span></span>

1. <span data-ttu-id="c197a-109">이 [웹 플랫폼 설치 관리자 부트스트래퍼](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015)를 다운로드하여 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-109">Download and run this [Web Platform Installer bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span></span>  

2. <span data-ttu-id="c197a-110">부트스트래퍼는 웹 플랫폼 설치 관리자를 설치하고(필요한 경우), *설치할 항목* 목록에 최신 버전의 **Azure SDK for Visual Studio 2015** 및 **Service Fabric SDK and Tools for Visual Studio 2015**를 자동으로 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-110">The bootstrapper will install Web Platform Installer (if needed) and automatically put the latest versions of the  **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** items in your *Items to be installed* list.</span></span>  <span data-ttu-id="c197a-111">**Install**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-111">Click **Install**.</span></span>

    ![웹 플랫폼 설치 관리자](media/dotnet-sdk-vs2015-install/webpi.png)

3. <span data-ttu-id="c197a-113">다음 화면에서 **동의**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-113">On the next screen, click **I Accept**.</span></span>  <span data-ttu-id="c197a-114">Web API에서 선택한 구성 요소의 다운로드 및 설치를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-114">Web PI will begin downloading and installing the components you selected.</span></span>

4. <span data-ttu-id="c197a-115">설치가 완료되면 확인 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-115">After the installation is finished, it will display a confirmation screen.</span></span>  <span data-ttu-id="c197a-116">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-116">Click **Finish**.</span></span>  <span data-ttu-id="c197a-117">이제 웹 플랫폼 설치 관리자를 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-117">You can now close Web Platform Installer.</span></span>

## <a name="verifying-the-installation"></a><span data-ttu-id="c197a-118">설치 확인</span><span class="sxs-lookup"><span data-stu-id="c197a-118">Verifying the installation</span></span>

1. <span data-ttu-id="c197a-119">Visual Studio 2015에서 **도구** 메뉴를 클릭한 다음 **확장 및 업데이트...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-119">In Visual Studio 2015, click the **Tools** menu, and then click **Extensions and Updates...**.</span></span>

2. <span data-ttu-id="c197a-120">표시된 목록에는 **Microsoft Azure App Service 도구**, **Microsoft Azure Storage 연결 서비스** 및 **Service Fabric 도구**와 같은 여러 Azure 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c197a-120">The displayed list will contain several Azure tools, such as **Microsoft Azure App Service Tools**, **Microsoft Azure Storage Connected Service**, and **Service Fabric Tools**.</span></span>

    ![확장 및 업데이트](media\dotnet-sdk-vs2015-install\ext-tools.png)

## <a name="next-steps"></a><span data-ttu-id="c197a-122">다음 단계</span><span class="sxs-lookup"><span data-stu-id="c197a-122">Next steps</span></span>

<span data-ttu-id="c197a-123">[.NET용 Azure 라이브러리 시작](dotnet-sdk-azure-get-started.md)</span><span class="sxs-lookup"><span data-stu-id="c197a-123">[Get started with Azure libraries for .NET](dotnet-sdk-azure-get-started.md).</span></span>
