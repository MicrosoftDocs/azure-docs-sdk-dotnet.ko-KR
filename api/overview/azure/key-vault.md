---
title: .NET용 Azure Key Vault 라이브러리
description: .NET용 Azure Key Vault 라이브러리에 대한 참조
keywords: Azure, .NET, SDK, API, Key Vault
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.devlang: dotnet
ms.service: key-vault
ms.custom: devcenter, svc-overview
ms.openlocfilehash: 037b80f60616a37665eddb0b7b212d15180700ba
ms.sourcegitcommit: bfa1898c97798991215d08ce89dea87efff44157
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065453"
---
# <a name="azure-key-vault-libraries-for-net"></a><span data-ttu-id="aef96-104">.NET용 Azure Key Vault 라이브러리</span><span class="sxs-lookup"><span data-stu-id="aef96-104">Azure Key Vault libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="aef96-105">개요</span><span class="sxs-lookup"><span data-stu-id="aef96-105">Overview</span></span>

<span data-ttu-id="aef96-106">Azure Key Vault는 클라우드 응용 프로그램 및 서비스에서 사용되는 암호화 키 및 비밀을 보호하는데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aef96-106">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span>

<span data-ttu-id="aef96-107">[Key Vault란 무엇인가요?](/azure/key-vault/key-vault-whatis)를 읽은 후 [Azure Key Vault 시작](/azure/key-vault/key-vault-get-started)을 읽어보거나 [웹앱에서 Key Vault 사용](/azure/key-vault/key-vault-use-from-web-application) 방법에 대해 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="aef96-107">Read more about [What is Key Vault?](/azure/key-vault/key-vault-whatis) then [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started) or learn how to [Use Key Vault from a web app](/azure/key-vault/key-vault-use-from-web-application).</span></span>

## <a name="client-library"></a><span data-ttu-id="aef96-108">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="aef96-108">Client library</span></span>

<span data-ttu-id="aef96-109">클라이언트 라이브러리를 사용하여 키와 관련 자산(예: 인증서 및 비밀)을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="aef96-109">Use the client library to manage keys and related assets such as certificates and secrets.</span></span>

<span data-ttu-id="aef96-110">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.KeyVault)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="aef96-110">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="aef96-111">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="aef96-111">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.KeyVault
```

```bash
dotnet add package Microsoft.Azure.KeyVault
```

### <a name="example"></a><span data-ttu-id="aef96-112">예</span><span class="sxs-lookup"><span data-stu-id="aef96-112">Example</span></span>

<span data-ttu-id="aef96-113">다음 예제에서는 응용 프로그램 설정에서 식별되는 특정 키에 대한 비밀을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="aef96-113">The following example retrieves the secret for a specific key that is identified in the application settings.</span></span>

```csharp
KeyVaultClient kv = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(securityToken));

SecretBundle sec = await kv.GetSecretAsync(WebConfigurationManager.AppSettings["SecretUri"]);

// sec.Value holds the secret
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="aef96-114">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="aef96-114">Explore the client APIs</span></span>](/dotnet/api/overview/azure/keyvault/client)

## <a name="management-library"></a><span data-ttu-id="aef96-115">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="aef96-115">Management library</span></span>

<span data-ttu-id="aef96-116">관리 라이브러리를 사용하여 키 자격 증명 모음을 만들고 삭제 및 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="aef96-116">Use the management library to create, delete, and query key vaults.</span></span>

<span data-ttu-id="aef96-117">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="aef96-117">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="aef96-118">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="aef96-118">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.KeyVault.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.KeyVault.Fluent
```

### <a name="example"></a><span data-ttu-id="aef96-119">예</span><span class="sxs-lookup"><span data-stu-id="aef96-119">Example</span></span>

<span data-ttu-id="aef96-120">다음 예제에서는 지정된 리소스 그룹 및 위치에 대한 새 키 자격 증명 모음을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aef96-120">The following example demonstrates how to create a new key vault for a given resource group and location.</span></span>

```csharp
using (KeyVaultManagementClient client = new KeyVaultManagementClient(
    new TokenCloudCredentials(subscriptionId, accessToken)))
{
    client.Vaults.CreateOrUpdate(resourceGroupName, "myKeyVault", new VaultCreateOrUpdateParameters
    {
        Properties = new VaultProperties
        {
            EnabledForDeployment = true,
            EnabledForDiskEncryption = true,
            EnabledForTemplateDeployment = true,
            Location = resourceGroupLocation,
            // SKU level, access policies, tenants, etc.
        }
    });
}
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="aef96-121">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="aef96-121">Explore the management APIs</span></span>](/dotnet/api/overview/azure/keyvault/management)

## <a name="samples"></a><span data-ttu-id="aef96-122">샘플</span><span class="sxs-lookup"><span data-stu-id="aef96-122">Samples</span></span>

* [<span data-ttu-id="aef96-123">Azure Key Vault 클라이언트 샘플 다운로드</span><span class="sxs-lookup"><span data-stu-id="aef96-123">Download the Azure Key Vault client samples</span></span>](https://www.microsoft.com/download/details.aspx?id=45343)
* [<span data-ttu-id="aef96-124">.NET에서 Azure 클라이언트 쪽 암호화 시작</span><span class="sxs-lookup"><span data-stu-id="aef96-124">Getting Started with Azure Client Side Encryption in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-dotnet-client-side-encryption/)


<span data-ttu-id="aef96-125">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aef96-125">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
