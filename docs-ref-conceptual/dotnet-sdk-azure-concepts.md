---
title: ".NET 사용 개념 및 패턴에 대한 Azure 관리 라이브러리"
description: 
keywords: "Azure, .NET, SDK, API, 패턴, 개념, 흐름, 로깅"
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: b817216e114e5ab3ff22c1c5adb0f892c7874147
ms.sourcegitcommit: 3ba0ff4463338a0ab0f3f15a7601b89417c06970
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2018
---
# <a name="azure-management-library-for-net-fluent-concepts"></a><span data-ttu-id="55a32-103">.NET 흐름 개념에 대한 Azure 관리 라이브러리</span><span class="sxs-lookup"><span data-stu-id="55a32-103">Azure management library for .NET fluent concepts</span></span>

<span data-ttu-id="55a32-104">이 문서는 .NET용 Azure 관리 라이브러리에서 흐름 인터페이스를 효과적으로 사용하는 방법을 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-104">This article will help you understand how to effectively use the fluent interface in the Azure management libraries for .NET.</span></span>

## <a name="building-resources-using-a-fluent-interface"></a><span data-ttu-id="55a32-105">흐름 인터페이스를 사용하여 리소스 빌드</span><span class="sxs-lookup"><span data-stu-id="55a32-105">Building resources using a fluent interface</span></span>

<span data-ttu-id="55a32-106">흐름 인터페이스는 리소스의 올바른 구성을 적용하는 메서드 체인을 통해 개체를 만드는 작성기 패턴의 특정 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-106">A fluent interface is a specific form of the builder pattern that creates objects through a method chain that enforces correct configuration of a resource.</span></span> <span data-ttu-id="55a32-107">예를 들어 Azure 끝점 개체는 흐름 인터페이스를 사용하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-107">For example, the entry-point Azure object is created using a fluent interface:</span></span>

