---
title: Azure .NET API
description: ".NET용 Azure API 개요"
keywords: "Azure, .NET, SDK, API, NuGet, 라이브러리, 패키지"
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
ms.openlocfilehash: cd0f8d6e0572fc9211af637e60d1a4f19e1ee1e8
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2017
---
# <a name="azure-net-apis"></a><span data-ttu-id="65289-104">Azure .NET API</span><span class="sxs-lookup"><span data-stu-id="65289-104">Azure .NET APIs</span></span>

<span data-ttu-id="65289-105">Azure .NET API를 사용하면 Azure 서비스를 사용하고 응용 프로그램 코드에서 Azure 리소스를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65289-105">The Azure .NET APIs let you use Azure services and manage Azure resources from your application code.</span></span> <span data-ttu-id="65289-106">API는 .NET 프로젝트에서 사용할 [NuGet 패키지](/dotnet/api/overview/azure/)로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65289-106">The APIs are available as [NuGet packages](/dotnet/api/overview/azure/) for use in your .NET projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="65289-107">Azure 리소스 관리</span><span class="sxs-lookup"><span data-stu-id="65289-107">Manage Azure resources</span></span>

<span data-ttu-id="65289-108">.NET용 Azure 라이브러리를 사용하면 .NET 응용 프로그램에서 Azure 리소스를 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65289-108">The Azure libraries for .NET let you create and manage Azure resources from your .NET applications.</span></span>

<span data-ttu-id="65289-109">Azure 리소스를 관리하는 많은 패키지에는 사양에 맞게 리소스를 정확히 구성하는 [흐름](dotnet-sdk-azure-concepts.md) 인터페이스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65289-109">Many of the packages for managing Azure resources have a [fluent](dotnet-sdk-azure-concepts.md) interface to configure resources exactly to your specifications.</span></span> <span data-ttu-id="65289-110">예를 들어 Linux VM을 만들려면 다음 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="65289-110">For example, to create a Windows VM you would write the following code:</span></span>

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

<span data-ttu-id="65289-111">[.NET 서비스 목록](/dotnet/api/overview/azure/)을 검토하여 프로젝트에서 라이브러리를 바로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65289-111">Review the [.NET service list](/dotnet/api/overview/azure/) to start using the libraries immediately with your projects.</span></span> <span data-ttu-id="65289-112">그런 다음 [시작 문서](dotnet-sdk-azure-get-started.md)을 참조하고, 인증을 설정하고, 자신의 Azure 구독에 대한 샘플 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="65289-112">Then read the [get started article](dotnet-sdk-azure-get-started.md) to set up authentication and run sample code against your own Azure subscription.</span></span>  <span data-ttu-id="65289-113">[개념 문서](dotnet-sdk-azure-concepts.md)는 SDK에서 사용하는 규칙과 응용 프로그램 코드를 단순화하는 데 활용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="65289-113">The [concepts article](dotnet-sdk-azure-concepts.md) goes into the conventions the SDK uses and how to leverage them to simplify your application code.</span></span> <span data-ttu-id="65289-114">새 기능, 주요 변경 내용 및 마이그레이션 지침은 [릴리스 정보](dotnet-sdk-azure-release-notes.md)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65289-114">New features, breaking changes, and migration instructions are available in the [release notes](dotnet-sdk-azure-release-notes.md).</span></span>

## <a name="consume-azure-services"></a><span data-ttu-id="65289-115">Azure 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="65289-115">Consume Azure services</span></span>

<span data-ttu-id="65289-116">.NET API를 사용하여 Azure 내에서 리소스를 만들고 프로그래밍 방식으로 관리하는 것 외에도 .NET API를 사용하여 응용 프로그램을 이러한 리소스에 연결하고 런타임에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65289-116">In addition to using .NET APIs to create and programmatically manage resources within Azure, you can also then use .NET APIs to connect your applications to these resources and use them at runtime.</span></span>  <span data-ttu-id="65289-117">예를 들어 SQL Database에 연결하거나 Azure Storage에 데이터를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65289-117">For example, you might connect to a SQL Database or store data within Azure Storage.</span></span>  <span data-ttu-id="65289-118">[서비스 API의 전체 목록](/dotnet/api/overview/azure/)을 검색하여 특정 Azure 서비스에 사용할 NuGet 패키지를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65289-118">You can identify which NuGet package to use for a particular Azure service by browsing our [full list of service APIs](/dotnet/api/overview/azure/).</span></span>  

## <a name="samples"></a><span data-ttu-id="65289-119">샘플</span><span class="sxs-lookup"><span data-stu-id="65289-119">Samples</span></span>

<span data-ttu-id="65289-120">다음 샘플에서는 .NET용 Azure 라이브러리를 사용하는 일반적인 자동화 작업에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="65289-120">The following samples cover common automation tasks with the Azure libraries for .NET:</span></span>

- [<span data-ttu-id="65289-121">가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="65289-121">Virtual machines</span></span>](dotnet-sdk-azure-virtual-machine-samples.md)
- [<span data-ttu-id="65289-122">웹앱</span><span class="sxs-lookup"><span data-stu-id="65289-122">Web apps</span></span>](dotnet-sdk-azure-web-apps-samples.md)
- [<span data-ttu-id="65289-123">SQL 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="65289-123">SQL Database</span></span>](dotnet-sdk-azure-sql-database-samples.md)

<span data-ttu-id="65289-124">통합된 [참조](/dotnet/api/overview/azure/?view=azure-dotnet)는 서비스 라이브러리와 관리 라이브러리 둘 다의 모든 패키지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65289-124">A unified [reference](/dotnet/api/overview/azure/?view=azure-dotnet) is available for all packages in both the service and management libraries.</span></span> <span data-ttu-id="65289-125">새 기능, 주요 변경 내용 및 마이그레이션 지침은 [릴리스 정보](dotnet-sdk-azure-release-notes.md)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65289-125">New features, breaking changes, and migration instructions are available in the [release notes](dotnet-sdk-azure-release-notes.md).</span></span>

[!include[Contribute and community](includes/contribute.md)]