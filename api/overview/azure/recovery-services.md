---
title: Azure Recovery Services 및 .NET용백업 라이브러리
description: Azure Recovery Services 및 .NET용백업 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Recovery Services, Backup
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: recovery-services
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 6186411b668d0950328b49bb826e5b05c5ee0304
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065433"
---
# <a name="azure-recovery-services-and-backup-libraries-for-net"></a><span data-ttu-id="261d6-104">Azure Recovery Services 및 .NET용백업 라이브러리</span><span class="sxs-lookup"><span data-stu-id="261d6-104">Azure Recovery Services and Backup libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="261d6-105">개요</span><span class="sxs-lookup"><span data-stu-id="261d6-105">Overview</span></span>

<span data-ttu-id="261d6-106">Azure Recovery Services는 [Azure Backup](/azure/backup/) 및 [Azure Site Recovery](/azure/site-recovery/)를 포함한 데이터 복구를 위한 서비스 도구 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="261d6-106">Azure Recovery Services is a suite of services for data recovery, including [Azure Backup](/azure/backup/) and [Azure Site Recovery](/azure/site-recovery/).</span></span>

## <a name="management-library"></a><span data-ttu-id="261d6-107">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="261d6-107">Management library</span></span>

<span data-ttu-id="261d6-108">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="261d6-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="261d6-109">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="261d6-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

#### <a name="net-core-cli"></a><span data-ttu-id="261d6-110">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="261d6-110">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="261d6-111">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="261d6-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/recoveryservices/management)


## <a name="code-example"></a><span data-ttu-id="261d6-112">코드 예제</span><span class="sxs-lookup"><span data-stu-id="261d6-112">Code Example</span></span>

<span data-ttu-id="261d6-113">다음 코드에서는 관리 라이브러리를 사용하여 백업을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="261d6-113">The following code example uses the management library to trigger a backup.</span></span>

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
