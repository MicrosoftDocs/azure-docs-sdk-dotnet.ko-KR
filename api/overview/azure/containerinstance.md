---
title: .NET용 Azure Container Instances 라이브러리
description: .NET용 Azure Container Instances 라이브러리에 대한 참조
ms.date: 06/11/2018
ms.topic: reference
ms.service: dcontainer-instances
ms.openlocfilehash: 93f537058e0ed11f51cc6cb6cece01da80559822
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190726"
---
# <a name="azure-container-instances-libraries-for-net"></a><span data-ttu-id="3a029-103">.NET용 Azure Container Instances 라이브러리</span><span class="sxs-lookup"><span data-stu-id="3a029-103">Azure Container Instances libraries for .NET</span></span>

<span data-ttu-id="3a029-104">.NET용 Microsoft Azure Container Instances 라이브러리를 사용하여 Azure Container Instances를 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-104">Use the Microsoft Azure Container Instances libraries for .NET to create and manage Azure container instances.</span></span> <span data-ttu-id="3a029-105">자세한 내용은 [Azure Container Instances 개요](/azure/container-instances/container-instances-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a029-105">Learn more by reading the [Azure Container Instances overview](/azure/container-instances/container-instances-overview).</span></span>

## <a name="management-library"></a><span data-ttu-id="3a029-106">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="3a029-106">Management library</span></span>

<span data-ttu-id="3a029-107">Azure에서 관리 라이브러리를 사용하여 Azure Container Instances를 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-107">Use the management library to create and manage Azure container instances in Azure.</span></span>

<span data-ttu-id="3a029-108">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

### <a name="visual-studio-package-manager"></a><span data-ttu-id="3a029-109">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="3a029-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="example-source"></a><span data-ttu-id="3a029-110">예제 소스</span><span class="sxs-lookup"><span data-stu-id="3a029-110">Example source</span></span>

<span data-ttu-id="3a029-111">컨텍스트에서 다음 코드 예제를 보려는 경우, 다음 GitHub 리포지토리에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-111">If you'd like to see the following code examples in context, you can find them in the following GitHub repository:</span></span>

[<span data-ttu-id="3a029-112">Azure-Samples/aci-docs-sample-dotnet</span><span class="sxs-lookup"><span data-stu-id="3a029-112">Azure-Samples/aci-docs-sample-dotnet</span></span>](https://github.com/Azure-Samples/aci-docs-sample-dotnet)

## <a name="authentication"></a><span data-ttu-id="3a029-113">인증</span><span class="sxs-lookup"><span data-stu-id="3a029-113">Authentication</span></span>

<span data-ttu-id="3a029-114">SDK 클라이언트를 인증하는 가장 쉬운 방법 중 하나는 [파일 기반 인증][sdk-auth]을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-114">One of the easiest ways to authenticate SDK clients is with [file-based authentication][sdk-auth].</span></span> <span data-ttu-id="3a029-115">파일 기반 인증은 [IAzure][iazure] 클라이언트 개체를 인스턴스화할 때 자격 증명 파일을 구문 분석한 후, 이러한 자격 증명을 사용 Azure에서 인증을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-115">File-based authentication parses a credentials file when instantiating the [IAzure][iazure] client object, which then uses those credentials when authenticating with Azure.</span></span> <span data-ttu-id="3a029-116">파일 기반 인증 사용:</span><span class="sxs-lookup"><span data-stu-id="3a029-116">To use file-based authentication:</span></span>

1. <span data-ttu-id="3a029-117">[Azure CLI](/cli/azure) 또는 [Cloud Shell](https://shell.azure.com/)로 자격 증명 파일 만들기:</span><span class="sxs-lookup"><span data-stu-id="3a029-117">Create a credentials file with the [Azure CLI](/cli/azure) or [Cloud Shell](https://shell.azure.com/):</span></span>

   `az ad sp create-for-rbac --sdk-auth > my.azureauth`

   <span data-ttu-id="3a029-118">[Cloud Shell](https://shell.azure.com/)을 사용하여 자격 증명 파일을 생성하려면 해당 내용을 .NET 응용 프로그램이 액세스할 수 있는 로컬 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-118">If you use the [Cloud Shell](https://shell.azure.com/) to generate the credentials file, copy its contents into a local file that your .NET application can access.</span></span>

2. <span data-ttu-id="3a029-119">`AZURE_AUTH_LOCATION` 환경 변수를 생성된 자격 증명 파일의 전체 경로로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-119">Set the `AZURE_AUTH_LOCATION` environment variable to the full path of the generated credentials file.</span></span> <span data-ttu-id="3a029-120">예(Bash 셸):</span><span class="sxs-lookup"><span data-stu-id="3a029-120">For example (in the Bash shell):</span></span>

   ```bash
   export AZURE_AUTH_LOCATION=/home/yourusername/my.azureauth
   ```

<span data-ttu-id="3a029-121">자격 증명 파일을 만들고 `AZURE_AUTH_LOCATION` 환경 변수를 입력한 다음에는 [Azure.Authenticate][iazure-authenticate] 메서드를 사용하여 [IAzure][iazure] 클라이언트 개체를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-121">Once you've created the credentials file and populated the `AZURE_AUTH_LOCATION` environment variable, use the [Azure.Authenticate][iazure-authenticate] method to initialize the [IAzure][iazure] client object.</span></span> <span data-ttu-id="3a029-122">예제 프로젝트는 먼저 `AZURE_AUTH_LOCATION` 값을 가져온 후 초기화된 `IAzure` 클라이언트 개체를 반환하는 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-122">The example project first obtains the `AZURE_AUTH_LOCATION` value, then calls a method that returns an initialized `IAzure` client object:</span></span>

<span data-ttu-id="3a029-123"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]</span><span class="sxs-lookup"><span data-stu-id="3a029-123"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#L29-L35 "Get environment variable")]</span></span>

<span data-ttu-id="3a029-124">샘플 응용 프로그램의 이 메서드는 초기화된 [IAzure][iazure] 인스턴스를 반환하고, 이 인스턴스는 샘플에 있는 다른 모든 메서드에 첫 번째 매개변수로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-124">This method from the sample application returns the initialized [IAzure][iazure] instance, which is then passed as the first parameter to all other methods in the sample:</span></span>

<span data-ttu-id="3a029-125"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]</span><span class="sxs-lookup"><span data-stu-id="3a029-125"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[authenticate](~/aci-docs-sample-dotnet/Program.cs#azure_auth "Authenticate IAzure client object")]</span></span>

<span data-ttu-id="3a029-126">Azure용 .NET 관리 라이브러리에 사용 가능한 인증 방법에 대한 자세한 내용은 [.NET용 Azure 관리 라이브러리의 인증][sdk-auth]을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-126">For more details about the available authentication methods in the .NET management libraries for Azure, see [Authentication in Azure Management Libraries for .NET][sdk-auth].</span></span>

## <a name="create-container-group---single-container"></a><span data-ttu-id="3a029-127">컨테이너 그룹 만들기 - 단일 컨테이너</span><span class="sxs-lookup"><span data-stu-id="3a029-127">Create container group - single container</span></span>

<span data-ttu-id="3a029-128">이 예에서는 단일 컨테이너로 컨테이너 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-128">This example creates a container group with a single container.</span></span>

<span data-ttu-id="3a029-129"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]</span><span class="sxs-lookup"><span data-stu-id="3a029-129"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]</span></span>