```csharp
var azure = Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

## <a name="resource-collections"></a><span data-ttu-id="55a32-108">리소스 컬렉션</span><span class="sxs-lookup"><span data-stu-id="55a32-108">Resource collections</span></span>

<span data-ttu-id="55a32-109">위에 표시된 `Microsoft.Azure.Management.Fluent.Azure` 개체는 흐름 관리 라이브러리에서 모든 리소스 만들기에 대한 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-109">The `Microsoft.Azure.Management.Fluent.Azure` object shown above is the entry point for all resource creation in the fluent management libraries.</span></span> <span data-ttu-id="55a32-110">`Azure` 개체의 리소스 컬렉션 메서드를 사용하여 작업할 리소스 종류를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-110">Select which type of resources to work with using the resource collections in the `Azure` object.</span></span> <span data-ttu-id="55a32-111">예를 들어 SQL Database의 경우 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-111">For example, for SQL Database:</span></span>

```csharp
var sql = azure.SqlServers.Define(sqlServerName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithAdministratorLogin(administratorLogin)
    .WithAdministratorPassword(administratorPassword)
    .Create();
```

<span data-ttu-id="55a32-112">위에서 보여 주듯이 API를 사용하는 대부분의 흐름 "대화"는 작업해야 하는 Azure 리소스에 적절한 리소스 컬렉션을 선택하는 것으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-112">As seen above, most fluent "conversations" you have with the API start with selecting the appropriate resource collection for the Azure resources you need to work with.</span></span>  <span data-ttu-id="55a32-113">그런 다음 Visual Studio의 Intellisense에서 대화를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-113">Intellisense in Visual Studio then guides you through the conversation.</span></span> 

![흐름 대화를 구동하는 Visual Studio의 Intellisense에 대한 GIF](media/dotnet-sdk-azure-concepts/vs-fluent.gif)   

## <a name="lists-and-iterations"></a><span data-ttu-id="55a32-115">목록 및 반복</span><span class="sxs-lookup"><span data-stu-id="55a32-115">Lists and iterations</span></span>

<span data-ttu-id="55a32-116">각 리소스 컬렉션에는 현재 구독에 있는 해당 리소스의 모든 인스턴스를 반환하는 `List()` 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-116">Every resource collection has a `List()` method to return every instance of that resource in your current subscription.</span></span> <span data-ttu-id="55a32-117">예를 들어 `Azure.SqlServers.List()`는 구독의 모든 SQL 서버를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-117">For example, `Azure.SqlServers.List()` returns all SQL servers in the subscription.</span></span>

<span data-ttu-id="55a32-118">`ListByResourceGroup()` 메서드를 사용하여 반환된 List의 범위를 특정 [Azure 리소스 그룹](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups)으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-118">Use the `ListByResourceGroup()` method to scope the returned List to a specific [Azure resource group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups).</span></span>  

<span data-ttu-id="55a32-119">일반 `List<T>`와 마찬가지로 반환된 컬렉션을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-119">Iterate over the returned collection just as you would a normal `List<T>`:</span></span>

```csharp
var vmList = azure.VirtualMachines.List();
foreach(var vm in vmList)
{
    Console.WriteLine("VM Name: {0}", vm.Name);
}
```   

## <a name="actionable-verbs"></a><span data-ttu-id="55a32-120">실행 가능한 동사</span><span class="sxs-lookup"><span data-stu-id="55a32-120">Actionable verbs</span></span>

<span data-ttu-id="55a32-121">이름에 동사가 있는 리소스 컬렉션 메서드는 Azure에서 즉시로 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-121">Resource collection methods with verbs in their names take immediate action in Azure.</span></span> <span data-ttu-id="55a32-122">이러한 메서드는 동기적으로 작동하고 완료될 때까지 현재 스레드의 실행을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-122">These methods work synchronously and block execution in the current thread until they complete.</span></span> 

| <span data-ttu-id="55a32-123">동사</span><span class="sxs-lookup"><span data-stu-id="55a32-123">Verb</span></span>   |  <span data-ttu-id="55a32-124">샘플 사용</span><span class="sxs-lookup"><span data-stu-id="55a32-124">Sample usage</span></span> |
|--------|---------------|
| <span data-ttu-id="55a32-125">생성</span><span class="sxs-lookup"><span data-stu-id="55a32-125">Create</span></span> | `azure.VirtualMachines.Create(listOfVMCreatables)` |
| <span data-ttu-id="55a32-126">적용</span><span class="sxs-lookup"><span data-stu-id="55a32-126">Apply</span></span>  | `virtualMachineScaleSet.Update().WithCapacity(6).Apply()` |
| <span data-ttu-id="55a32-127">삭제</span><span class="sxs-lookup"><span data-stu-id="55a32-127">Delete</span></span> | `azure.Disks.DeleteById(id)` | 
| <span data-ttu-id="55a32-128">나열</span><span class="sxs-lookup"><span data-stu-id="55a32-128">List</span></span>   | `azure.SqlServers.List()` | 
| <span data-ttu-id="55a32-129">가져오기</span><span class="sxs-lookup"><span data-stu-id="55a32-129">Get</span></span>    | `var vm  = azure.VirtualMachines.GetByResourceGroup(group, vmName)` |

>[!NOTE]
> <span data-ttu-id="55a32-130">`Define()` 및 `Update()`는 동사이지만 `Create()` 또는 `Apply()`가 뒤에 나오지 않으면 차단하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-130">`Define()` and `Update()` are verbs but do not block unless followed by a `Create()` or `Apply()`.</span></span>
 
<span data-ttu-id="55a32-131">일부 리소스 개체에는 Azure에서 리소스의 상태를 변경하는 동사가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-131">Specific resource objects have verbs that change the state of the resource in Azure.</span></span> <span data-ttu-id="55a32-132">예: </span><span class="sxs-lookup"><span data-stu-id="55a32-132">For example:</span></span>

```csharp
var vmToRestart = azure.VirtualMachines.GetById(id);
vmToRestart.Restart();
```

<span data-ttu-id="55a32-133">이 섹션에서 설명하는 대부분의 메서드에는 비동기 버전(`Async` 접미사로 표시됨)도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-133">Most of the methods described in this section have an asynchronous version as well, denoted by the suffix `Async`.</span></span>

```csharp
Task restartTask = azure.VirtualMachines.GetById(id).RestartAsync();
```

## <a name="lazy-resource-creation"></a><span data-ttu-id="55a32-134">지연 리소스 만들기</span><span class="sxs-lookup"><span data-stu-id="55a32-134">Lazy resource creation</span></span>

<span data-ttu-id="55a32-135">Azure 리소스를 만들 때 새 리소스가 아직 존재하지 않는 다른 리소스에 종속되면 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-135">A challenge when creating Azure resources arises when a new resource depends on another resource that doesn't yet exist.</span></span> <span data-ttu-id="55a32-136">한 예로, 새 가상 머신을 만들 때 공용 IP 주소를 예약하고 디스크를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-136">An example is reserving a public IP address and setting up a disk when creating a new virtual machine.</span></span> <span data-ttu-id="55a32-137">주소 예약 또는 디스크 만들기를 확인하지 않으려는 경우 이러한 리소스로 가상 머신을 구성하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-137">You don't want to verify reserving the address or the creating the disk, you just want to configure the virtual machine with those resources.</span></span>

<span data-ttu-id="55a32-138">만들 수 있는(Creatable) 개체를 사용하여 코드에서 사용할 Azure 리소스를 정의하지만 Azure에서 필요할 때만 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-138">Use creatable objects to define Azure resources for use in your code but only create them when needed in Azure.</span></span> <span data-ttu-id="55a32-139">만들 수 있는 개체로 작성된 코드는 Azure 환경의 리소스 만들기를 관리 API로 오프로드하여 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-139">Code written with creatable objects offloads resource creation in the Azure environment to the management API, boosting performance.</span></span> 

<span data-ttu-id="55a32-140">`Create()` 동사 없이 리소스 컬렉션의 `Define()` 동사를 통해 만들 수 있는 개체를 생성하는 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-140">Generate creatable objects through the resource collections' `Define()` verb without a `Create()` verb:</span></span>

```csharp
// Init a creatable Public IP Address
var publicIpAddressCreatable = azure.PublicIPAddresses.Define("publicIPAddressName")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName);
```

<span data-ttu-id="55a32-141">만들 수 있는 개체에서 정의된 Azure 리소스는 아직 구독에 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-141">The Azure resource defined by the creatable object does not yet exist in your subscription.</span></span> <span data-ttu-id="55a32-142">만들 수 있는 개체는 필요할 때(`.Create()`가 호출될 때) 관리 API에서 만드는 리소스의 로컬 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-142">A creatable object is a local representation of a resource that the management API will create when it's needed (when `.Create()` is called).</span></span> <span data-ttu-id="55a32-143">이 리소스가 필요한 다른 Azure 리소스의 정의에서 이 만들 수 있는 개체를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-143">Use this creatable object in the definition of other Azure resources that need this resource.</span></span> 

```csharp
// Init a creatable VM using the creatable Public IP Address
var vmCreatable = azure.VirtualMachines.Define("creatableVM")
    // ...
    .withNewPrimaryPublicIPAddress(publicIPAddressCreatable)
    // ...
