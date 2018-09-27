---
title: .NET용 Azure Key Vault 라이브러리
description: .NET용 Azure Key Vault 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: key-vault
ms.openlocfilehash: a42eb9684bcfb8e8d2209235f61bbf6962cf5e9e
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190556"
---
# <a name="azure-key-vault-libraries-for-net"></a><span data-ttu-id="194bd-103">.NET용 Azure Key Vault 라이브러리</span><span class="sxs-lookup"><span data-stu-id="194bd-103">Azure Key Vault libraries for .NET</span></span>

## <a name="overview"></a><span data-ttu-id="194bd-104">개요</span><span class="sxs-lookup"><span data-stu-id="194bd-104">Overview</span></span>

<span data-ttu-id="194bd-105">Azure Key Vault는 클라우드 응용 프로그램 및 서비스에서 사용되는 암호화 키 및 비밀을 보호하는데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="194bd-105">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span>

<span data-ttu-id="194bd-106">[Key Vault란 무엇인가요?](/azure/key-vault/key-vault-whatis)를 읽은 후 [Azure Key Vault 시작](/azure/key-vault/key-vault-get-started)을 읽어보거나 [웹앱에서 Key Vault 사용](/azure/key-vault/key-vault-use-from-web-application) 방법에 대해 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="194bd-106">Read more about [What is Key Vault?](/azure/key-vault/key-vault-whatis) then [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started) or learn how to [Use Key Vault from a web app](/azure/key-vault/key-vault-use-from-web-application).</span></span>

## <a name="client-library"></a><span data-ttu-id="194bd-107">클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="194bd-107">Client library</span></span>

<span data-ttu-id="194bd-108">클라이언트 라이브러리를 사용하여 키와 관련 자산(예: 인증서 및 비밀)을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="194bd-108">Use the client library to manage keys and related assets such as certificates and secrets.</span></span>

<span data-ttu-id="194bd-109">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.KeyVault)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="194bd-109">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="194bd-110">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="194bd-110">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.KeyVault
```

```bash
dotnet add package Microsoft.Azure.KeyVault
```

### <a name="example"></a><span data-ttu-id="194bd-111">예</span><span class="sxs-lookup"><span data-stu-id="194bd-111">Example</span></span>

<span data-ttu-id="194bd-112">다음 예제에서는 응용 프로그램 설정에서 식별되는 특정 키에 대한 비밀을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="194bd-112">The following example retrieves the secret for a specific key that is identified in the application settings.</span></span>

```csharp
KeyVaultClient kv = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(securityToken));

SecretBundle sec = await kv.GetSecretAsync(WebConfigurationManager.AppSettings["SecretUri"]);

// sec.Value holds the secret
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="194bd-113">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="194bd-113">Explore the client APIs</span></span>](/dotnet/api/overview/azure/keyvault/client)

## <a name="management-library"></a><span data-ttu-id="194bd-114">관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="194bd-114">Management library</span></span>

<span data-ttu-id="194bd-115">관리 라이브러리를 사용하여 키 자격 증명 모음을 만들고 삭제 및 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="194bd-115">Use the management library to create, delete, and query key vaults.</span></span>

<span data-ttu-id="194bd-116">Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent)를 직접 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="194bd-116">Install the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent) directly from the Visual Studio [Package Manager console][PackageManager] or with the [.NET Core CLI][DotNetCLI].</span></span>

#### <a name="visual-studio-package-manager"></a><span data-ttu-id="194bd-117">Visual Studio 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="194bd-117">Visual Studio Package Manager</span></span>

```powershell
Install-Package Microsoft.Azure.Management.KeyVault.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.KeyVault.Fluent
```

### <a name="example"></a><span data-ttu-id="194bd-118">예</span><span class="sxs-lookup"><span data-stu-id="194bd-118">Example</span></span>

<span data-ttu-id="194bd-119">다음 예제에서는 지정된 리소스 그룹 및 위치에 대한 새 키 자격 증명 모음을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="194bd-119">The following example demonstrates how to create a new key vault for a given resource group and location.</span></span>

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
> [<span data-ttu-id="194bd-120">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="194bd-120">Explore the management APIs</span></span>](/dotnet/api/overview/azure/keyvault/management)

## <a name="samples"></a><span data-ttu-id="194bd-121">샘플</span><span class="sxs-lookup"><span data-stu-id="194bd-121">Samples</span></span>

* [<span data-ttu-id="194bd-122">Azure Key Vault 클라이언트 샘플 다운로드</span><span class="sxs-lookup"><span data-stu-id="194bd-122">Download the Azure Key Vault client samples</span></span>](https://www.microsoft.com/download/details.aspx?id=45343)
* [<span data-ttu-id="194bd-123">.NET에서 Azure 클라이언트 쪽 암호화 시작</span><span class="sxs-lookup"><span data-stu-id="194bd-123">Getting Started with Azure Client Side Encryption in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-dotnet-client-side-encryption/)


<span data-ttu-id="194bd-124">앱에서 사용할 수 있는 [샘플 .NET 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="194bd-124">Explore more [sample .NET code](https://azure.microsoft.com/resources/samples/?platform=dotnet) you can use in your apps.</span></span>

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