## <a name="create-container-group---multiple-containers"></a><span data-ttu-id="3a029-130">컨테이너 그룹 만들기 - 여러 컨테이너</span><span class="sxs-lookup"><span data-stu-id="3a029-130">Create container group - multiple containers</span></span>

<span data-ttu-id="3a029-131">이 예에서는 응용 프로그램 컨테이너와 사이드카 컨테이너라는 두 개의 컨테이너로 컨테이너 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-131">This example creates a container group with two containers: an application container and a sidecar container.</span></span>

<span data-ttu-id="3a029-132"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]</span><span class="sxs-lookup"><span data-stu-id="3a029-132"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]</span></span>

## <a name="asynchronous-container-create-with-polling"></a><span data-ttu-id="3a029-133">폴링을 사용하여 비동기 컨테이너 만들기</span><span class="sxs-lookup"><span data-stu-id="3a029-133">Asynchronous container create with polling</span></span>

<span data-ttu-id="3a029-134">이 예에서는 비동기 만들기 메서드를 사용하여 단일 컨테이너로 컨테이너 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-134">This example creates a container group with a single container using the async create method.</span></span> <span data-ttu-id="3a029-135">그런 다음 컨테이너 그룹에 대해 Azure를 폴링하고 상태가 "실행 중"이 될 때까지 컨테이너 그룹의 상태를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-135">It then polls Azure for the container group, and outputs the container group's status until its state is "Running."</span></span>

<span data-ttu-id="3a029-136"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]</span><span class="sxs-lookup"><span data-stu-id="3a029-136"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]</span></span>

## <a name="create-task-based-container-group"></a><span data-ttu-id="3a029-137">작업 기반 컨테이너 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="3a029-137">Create task-based container group</span></span>