```

<span data-ttu-id="55a32-144">리소스 컬렉션에 `Create()` 메서드를 사용하여 Azure 구독에 리소스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-144">Create the resources in your Azure subscription using the `Create()` method for the resource collection.</span></span> 

```csharp
// Create the VM and its Public IP Address
var virtualMachine = azure.VirtualMachines.Create(vmCreatable);
```

<span data-ttu-id="55a32-145">만들 수 있는 개체를 `Create()`에 전달하면 단일 리소스 개체 대신 `ICreatedResources` 개체가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-145">Passing creatable objects to `Create()` returns a `ICreatedResources` object instead of a single resource object.</span></span>  <span data-ttu-id="55a32-146">`CreatedRelatedResource` 개체를 사용하면 리소스 컬렉션의 형식 외에도 `Create()` 호출로 만든 모든 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-146">The `CreatedRelatedResource` object lets you access all resources created by the `Create()` call, not just the type from the resource collection.</span></span> <span data-ttu-id="55a32-147">위의 예제에서 만든 가상 머신에 대해 Azure에서 만든 공용 IP 주소에 액세스하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-147">To access the public IP address created in Azure for the virtual machine created in the above example:</span></span>

```csharp
var pip = virtualMachine.CreatedRelatedResource(publicIPAddressCreatable.Key()) as PublicIPAddress;;
```    

## <a name="exception-handling"></a><span data-ttu-id="55a32-148">예외 처리</span><span class="sxs-lookup"><span data-stu-id="55a32-148">Exception handling</span></span>

<span data-ttu-id="55a32-149">관리 API에서 `Microsoft.Rest.RestException`을 확장하는 예외 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-149">The management API defines exception classes that extend `Microsoft.Rest.RestException`.</span></span> <span data-ttu-id="55a32-150">관련된 `try` 문 뒤에 `catch (RestException exception)` 블록이 있는 관리 API에서 생성된 예외를 catch합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-150">Catch exceptions generated by management API, with a `catch (RestException exception)` block after the relevant `try` statement.</span></span>

## <a name="logs-and-tracing"></a><span data-ttu-id="55a32-151">로그 및 추적</span><span class="sxs-lookup"><span data-stu-id="55a32-151">Logs and tracing</span></span>

<span data-ttu-id="55a32-152">.NET용 흐름 Azure 관리 라이브러리의 로깅에서는 기본 [AutoRest](https://github.com/Azure/AutoRest) 서비스 클라이언트 추적을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-152">Logging in the fluent Azure management libraries for .NET leverages the underlying [AutoRest](https://github.com/Azure/AutoRest) service client tracing.</span></span>

<span data-ttu-id="55a32-153">`Microsoft.Rest.IServiceClientTracingInterceptor`를 구현하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-153">Create a class that implements `Microsoft.Rest.IServiceClientTracingInterceptor`.</span></span>  <span data-ttu-id="55a32-154">이 클래스는 로그 메시지를 가로채 사용 중인 모든 로깅 메커니즘에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-154">This class will be responsible for intercepting log messages and passing them to whatever logging mechanism you're using.</span></span>  <span data-ttu-id="55a32-155">이 예제에서는 콘솔에 메시지를 쓰지만, Log4Net, `Microsoft.Extensions.Logging` 또는 다른 로깅 프레임워크로 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-155">In this example, we're just writing messages to the console, but you could also pass them to Log4Net, `Microsoft.Extensions.Logging`, or any other logging framework.</span></span>

```csharp
class ConsoleTracer : IServiceClientTracingInterceptor
{
    public void Information(string message)
    {
        Console.WriteLine(message);
    }

