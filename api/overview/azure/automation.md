---
title: .NET용 Azure Automation 라이브러리
description: .NET용 Azure Automation 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Automation
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: automation
ms.custom: devcenter, svc-overview
ms.openlocfilehash: e45db49fa71e5ad16ab1e4f26d76cd9b0146ac5f
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065763"
---
# <a name="azure-automation-libraries-for-net"></a><span data-ttu-id="dffad-104">.NET용 Azure Automation 라이브러리</span><span class="sxs-lookup"><span data-stu-id="dffad-104">Azure Automation libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="dffad-105">개요</span><span class="sxs-lookup"><span data-stu-id="dffad-105">Overview</span></span>

<span data-ttu-id="dffad-106">Microsoft Azure Automation은 사용자가 클라우드 및 엔터프라이즈 환경에서 일반적으로 수행되는 작업을 자동화하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dffad-106">Microsoft Azure Automation provides a way for users to automate the tasks that are commonly performed in a cloud and enterprise environment.</span></span> 

<span data-ttu-id="dffad-107">자세한 내용은 [Azure Automation 개요](/azure/automation/automation-intro)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dffad-107">Learn more by reading the [Azure Automation Overview](/azure/automation/automation-intro).</span></span>

## <a name="management-library"></a><span data-ttu-id="dffad-108">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="dffad-108">Management library</span></span>

<span data-ttu-id="dffad-109">관리 라이브러리를 사용하여 Runbook 및 작업을 관리하고 필요한 상태 구성 설정을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="dffad-109">Using the management library to manage runbooks and jobs and manage Desired State Configuration settings.</span></span>

<span data-ttu-id="dffad-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Automation)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="dffad-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.Automation) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="dffad-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="dffad-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Automation
```

```bash
dotnet add package Microsoft.Azure.Management.Automation
```

### <a name="code-example"></a><span data-ttu-id="dffad-112">코드 예제</span><span class="sxs-lookup"><span data-stu-id="dffad-112">Code Example</span></span>

<span data-ttu-id="dffad-113">다음 예제에서는 기존 Runbook에 따라 새 작업을 시작하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dffad-113">The following example illustrates how to start a new job based on an existing runbook.</span></span>

```csharp
/*
  using Microsoft.Azure.Management.Automation;
*/
AutomationManagementClient client =
    new AutomationManagementClient(new CertificateCloudCredentials(subscriptionId, cert));

// Create job create parameters
JobCreateParameters jcParam = new JobCreateParameters
{
    Properties = new JobCreateProperties
    {
        Runbook = new RunbookAssociationProperty
        {
            Name = runbookName
        },
        Parameters = null // optional parameters here
    }
};

// create runbook job. This gives back the Job
Job job = automationManagementClient.Jobs.Create(automationAccountName, jcParam).Job;
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="dffad-114">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="dffad-114">Explore the management APIs</span></span>](/dotnet/api/overview/azure/automation/management)

## <a name="samples"></a><span data-ttu-id="dffad-115">샘플</span><span class="sxs-lookup"><span data-stu-id="dffad-115">Samples</span></span>

* <span data-ttu-id="dffad-116">[AzureBot](https://github.com/Microsoft/AzureBot)은 [Bot Framework](https://docs.microsoft.com/bot-framework/) 및 [Cognitive Services](/cognitive-services)가 포함된 자동화 라이브러리를 사용하여 Azure에서 개발자의 생산성을 향상시켜 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dffad-116">[AzureBot](https://github.com/Microsoft/AzureBot) uses the automation library with the [Bot Framework](https://docs.microsoft.com/bot-framework/) and [Cognitive Services](/cognitive-services) to improve developer productivity on Azure</span></span>

<span data-ttu-id="dffad-117">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="dffad-117">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
