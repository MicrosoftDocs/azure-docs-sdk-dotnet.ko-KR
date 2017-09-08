<span data-ttu-id="5952e-101">.NET 응용 프로그램에는 .NET용 Azure 관리 라이브러리를 사용하기 위해 Azure 구독에서 리소스를 읽고 만들 수 있는 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5952e-101">Your .NET application needs permissions to read and create resources in your Azure subscription in order to use the Azure Management Libraries for .NET.</span></span> <span data-ttu-id="5952e-102">서비스 주체를 만들고 이 액세스 권한을 부여하기 위해 해당 자격 증명을 사용하여 실행되도록 앱을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5952e-102">Create a service principal and configure your app to run with its credentials to grant this access.</span></span> <span data-ttu-id="5952e-103">서비스 주체는 앱에서 실행하는 데 필요한 권한만 부여하는 ID와 연결되는 비대화형 계정을 만드는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5952e-103">Service principals provide a way to create a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="5952e-104">먼저, Azure PowerShell에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="5952e-104">First, login to Azure PowerShell:</span></span>

```powershell
Login-AzureRmAccount
```

<span data-ttu-id="5952e-105">테넌트 및 구독에 대해 표시된 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5952e-105">Note the information displayed about your tenant and subscription:</span></span>

```plaintext
Environment           : AzureCloud
Account               : jane@contoso.com
TenantId              : 43413cc1-5886-4711-9804-8cfea3d1c3ee
SubscriptionId        : 15dbcfa8-4b93-4c9a-881c-6189d39f04d4
SubscriptionName      : my-subscription
CurrentStorageAccount : 
```

<span data-ttu-id="5952e-106">다음과 같이 [PowerShell을 사용하여 서비스 주체를 만듭니다](/powershell/azure/create-azure-service-principal-azureps).</span><span class="sxs-lookup"><span data-stu-id="5952e-106">[Create a service principal using PowerShell](/powershell/azure/create-azure-service-principal-azureps), like this:</span></span>

```powershell
# Create the service principal (use a strong password)
$sp = New-AzureRmADServicePrincipal -DisplayName "AzureDotNetTest" -Password "password"

# Give it the permissions it needs...
New-AzureRmRoleAssignment -ServicePrincipalName $sp.ApplicationId -RoleDefinitionName Contributor

# Display the Application ID, because we'll need it later.
$sp | Select DisplayName, ApplicationId
```

<span data-ttu-id="5952e-107">ApplicationId를 메모해 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5952e-107">Make sure to note the ApplicationId:</span></span>

```plaintext
DisplayName     ApplicationId
-----------     -------------
AzureDotNetTest a2ab11af-01aa-4759-8345-7803287dbd39
```
