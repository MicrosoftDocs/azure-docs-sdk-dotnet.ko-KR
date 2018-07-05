.NET 응용 프로그램에는 .NET용 Azure 관리 라이브러리를 사용하기 위해 Azure 구독에서 리소스를 읽고 만들 수 있는 권한이 필요합니다. 서비스 주체를 만들고 이 액세스 권한을 부여하기 위해 해당 자격 증명을 사용하여 실행되도록 앱을 구성합니다. 서비스 주체는 앱에서 실행하는 데 필요한 권한만 부여하는 ID와 연결되는 비대화형 계정을 만드는 방법을 제공합니다.

먼저, Azure PowerShell에 로그인합니다.

```powershell
Login-AzureRmAccount
```

테넌트 및 구독에 대해 표시된 정보를 확인합니다.

```plaintext
Environment           : AzureCloud
Account               : jane@contoso.com
TenantId              : 43413cc1-5886-4711-9804-8cfea3d1c3ee
SubscriptionId        : 15dbcfa8-4b93-4c9a-881c-6189d39f04d4
SubscriptionName      : my-subscription
CurrentStorageAccount : 
```

다음과 같이 [PowerShell을 사용하여 서비스 주체를 만듭니다](/powershell/azure/create-azure-service-principal-azureps). 

> [!NOTE]
> 아래의 `New-AzureRmADServicePrincipal` cmdlet이 "identifierUris 속성과 값이 동일한 다른 개체가 이미 있습니다."를 반환할 경우, 해당 이름의 서비스 주체가 테넌트에 이미 있는 것입니다. **DisplayName** 매개 변수에 대해 다른 값을 사용합니다. 

```powershell
# Create the service principal (use a strong password)
$cred = Get-Credential
$sp = New-AzureRmADServicePrincipal -DisplayName "AzureDotNetTest" -Password $cred.Password

# Give it the permissions it needs...
New-AzureRmRoleAssignment -ServicePrincipalName $sp.ApplicationId -RoleDefinitionName Contributor

# Display the Application ID, because we'll need it later.
$sp | Select DisplayName, ApplicationId
```

ApplicationId를 메모해 두어야 합니다.

```plaintext
DisplayName     ApplicationId
-----------     -------------
AzureDotNetTest a2ab11af-01aa-4759-8345-7803287dbd39
```
