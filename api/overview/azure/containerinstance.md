---
title: .NET용 Azure Container Instances 라이브러리
description: .NET용 Azure Container Instances 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Container Instances, ACI
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 05/25/2018
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: dcontainer-instances
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 033f67a989b0ed6cfcb67a6212c0d5c46c485afa
ms.sourcegitcommit: 4ae9f77a9300a4fe54d0179055ae61191078f207
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34567189"
---
# <a name="azure-container-instances-libraries-for-net"></a><span data-ttu-id="badfb-104">.NET용 Azure Container Instances 라이브러리</span><span class="sxs-lookup"><span data-stu-id="badfb-104">Azure Container Instances libraries for .NET</span></span>

<span data-ttu-id="badfb-105">.NET용 Microsoft Azure Container Instances 라이브러리를 사용하여 Azure Container Instances를 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-105">Use the Microsoft Azure Container Instances libraries for .NET to create and manage Azure container instances.</span></span> <span data-ttu-id="badfb-106">자세한 내용은 [Azure Container Instances 개요](/azure/container-instances/container-instances-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="badfb-106">Learn more by reading the [Azure Container Instances overview](/azure/container-instances/container-instances-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="badfb-107">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="badfb-107">Management library</span></span>

<span data-ttu-id="badfb-108">Azure에서 관리 라이브러리를 사용하여 Azure Container Instances를 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-108">Use the management library to create and manage Azure container instances in Azure.</span></span>

<span data-ttu-id="badfb-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

### <a name="visual-studio-package-manager"></a><span data-ttu-id="badfb-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="badfb-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="examples"></a><span data-ttu-id="badfb-111">예</span><span class="sxs-lookup"><span data-stu-id="badfb-111">Examples</span></span>

### <a name="create-container-group---single-container"></a><span data-ttu-id="badfb-112">컨테이너 그룹 만들기 - 단일 컨테이너</span><span class="sxs-lookup"><span data-stu-id="badfb-112">Create container group - single container</span></span>

<span data-ttu-id="badfb-113">이 예에서는 단일 컨테이너로 컨테이너 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-113">This example creates a container group with a single container.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]

### <a name="create-container-group---multiple-containers"></a><span data-ttu-id="badfb-114">컨테이너 그룹 만들기 - 여러 컨테이너</span><span class="sxs-lookup"><span data-stu-id="badfb-114">Create container group - multiple containers</span></span>

<span data-ttu-id="badfb-115">이 예에서는 응용 프로그램 컨테이너와 사이드카 컨테이너라는 두 개의 컨테이너로 컨테이너 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-115">This example creates a container group with two containers: an application container and a sidecar container.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]

### <a name="asynchronous-container-create-with-polling"></a><span data-ttu-id="badfb-116">폴링을 사용하여 비동기 컨테이너 만들기</span><span class="sxs-lookup"><span data-stu-id="badfb-116">Asynchronous container create with polling</span></span>

<span data-ttu-id="badfb-117">이 예에서는 비동기 만들기 메서드를 사용하여 단일 컨테이너로 컨테이너 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-117">This example creates a container group with a single container using the async create method.</span></span> <span data-ttu-id="badfb-118">그런 다음 컨테이너 그룹에 대해 Azure를 폴링하고 상태가 "실행 중"이 될 때까지 컨테이너 그룹의 상태를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-118">It then polls Azure for the container group, and outputs the container group's status until its state is "Running."</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]

### <a name="create-task-based-container-group"></a><span data-ttu-id="badfb-119">작업 기반 컨테이너 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="badfb-119">Create task-based container group</span></span>

<span data-ttu-id="badfb-120">이 예에서는 단일 작업 기반 컨테이너로 컨테이너 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-120">This example creates a container group with a single task-based container.</span></span> <span data-ttu-id="badfb-121">컨테이너는 "Never"의 [재시작 정책](/azure/container-instances/container-instances-restart-policy)과 [명령줄 사용자 정의](/azure/container-instances/container-instances-restart-policy#command-line-override)로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-121">The container is configured with a [restart policy](/azure/container-instances/container-instances-restart-policy) of "Never" and a [custom command line](/azure/container-instances/container-instances-restart-policy#command-line-override).</span></span>

<span data-ttu-id="badfb-122">`echo FOO BAR`과 같이 여러 명령줄 인수를 사용하여 단일 명령을 실행하려면 이들 인수를 문자열 배열로서 `WithStartingCommandLines` 메서드에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-122">If you want to run a single command with several command-line arguments, for example `echo FOO BAR`, you must supply them as a string array to the `WithStartingCommandLines` method.</span></span> <span data-ttu-id="badfb-123">예: </span><span class="sxs-lookup"><span data-stu-id="badfb-123">For example:</span></span>

`WithStartingCommandLines("echo", "FOO", "BAR")`

<span data-ttu-id="badfb-124">그러나 (잠재적으로) 여러 인수를 사용하여 여러 명령을 실행하려는 경우, 셸을 실행하고 연결된 명령을 인수로서 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-124">If, however, you want to run multiple commands with (potentially) multiple arguments, you must execute a shell and pass the chained commands as an argument.</span></span> <span data-ttu-id="badfb-125">예를 들어,이는 `echo` 및 `tail` 명령을 모두 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-125">For example, this executes both an `echo` and a `tail` command:</span></span>

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]

### <a name="list-container-groups"></a><span data-ttu-id="badfb-126">컨테이너 그룹 나열</span><span class="sxs-lookup"><span data-stu-id="badfb-126">List container groups</span></span>

<span data-ttu-id="badfb-127">이 예는 리소스 그룹의 컨테이너 그룹을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-127">This example lists the container groups in a resource group.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]

### <a name="get-an-existing-container-group"></a><span data-ttu-id="badfb-128">기존 컨테이너 그룹 가져오기</span><span class="sxs-lookup"><span data-stu-id="badfb-128">Get an existing container group</span></span>

<span data-ttu-id="badfb-129">이 예에서는 리소스 그룹에 있는 특정 컨테이너 그룹을 가져와서 몇 가지 속성과 그 값을 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-129">This example gets a specific container group residing in a resource group and then prints a few of its properties and their values.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]

### <a name="delete-a-container-group"></a><span data-ttu-id="badfb-130">컨테이너 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="badfb-130">Delete a container group</span></span>

<span data-ttu-id="badfb-131">이 예에서는 리소스 그룹에서 컨테이너 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-131">This example deletes a container group from a resource group.</span></span>

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]

## <a name="api-reference"></a><span data-ttu-id="badfb-132">API 참조</span><span class="sxs-lookup"><span data-stu-id="badfb-132">API reference</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="badfb-133">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="badfb-133">Explore the management APIs</span></span>](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a><span data-ttu-id="badfb-134">샘플</span><span class="sxs-lookup"><span data-stu-id="badfb-134">Samples</span></span>

* <span data-ttu-id="badfb-135">앞의 예에 대한 소스 코드는 GitHub에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-135">The source code for the preceding examples can be found on GitHub:</span></span>

  <span data-ttu-id="badfb-136">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span><span class="sxs-lookup"><span data-stu-id="badfb-136">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span></span>

* <span data-ttu-id="badfb-137">더 많은 Azure Container Instances 코드 샘플:</span><span class="sxs-lookup"><span data-stu-id="badfb-137">More Azure Container Instances code samples:</span></span>

  <span data-ttu-id="badfb-138">[Azure 코드 샘플][samples]</span><span class="sxs-lookup"><span data-stu-id="badfb-138">[Azure Code Samples][samples]</span></span>

<span data-ttu-id="badfb-139">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="badfb-139">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
