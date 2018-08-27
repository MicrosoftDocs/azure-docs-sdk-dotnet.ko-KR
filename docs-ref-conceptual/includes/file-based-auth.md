<span data-ttu-id="66bef-101">`azureauth.json` 이름의 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="66bef-101">Create a text file named `azureauth.json`.</span></span> <span data-ttu-id="66bef-102">서비스 주체를 만들 때의 JSON 출력을 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="66bef-102">Paste the JSON output from when you created the service principal.</span></span>

<span data-ttu-id="66bef-103">코드에서 읽을 수 있는 시스템의 안전한 위치에 JSON 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="66bef-103">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="66bef-104">PowerShell을 사용하여 파일에 대한 전체 경로를 포함하여 `AZURE_AUTH_LOCATION`이라는 환경 변수를 설정합니다. 예:</span><span class="sxs-lookup"><span data-stu-id="66bef-104">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
