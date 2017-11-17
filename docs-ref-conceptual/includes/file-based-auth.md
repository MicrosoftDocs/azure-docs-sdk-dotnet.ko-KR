<span data-ttu-id="4111b-101">서비스 주체 자격 증명을 사용하여 `azureauth.properties`라는 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4111b-101">Create a text file named `azureauth.properties` using the service principal credentials:</span></span>

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

- <span data-ttu-id="4111b-102">subscription: `Login-AzureRmAccount`를 실행할 때 사용했던 *SubscriptionId* 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4111b-102">subscription: use the *SubscriptionId* value from when you ran `Login-AzureRmAccount`.</span></span>
- <span data-ttu-id="4111b-103">client: 서비스 주체 출력의 *ApplicationId* 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4111b-103">client: use the *ApplicationId* value from the service principal output.</span></span>
- <span data-ttu-id="4111b-104">key: `New-AzureRmADServicePrincipal`을 실행할 때 할당한 *-Password* 매개 변수를 사용합니다(따옴표 제외).</span><span class="sxs-lookup"><span data-stu-id="4111b-104">key: use the *-Password* parameter you assigned when you ran `New-AzureRmADServicePrincipal` (without quotes).</span></span>
- <span data-ttu-id="4111b-105">tenant: `Login-AzureRmAccount`를 실행할 때의 *TenantId* 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4111b-105">tenant: use the *TenantId* value from when you ran `Login-AzureRmAccount`.</span></span>

<span data-ttu-id="4111b-106">코드에서 읽을 수 있는 시스템의 안전한 위치에 이 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4111b-106">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="4111b-107">PowerShell을 사용하여 파일에 대한 전체 경로를 포함하여 `AZURE_AUTH_LOCATION`이라는 환경 변수를 설정합니다. 예:</span><span class="sxs-lookup"><span data-stu-id="4111b-107">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.properties", "User")
```
