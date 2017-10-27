---
title: "Azure Recovery Services 및 .NET용백업 라이브러리"
description: "Azure Recovery Services 및 .NET용백업 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Recovery Services, Backup
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: recovery-services
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 3b399827f187fc2cb59c8698a555e63d08cee6c7
ms.sourcegitcommit: 2c08a778353ed743b9e437ed85f2e1dfb21b9427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2017
---
# <a name="azure-recovery-services-and-backup-libraries-for-net"></a><span data-ttu-id="58404-104">Azure Recovery Services 및 .NET용백업 라이브러리</span><span class="sxs-lookup"><span data-stu-id="58404-104">Azure Recovery Services and Backup libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="58404-105">개요</span><span class="sxs-lookup"><span data-stu-id="58404-105">Overview</span></span>

<span data-ttu-id="58404-106">Azure Recovery Services는 [Azure Backup](/azure/backup/) 및 [Azure Site Recovery](/azure/site-recovery/)를 포함한 데이터 복구를 위한 서비스 도구 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="58404-106">Azure Recovery Services is a suite of services for data recovery, including [Azure Backup](/azure/backup/) and [Azure Site Recovery](/azure/site-recovery/).</span></span>

## <a name="management-library"></a><span data-ttu-id="58404-107">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="58404-107">Management library</span></span>

<span data-ttu-id="58404-108">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="58404-108">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="58404-109">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="58404-109">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

#### <a name="net-core-cli"></a><span data-ttu-id="58404-110">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="58404-110">.NET Core CLI</span></span>

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="58404-111">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="58404-111">Explore the management APIs</span></span>](/dotnet/api/overview/azure/recoveryservices/management)


## <a name="code-example"></a><span data-ttu-id="58404-112">코드 예제</span><span class="sxs-lookup"><span data-stu-id="58404-112">Code Example</span></span>

<span data-ttu-id="58404-113">다음 코드에서는 관리 라이브러리를 사용하여 백업을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="58404-113">The following code example uses the management library to trigger a backup.</span></span>

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
