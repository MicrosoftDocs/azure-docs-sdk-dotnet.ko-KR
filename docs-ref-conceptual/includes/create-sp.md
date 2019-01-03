---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: 5c8cb328802cfb94e944e4241852fb9568e8507f
ms.sourcegitcommit: e25b6ac74033f3b0a7610bf66feb654acb43054c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53430536"
---
<span data-ttu-id="f5d2b-101">.NET 애플리케이션에는 .NET용 Azure 관리 라이브러리를 사용하기 위해 Azure 구독에서 리소스를 읽고 만들 수 있는 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f5d2b-101">Your .NET application needs permissions to read and create resources in your Azure subscription in order to use the Azure Management Libraries for .NET.</span></span> <span data-ttu-id="f5d2b-102">서비스 주체를 만들고 이 액세스 권한을 부여하기 위해 해당 자격 증명을 사용하여 실행되도록 앱을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f5d2b-102">Create a service principal and configure your app to run with its credentials to grant this access.</span></span> <span data-ttu-id="f5d2b-103">서비스 주체는 앱에서 실행하는 데 필요한 권한만 부여하는 ID와 연결되는 비대화형 계정을 만드는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f5d2b-103">Service principals provide a way to create a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="f5d2b-104">먼저, [Azure Cloud Shell](https://shell.azure.com/bash)에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="f5d2b-104">First, login to [Azure Cloud Shell](https://shell.azure.com/bash).</span></span> <span data-ttu-id="f5d2b-105">서비스 주체를 만들려는 구독을 현재 사용하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f5d2b-105">Verify you are currently using the subscription in which you want the service principal created.</span></span> 

```azurecli-interactive
az account show
```

<span data-ttu-id="f5d2b-106">구독 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5d2b-106">Your subscription information is displayed.</span></span>

```json
{
  "environmentName": "AzureCloud",
  "id": "15dbcfa8-4b93-4c9a-881c-6189d39f04d4",
  "isDefault": true,
  "name": "my-subscription",
  "state": "Enabled",
  "tenantId": "43413cc1-5886-4711-9804-8cfea3d1c3ee",
  "user": {
    "cloudShellID": true,
    "name": "jane@contoso.com",
    "type": "user"
  }
}
```

<span data-ttu-id="f5d2b-107">올바른 구독에 로그인되지 않은 경우 `az account set -s <name or ID of subscription>`을 입력하여 올바른 구독을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f5d2b-107">If you're not logged into the correct subscription, select the correct one by typing `az account set -s <name or ID of subscription>`.</span></span>

<span data-ttu-id="f5d2b-108">다음 명령을 사용하여 서비스 주체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f5d2b-108">Create the service principal with the following command:</span></span>

```azurecli-interactive
az ad sp create-for-rbac --sdk-auth
```

<span data-ttu-id="f5d2b-109">서비스 주체 정보는 JSON으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5d2b-109">The service principal information is displayed as JSON.</span></span>

```json
{
  "clientId": "b52dd125-9272-4b21-9862-0be667bdf6dc",
  "clientSecret": "ebc6e170-72b2-4b6f-9de2-99410964d2d0",
  "subscriptionId": "ffa52f27-be12-4cad-b1ea-c2c241b6cceb",
  "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
```

<span data-ttu-id="f5d2b-110">JSON 출력을 복사하여 나중에 사용할 텍스트 편집기에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f5d2b-110">Copy and paste the JSON output to a text editor for use later.</span></span>
