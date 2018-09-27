---
title: Azure Tools for Visual Studio 2015
description: Visual Studio 2015에서 Azure .NET 라이브러리를 사용하여 시작하는 도구를 가져옵니다.
ms.date: 10/19/2017
ms.openlocfilehash: b574841d17ba60e8ab52a4c06831f0b1cc8cc8aa
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190406"
---
# <a name="azure-tools-for-visual-studio-2015"></a><span data-ttu-id="af5a9-103">Azure Tools for Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="af5a9-103">Azure tools for Visual Studio 2015</span></span>

<span data-ttu-id="af5a9-104">**Azure SDK for Visual Studio 2015** 및 **Service Fabric SDK and Tools for Visual Studio 2015**를 설치하는 가장 빠르고 쉬운 방법은 [웹 플랫폼 설치 관리자](https://www.microsoft.com/web/downloads/platform.aspx)를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-104">The quickest and easiest way to install the **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** is using the [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).</span></span>  <span data-ttu-id="af5a9-105">Microsoft 웹 플랫폼 설치 관리자는 Azure Tools for Visual Studio 2015를 포함하여 Microsoft 웹 플랫폼 구성 요소 일부의 다운로드, 설치 및 업데이트를 간소화하는 무료 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-105">The Microsoft Web Platform Installer is a free tool that streamlines downloading, installing, and updating some of the components of the Microsoft Web Platform, including Azure tools for Visual Studio 2015.</span></span>  <span data-ttu-id="af5a9-106">이러한 SDK는 [Azure 다운로드 페이지](https://azure.microsoft.com/downloads/)에서 개별 구성 요소로 다운로드하여 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-106">These SDKs can also be downloaded and installed as individual components from the [Azure Downloads page](https://azure.microsoft.com/downloads/).</span></span> 

## <a name="using-the-web-platform-installer"></a><span data-ttu-id="af5a9-107">웹 플랫폼 설치 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="af5a9-107">Using the Web Platform Installer</span></span>

1. <span data-ttu-id="af5a9-108">이 [웹 플랫폼 설치 관리자 부트스트래퍼](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015)를 다운로드하여 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-108">Download and run this [Web Platform Installer bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span></span>  

2. <span data-ttu-id="af5a9-109">부트스트래퍼는 웹 플랫폼 설치 관리자를 설치하고(필요한 경우), *설치할 항목* 목록에 최신 버전의 **Azure SDK for Visual Studio 2015** 및 **Service Fabric SDK and Tools for Visual Studio 2015**를 자동으로 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-109">The bootstrapper will install Web Platform Installer (if needed) and automatically put the latest versions of the  **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** items in your *Items to be installed* list.</span></span>  <span data-ttu-id="af5a9-110">**Install**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-110">Click **Install**.</span></span>

    ![웹 플랫폼 설치 관리자](media/dotnet-sdk-vs2015-install/webpi.png)

3. <span data-ttu-id="af5a9-112">다음 화면에서 **동의**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-112">On the next screen, click **I Accept**.</span></span>  <span data-ttu-id="af5a9-113">Web API에서 선택한 구성 요소의 다운로드 및 설치를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-113">Web PI will begin downloading and installing the components you selected.</span></span>

4. <span data-ttu-id="af5a9-114">설치가 완료되면 확인 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-114">After the installation is finished, it will display a confirmation screen.</span></span>  <span data-ttu-id="af5a9-115">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-115">Click **Finish**.</span></span>  <span data-ttu-id="af5a9-116">이제 웹 플랫폼 설치 관리자를 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-116">You can now close Web Platform Installer.</span></span>

## <a name="verifying-the-installation"></a><span data-ttu-id="af5a9-117">설치 확인</span><span class="sxs-lookup"><span data-stu-id="af5a9-117">Verifying the installation</span></span>

1. <span data-ttu-id="af5a9-118">Visual Studio 2015에서 **도구** 메뉴를 클릭한 다음 **확장 및 업데이트...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-118">In Visual Studio 2015, click the **Tools** menu, and then click **Extensions and Updates...**.</span></span>

2. <span data-ttu-id="af5a9-119">표시된 목록에는 **Microsoft Azure App Service 도구**, **Microsoft Azure Storage 연결 서비스** 및 **Service Fabric 도구**와 같은 여러 Azure 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af5a9-119">The displayed list will contain several Azure tools, such as **Microsoft Azure App Service Tools**, **Microsoft Azure Storage Connected Service**, and **Service Fabric Tools**.</span></span>

    ![확장 및 업데이트](media/dotnet-sdk-vs2015-install/ext-tools.png)

## <a name="next-steps"></a><span data-ttu-id="af5a9-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="af5a9-121">Next steps</span></span>

<span data-ttu-id="af5a9-122">[.NET용 Azure 라이브러리 시작](dotnet-sdk-azure-get-started.md)</span><span class="sxs-lookup"><span data-stu-id="af5a9-122">[Get started with Azure libraries for .NET](dotnet-sdk-azure-get-started.md).</span></span>
