---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: 7f7c24957d2bc0574fc0b1bf2a8ae8fe8b4dfc64
ms.sourcegitcommit: e534dad2d96b72ab6a9bc4b5567508962bd7e05c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58343342"
---
<span data-ttu-id="c7cf6-101">`azureauth.json` 이름의 텍스트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7cf6-101">Create a text file named `azureauth.json`.</span></span> <span data-ttu-id="c7cf6-102">서비스 주체를 만들 때의 JSON 출력을 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c7cf6-102">Paste the JSON output from when you created the service principal.</span></span>

<span data-ttu-id="c7cf6-103">코드에서 읽을 수 있는 시스템의 안전한 위치에 JSON 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c7cf6-103">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="c7cf6-104">PowerShell을 사용하여 파일에 대한 전체 경로를 포함하여 `AZURE_AUTH_LOCATION`이라는 환경 변수를 설정합니다. 예:</span><span class="sxs-lookup"><span data-stu-id="c7cf6-104">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
