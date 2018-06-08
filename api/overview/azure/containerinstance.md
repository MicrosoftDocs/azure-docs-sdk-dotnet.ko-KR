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
# <a name="azure-container-instances-libraries-for-net"></a>.NET용 Azure Container Instances 라이브러리

.NET용 Microsoft Azure Container Instances 라이브러리를 사용하여 Azure Container Instances를 만들고 관리합니다. 자세한 내용은 [Azure Container Instances 개요](/azure/container-instances/container-instances-overview)를 참조하세요.

## <a name="management-library"></a>관리 라이브러리

Azure에서 관리 라이브러리를 사용하여 Azure Container Instances를 만들고 관리합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.ContainerInstance.Fluent)를 직접 설치합니다.

### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.ContainerInstance.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.ContainerInstance.Fluent
```

## <a name="examples"></a>예

### <a name="create-container-group---single-container"></a>컨테이너 그룹 만들기 - 단일 컨테이너

이 예에서는 단일 컨테이너로 컨테이너 그룹을 만듭니다.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group](~/aci-docs-sample-dotnet/Program.cs#create_container_group "Create single-container group")]

### <a name="create-container-group---multiple-containers"></a>컨테이너 그룹 만들기 - 여러 컨테이너

이 예에서는 응용 프로그램 컨테이너와 사이드카 컨테이너라는 두 개의 컨테이너로 컨테이너 그룹을 만듭니다.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_multi](~/aci-docs-sample-dotnet/Program.cs#create_container_group_multi "Create multi-container group")]

### <a name="asynchronous-container-create-with-polling"></a>폴링을 사용하여 비동기 컨테이너 만들기

이 예에서는 비동기 만들기 메서드를 사용하여 단일 컨테이너로 컨테이너 그룹을 만듭니다. 그런 다음 컨테이너 그룹에 대해 Azure를 폴링하고 상태가 "실행 중"이 될 때까지 컨테이너 그룹의 상태를 출력합니다.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_polling](~/aci-docs-sample-dotnet/Program.cs#create_container_group_polling "Create single-container group with async and polling")]

### <a name="create-task-based-container-group"></a>작업 기반 컨테이너 그룹 만들기

이 예에서는 단일 작업 기반 컨테이너로 컨테이너 그룹을 만듭니다. 컨테이너는 "Never"의 [재시작 정책](/azure/container-instances/container-instances-restart-policy)과 [명령줄 사용자 정의](/azure/container-instances/container-instances-restart-policy#command-line-override)로 구성됩니다.

`echo FOO BAR`과 같이 여러 명령줄 인수를 사용하여 단일 명령을 실행하려면 이들 인수를 문자열 배열로서 `WithStartingCommandLines` 메서드에 제공해야 합니다. 예: 

`WithStartingCommandLines("echo", "FOO", "BAR")`

그러나 (잠재적으로) 여러 인수를 사용하여 여러 명령을 실행하려는 경우, 셸을 실행하고 연결된 명령을 인수로서 전달해야 합니다. 예를 들어,이는 `echo` 및 `tail` 명령을 모두 실행합니다.

`WithStartingCommandLines("/bin/sh", "-c", "echo FOO BAR && tail -f /dev/null")`

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[create_container_group_task](~/aci-docs-sample-dotnet/Program.cs#create_container_group_task "Run a task-based container")]

### <a name="list-container-groups"></a>컨테이너 그룹 나열

이 예는 리소스 그룹의 컨테이너 그룹을 나열합니다.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[list_container_groups](~/aci-docs-sample-dotnet/Program.cs#list_container_groups "List container groups")]

### <a name="get-an-existing-container-group"></a>기존 컨테이너 그룹 가져오기

이 예에서는 리소스 그룹에 있는 특정 컨테이너 그룹을 가져와서 몇 가지 속성과 그 값을 인쇄합니다.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[get_container_group](~/aci-docs-sample-dotnet/Program.cs#get_container_group "Get container group")]

### <a name="delete-a-container-group"></a>컨테이너 그룹 삭제

이 예에서는 리소스 그룹에서 컨테이너 그룹을 삭제합니다.

<!-- SOURCE REPO: https://github.com/Azure-Samples/aci-docs-sample-dotnet -->
[!code-csharp[delete_container_group](~/aci-docs-sample-dotnet/Program.cs#delete_container_group "Delete container group")]

## <a name="api-reference"></a>API 참조

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/containerinstances/management)

## <a name="samples"></a>샘플

* 앞의 예에 대한 소스 코드는 GitHub에서 찾을 수 있습니다.

  [Azure-Samples/aci-docs-sample-dotnet][aci-docs-sample-dotnet]

* 더 많은 Azure Container Instances 코드 샘플:

  [Azure 코드 샘플][samples]

앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
[samples]: https://azure.microsoft.com/resources/samples/?sort=0&term=ACI
[aci-docs-sample-dotnet]: https://github.com/Azure-Samples/aci-docs-sample-dotnet
