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
# <a name="azure-backup-libraries-for-net"></a>.NET용 Azure Backup 라이브러리

## <a name="overview"></a>개요

Azure Backup은 데이터를 백업, 보호 및 복원하는 데 사용할 수 있는 클라우드 서비스입니다.

[Azure Backup이란?](/azure/backup/backup-introduction-to-azure-backup)을 읽고 Azure Backup에 대해 자세히 알아보세요.

## <a name="management-library"></a>관리 라이브러리

백업 관리 라이브러리를 사용하여 백업을 관리하고 Recovery Services 자격 증명 모음을 설정합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.RecoveryServices.Backup)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.RecoveryServices.Backup
```

```bash
dotnet add package Microsoft.Azure.Management.RecoveryServices.Backup
```

다음 코드에서는 관리 라이브러리를 사용하여 백업을 트리거합니다.

```csharp
RecoveryServicesBackupManagementClient client = new RecoveryServicesBackupManagementClient(credentials);
TriggerBackupRequest triggerBackupRequest = new TriggerBackupRequest();
BaseRecoveryServicesJobResponse resp =
    await client.Backups.TriggerBackupAsync(resourceGroupName, resourceName, null,
        fabricName, containerName, protectedItemName, triggerBackupRequest);
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/backup/management)

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