    public void TraceError(string invocationId, Exception exception)
    {
        Console.WriteLine("Exception in {0}: {1}", invocationId, exception);
    }

    public void ReceiveResponse(string invocationId, HttpResponseMessage response) { }

    public void SendRequest(string invocationId, HttpRequestMessage request) { }

    public void Configuration(string source, string name, string value) { }

    public void EnterMethod(string invocationId, object instance, string method, IDictionary<string, object> parameters) { }

    public void ExitMethod(string invocationId, object returnValue) { }
}
```

<span data-ttu-id="55a32-156">`Microsoft.Azure.Management.Fluent.Azure` 개체를 만들기 전에 `ServiceClientTracing.AddTracingInterceptor()`를 호출하여 위에 만든 `IServiceClientTracingInterceptor`를 초기화하고 `ServiceClientTracing.IsEnabled`를 *true*로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-156">Before creating the `Microsoft.Azure.Management.Fluent.Azure` object, initialize the `IServiceClientTracingInterceptor` you created above by calling `ServiceClientTracing.AddTracingInterceptor()` and set `ServiceClientTracing.IsEnabled` to *true*.</span></span>  <span data-ttu-id="55a32-157">`Azure` 개체를 만들 때 `.WithDelegatingHandler()` 및 `.WithLogLevel()` 메서드를 포함하여 클라이언트를 AutoRest의 서비스 클라이언트 추적에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-157">When you create the `Azure` object, include the `.WithDelegatingHandler()` and `.WithLogLevel()` methods to wire up the client to AutoRest's service client tracing.</span></span>

```csharp
ServiceClientTracing.AddTracingInterceptor(new ConsoleTracer());
ServiceClientTracing.IsEnabled = true;