<span data-ttu-id="3a029-138">이 예에서는 단일 작업 기반 컨테이너로 컨테이너 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-138">This example creates a container group with a single task-based container.</span></span> <span data-ttu-id="3a029-139">컨테이너는 "Never"의 [재시작 정책](/azure/container-instances/container-instances-restart-policy)과 [명령줄 사용자 정의](/azure/container-instances/container-instances-restart-policy#command-line-override)로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-139">The container is configured with a [restart policy](/azure/container-instances/container-instances-restart-policy) of "Never" and a [custom command line](/azure/container-instances/container-instances-restart-policy#command-line-override).</span></span>

<span data-ttu-id="3a029-140">`echo FOO BAR`과 같이 여러 명령줄 인수를 사용하여 단일 명령을 실행하려면 이들 인수를 문자열 배열로서 `WithStartingCommandLines` 메서드에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-140">If you want to run a single command with several command-line arguments, for example `echo FOO BAR`, you must supply them as a string array to the `WithStartingCommandLines` method.</span></span> <span data-ttu-id="3a029-141">예: </span><span class="sxs-lookup"><span data-stu-id="3a029-141">For example:</span></span>

`WithStartingCommandLines("echo", "FOO", "BAR")`

<span data-ttu-id="3a029-142">그러나 (잠재적으로) 여러 인수를 사용하여 여러 명령을 실행하려는 경우, 셸을 실행하고 연결된 명령을 인수로서 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-142">If, however, you want to run multiple commands with (potentially) multiple arguments, you must execute a shell and pass the chained commands as an argument.</span></span> <span data-ttu-id="3a029-143">예를 들어,이는 `echo` 및 `tail` 명령을 모두 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-143">For example, this executes both an `echo` and a `tail` command:</span></span>

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<span data-ttu-id="3a029-144"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]</span><span class="sxs-lookup"><span data-stu-id="3a029-144"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]</span></span>

## <a name="list-container-groups"></a><span data-ttu-id="3a029-145">컨테이너 그룹 나열</span><span class="sxs-lookup"><span data-stu-id="3a029-145">List container groups</span></span>

<span data-ttu-id="3a029-146">이 예는 리소스 그룹의 컨테이너 그룹을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-146">This example lists the container groups in a resource group.</span></span>

<span data-ttu-id="3a029-147"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]</span><span class="sxs-lookup"><span data-stu-id="3a029-147"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]</span></span>

## <a name="get-an-existing-container-group"></a><span data-ttu-id="3a029-148">기존 컨테이너 그룹 가져오기</span><span class="sxs-lookup"><span data-stu-id="3a029-148">Get an existing container group</span></span>

<span data-ttu-id="3a029-149">이 예에서는 리소스 그룹에 있는 특정 컨테이너 그룹을 가져와서 몇 가지 속성과 그 값을 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-149">This example gets a specific container group residing in a resource group and then prints a few of its properties and their values.</span></span>

<span data-ttu-id="3a029-150"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]</span><span class="sxs-lookup"><span data-stu-id="3a029-150"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]</span></span>

## <a name="delete-a-container-group"></a><span data-ttu-id="3a029-151">컨테이너 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="3a029-151">Delete a container group</span></span>

<span data-ttu-id="3a029-152">이 예에서는 리소스 그룹에서 컨테이너 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-152">This example deletes a container group from a resource group.</span></span>

<span data-ttu-id="3a029-153"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]</span><span class="sxs-lookup"><span data-stu-id="3a029-153"><!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet --> [!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]</span></span>

## <a name="api-reference"></a><span data-ttu-id="3a029-154">API 참조</span><span class="sxs-lookup"><span data-stu-id="3a029-154">API reference</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a029-155">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="3a029-155">Explore the management APIs</span></span>](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a><span data-ttu-id="3a029-156">샘플</span><span class="sxs-lookup"><span data-stu-id="3a029-156">Samples</span></span>

* <span data-ttu-id="3a029-157">앞의 예에 대한 소스 코드는 GitHub에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-157">The source code for the preceding examples can be found on GitHub:</span></span>

  <span data-ttu-id="3a029-158">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span><span class="sxs-lookup"><span data-stu-id="3a029-158">[Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]</span></span>

* <span data-ttu-id="3a029-159">더 많은 Azure Container Instances 코드 샘플:</span><span class="sxs-lookup"><span data-stu-id="3a029-159">More Azure Container Instances code samples:</span></span>

  <span data-ttu-id="3a029-160">[Azure 코드 샘플][samples]</span><span class="sxs-lookup"><span data-stu-id="3a029-160">[Azure Code Samples][samples]</span></span>

<span data-ttu-id="3a029-161">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="3a029-161">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

<!-- LINKS - External -->
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[sdk-auth]: https://github.com/Azure/azure-libraries-for-net/blob/master/AUTH.md

<!-- LINKS - Internal -->
[DotNetCLI]: /dotnet/core/tools/dotnet-add-package
[PackageManager]: /nuget/tools/package-manager-console
[iazure]: /dotnet/api/microsoft.azure.management.fluent.azure
[iazure-authenticate]: /dotnet/api/microsoft.azure.management.fluent.azure.authenticate
