---
<span data-ttu-id="c256e-101">uid: Microsoft.Azure.Management.Compute.VirtualMachinesOperationsExtensions.Capture(Microsoft.Azure.Management.Compute.IVirtualMachinesOperations,System.String,System.String,Microsoft.Azure.Management.Compute.Models.VirtualMachineCaptureParameters) 요약: \*콘텐츠</span><span class="sxs-lookup"><span data-stu-id="c256e-101">uid: Microsoft.Azure.Management.Compute.VirtualMachinesOperationsExtensions.Capture(Microsoft.Azure.Management.Compute.IVirtualMachinesOperations,System.String,System.String,Microsoft.Azure.Management.Compute.Models.VirtualMachineCaptureParameters) summary: \*content</span></span>
---

<span data-ttu-id="c256e-102">덮어쓰기 파일 메서드에 의해 삽입된 콘텐츠는 다음과 같습니다. 따라서 작성자가 API 설명서를 Markown 형식으로 생성하려는 만큼 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c256e-102">Here is content that is injected by the overwrite file method, so writers can add as much as they want to the generated API documentation in Markown format.</span></span>

---
<span data-ttu-id="c256e-103">uid: Microsoft.Azure.Management.Compute.VirtualMachinesOperationsExtensions.Capture(Microsoft.Azure.Management.Compute.IVirtualMachinesOperations,System.String,System.String,Microsoft.Azure.Management.Compute.Models.VirtualMachineCaptureParameters) 표시: \*콘텐츠</span><span class="sxs-lookup"><span data-stu-id="c256e-103">uid: Microsoft.Azure.Management.Compute.VirtualMachinesOperationsExtensions.Capture(Microsoft.Azure.Management.Compute.IVirtualMachinesOperations,System.String,System.String,Microsoft.Azure.Management.Compute.Models.VirtualMachineCaptureParameters) remarks: \*content</span></span>
---

<span data-ttu-id="c256e-104">아래 코드는 Azure .NET SDK를 사용하여 캡처 메서드를 호출하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c256e-104">The code below demonstrates how to call the Capture method using the Azure .NET SDK.</span></span> 

```csharp
using Microsoft.Azure.Management.Compute;
using Microsoft.Azure.Management.Compute.Models;
using Microsoft.Rest;

namespace MyAzureVmClientApp
{
    class Program
    {
        static void Main(string[] args)
        {
            var token = "[Token Obtained from ADAL]";

            var credential = new TokenCredentials(token);

            var captureResponse = 
                new ComputeManagementClient(credential)
                .VirtualMachines
                    .Capture(
                        "myResourceGroup",
                        "myVmName",
                        new VirtualMachineCaptureParameters
                        {
                            DestinationContainerName = "myblobcontainer",
                            OverwriteVhds = true,
                            VhdPrefix = "backup"
                        });
        }
    }
}
```

