서비스 주체 자격 증명을 사용하여 `azureauth.properties`라는 텍스트 파일을 만듭니다.

```plaintext
# sample management library properties file
subscription=15dbcfa8-4b93-4c9a-881c-6189d39f04d4
client=a2ab11af-01aa-4759-8345-7803287dbd39
key=password
tenant=43413cc1-5886-4711-9804-8cfea3d1c3ee
managementURI=https://management.core.windows.net/
baseURL=https://management.azure.com/
authURL=https://login.windows.net/
graphURL=https://graph.windows.net/
```

- subscription: `Login-AzureRmAccount`를 실행할 때 사용했던 *SubscriptionId* 값을 사용합니다.
- client: 서비스 주체 출력의 *ApplicationId* 값을 사용합니다.
- key: `New-AzureRmADServicePrincipal`을 실행할 때 할당한 *-Password* 매개 변수를 사용합니다(따옴표 제외).
- tenant: `Login-AzureRmAccount`를 실행할 때의 *TenantId* 값을 사용합니다.

코드에서 읽을 수 있는 시스템의 안전한 위치에 이 파일을 저장합니다. PowerShell을 사용하여 파일에 대한 전체 경로를 포함하여 `AZURE_AUTH_LOCATION`이라는 환경 변수를 설정합니다. 예:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.properties", "User")
```
