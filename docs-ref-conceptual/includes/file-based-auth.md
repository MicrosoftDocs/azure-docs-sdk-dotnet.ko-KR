`azureauth.json` 이름의 텍스트 파일을 만듭니다. 서비스 주체를 만들 때의 JSON 출력을 붙여넣습니다.

코드에서 읽을 수 있는 시스템의 안전한 위치에 JSON 파일을 저장합니다. PowerShell을 사용하여 파일에 대한 전체 경로를 포함하여 `AZURE_AUTH_LOCATION`이라는 환경 변수를 설정합니다. 예:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