var azure = Azure
    .Configure()
    .WithDelegatingHandler(new HttpLoggingDelegatingHandler())
    .WithLogLevel(HttpLoggingDelegatingHandler.Level.Basic)
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

<span data-ttu-id="55a32-158">`HttpLoggingDelegatingHandler` 로그 수준은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-158">The `HttpLoggingDelegatingHandler` log levels are defined as follows:</span></span>

| <span data-ttu-id="55a32-159">추적 수준</span><span class="sxs-lookup"><span data-stu-id="55a32-159">Trace level</span></span> | <span data-ttu-id="55a32-160">사용되는 로깅</span><span class="sxs-lookup"><span data-stu-id="55a32-160">Logging enabled</span></span> 
| ------------ | ---------------
| <span data-ttu-id="55a32-161">HttpLoggingDelegatingHandler.Level.None</span><span class="sxs-lookup"><span data-stu-id="55a32-161">HttpLoggingDelegatingHandler.Level.None</span></span> | <span data-ttu-id="55a32-162">출력 없음</span><span class="sxs-lookup"><span data-stu-id="55a32-162">No output</span></span>
| <span data-ttu-id="55a32-163">HttpLoggingDelegatingHandler.Level.Basic</span><span class="sxs-lookup"><span data-stu-id="55a32-163">HttpLoggingDelegatingHandler.Level.Basic</span></span> | <span data-ttu-id="55a32-164">기본 REST 호출, 응답 코드 및 시간에 URL을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="55a32-164">Logs the URLs to underlying REST calls, response codes and times</span></span>
| <span data-ttu-id="55a32-165">HttpLoggingDelegatingHandler.Level.Body</span><span class="sxs-lookup"><span data-stu-id="55a32-165">HttpLoggingDelegatingHandler.Level.Body</span></span> | <span data-ttu-id="55a32-166">Basic의 모든 항목 및 REST 호출에 대한 요청/응답 본문</span><span class="sxs-lookup"><span data-stu-id="55a32-166">Everything in Basic plus request and response bodies for the REST calls</span></span>
| <span data-ttu-id="55a32-167">HttpLoggingDelegatingHandler.Level.Headers</span><span class="sxs-lookup"><span data-stu-id="55a32-167">HttpLoggingDelegatingHandler.Level.Headers</span></span> | <span data-ttu-id="55a32-168">Basic의 모든 항목 및 REST 호출에 대한 요청/응답 헤더</span><span class="sxs-lookup"><span data-stu-id="55a32-168">Everything in Basic plus the request and response headers REST calls</span></span>
| <span data-ttu-id="55a32-169">HttpLoggingDelegatingHandler.Level.BodyAndHeaders</span><span class="sxs-lookup"><span data-stu-id="55a32-169">HttpLoggingDelegatingHandler.Level.BodyAndHeaders</span></span> | <span data-ttu-id="55a32-170">Body 및 Headers 로그 수준 둘 다의 모든 항목</span><span class="sxs-lookup"><span data-stu-id="55a32-170">Everything in both Body and Headers log level</span></span>
