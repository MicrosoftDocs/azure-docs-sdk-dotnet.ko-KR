---
title: ".NET용 Azure Key Vault 라이브러리"
description: ".NET용 Azure Key Vault 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Key Vault
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/21/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 77a4e710e858bbeb98579a7b540b52b4cb9dd7b0
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-key-vault-libraries-for-net"></a>.NET용 Azure Key Vault 라이브러리

## <a name="overview"></a>개요

Azure 키 자격 증명 모음은 클라우드 응용 프로그램 및 서비스에서 사용되는 암호화 키 및 비밀을 보호하는데 도움이 됩니다.

[Key Vault란 무엇인가요?](/azure/key-vault/key-vault-whatis)를 읽은 후 [Azure Key Vault 시작](/azure/key-vault/key-vault-get-started)을 읽어보거나 [웹앱에서 Key Vault 사용](/azure/key-vault/key-vault-use-from-web-application) 방법에 대해 알아보세요.

## <a name="client-library"></a>클라이언트 라이브러리

클라이언트 라이브러리를 사용하여 키와 관련 자산(예: 인증서 및 비밀)을 관리합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.KeyVault)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.KeyVault
```

```bash
dotnet add package Microsoft.Azure.KeyVault
```

### <a name="example"></a>예제

다음 예제에서는 응용 프로그램 설정에서 식별되는 특정 키에 대한 비밀을 검색합니다.

```csharp
KeyVaultClient kv = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(securityToken));

SecretBundle sec = await kv.GetSecretAsync(WebConfigurationManager.AppSettings["SecretUri"]);

// sec.Value holds the secret
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/keyvault/client)

## <a name="management-library"></a>관리 라이브러리

관리 라이브러리를 사용하여 키 자격 증명 모음을 만들고 삭제 및 쿼리합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.KeyVault.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.KeyVault.Fluent
```

```bash
dotnet add package Microsoft.Azure.Management.KeyVault.Fluent
```

### <a name="example"></a>예제

다음 예제에서는 지정된 리소스 그룹 및 위치에 대한 새 키 자격 증명 모음을 만드는 방법을 보여 줍니다.

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
> [관리 API 탐색](/dotnet/api/overview/azure/keyvault/management)

## <a name="samples"></a>샘플

* [Azure Key Vault 클라이언트 샘플 다운로드](https://www.microsoft.com/download/details.aspx?id=45343)
* [.NET에서 Azure 클라이언트 쪽 암호화 시작](https://azure.microsoft.com/resources/samples/storage-dotnet-client-side-encryption/)


앱에서 사용할 수 있는 [.NET 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)를 추가로 탐색합니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-package
