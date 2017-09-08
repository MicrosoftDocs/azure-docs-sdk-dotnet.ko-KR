---
title: ".NET용 Azure Backup 라이브러리"
description: ".NET용 Azure Backup 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Backup
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/24/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 93eeaeda1860e3b7190dfb0ae917b4b85b5a3609
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-backup-libraries-for-net"></a><span data-ttu-id="72c3f-104">.NET용 Azure Backup 라이브러리</span><span class="sxs-lookup"><span data-stu-id="72c3f-104">Azure Backup libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="72c3f-105">개요</span><span class="sxs-lookup"><span data-stu-id="72c3f-105">Overview</span></span>

<span data-ttu-id="72c3f-106">Azure Backup은 데이터를 백업, 보호 및 복원하는 데 사용할 수 있는 클라우드 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="72c3f-106">Azure Backup is the cloud service you can use to back up, protect, and restore your data.</span></span>

<span data-ttu-id="72c3f-107">[Azure Backup이란?](/azure/backup/backup-introduction-to-azure-backup)을 읽고 Azure Backup에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="72c3f-107">Learn more about Azure Backup by reading [What is Azure Backup?](/azure/backup/backup-introduction-to-azure-backup).</span></span>

## <a name="management-library"></a><span data-ttu-id="72c3f-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="72c3f-108">Management library</span></span>

<span data-ttu-id="72c3f-109">백업 관리 라이브러리를 사용하여 백업을 관리하고 Recovery Services 자격 증명 모음을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c3f-109">Use the backup management library to manage backups and set up Recovery Services vaults.</span></span>

<span data-ttu-id="72c3f-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices.Backup)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="72c3f-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices.Backup) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="72c3f-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="72c3f-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

<span data-ttu-id="72c3f-112">다음 코드에서는 관리 라이브러리를 사용하여 백업을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="72c3f-112">The following code example uses the management library to trigger a backup.</span></span>

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="72c3f-113">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="72c3f-113">Explore the management APIs</span></span>](/dotnet/api/overview/azure/backup/management)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
