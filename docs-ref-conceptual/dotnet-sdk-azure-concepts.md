---
title: ".NET 사용 개념 및 패턴에 대한 Azure 관리 라이브러리"
description: 
keywords: "Azure, .NET, SDK, API, 패턴, 개념, 흐름, 로깅"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.assetid: 
ms.openlocfilehash: b2e6849f06c36de18471e55c468e984f4205f646
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-management-library-for-net-fluent-concepts"></a>.NET 흐름 개념에 대한 Azure 관리 라이브러리

이 문서는 .NET용 Azure 관리 라이브러리에서 흐름 인터페이스를 효과적으로 사용하는 방법을 이해하는 데 도움이 됩니다.

## <a name="building-resources-using-a-fluent-interface"></a>흐름 인터페이스를 사용하여 리소스 빌드

흐름 인터페이스는 리소스의 올바른 구성을 적용하는 메서드 체인을 통해 개체를 만드는 작성기 패턴의 특정 형태입니다. 예를 들어 Azure 끝점 개체는 흐름 인터페이스를 사용하여 만들어집니다.

```csharp
var azure = Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

## <a name="resource-collections"></a>리소스 컬렉션

위에 표시된 `Microsoft.Azure.Management.Fluent.Azure` 개체는 흐름 관리 라이브러리에서 모든 리소스 만들기에 대한 진입점입니다. `Azure` 개체의 리소스 컬렉션 메서드를 사용하여 작업할 리소스 종류를 선택합니다. 예를 들어 SQL Database의 경우 다음과 같습니다.

```csharp
var sql = azure.SqlServers.Define(sqlServerName)
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName)
    .WithAdministratorLogin(administratorLogin)
    .WithAdministratorPassword(administratorPassword)
    .Create();
```

위에서 보여 주듯이 API를 사용하는 대부분의 흐름 "대화"는 작업해야 하는 Azure 리소스에 적절한 리소스 컬렉션을 선택하는 것으로 시작됩니다.  그런 다음 Visual Studio의 Intellisense에서 대화를 안내합니다. 

![흐름 대화를 구동하는 Visual Studio의 Intellisense에 대한 GIF](media/dotnet-sdk-azure-concepts/vs-fluent.gif)   

## <a name="lists-and-iterations"></a>목록 및 반복

각 리소스 컬렉션에는 현재 구독에 있는 해당 리소스의 모든 인스턴스를 반환하는 `List()` 메서드가 있습니다. 예를 들어 `Azure.SqlServers.List()`는 구독의 모든 SQL 서버를 반환합니다.

`ListByResourceGroup()` 메서드를 사용하여 반환된 List의 범위를 특정 [Azure 리소스 그룹](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups)으로 지정합니다.  

일반 `List<T>`와 마찬가지로 반환된 컬렉션을 반복합니다.

```csharp
var vmList = azure.VirtualMachines.List();
foreach(var vm in vmList)
{
    Console.WriteLine("VM Name: {0}", vm.Name);
}
```   

## <a name="actionable-verbs"></a>실행 가능한 동사

이름에 동사가 있는 리소스 컬렉션 메서드는 Azure에서 즉시로 작업을 수행합니다. 이러한 메서드는 동기적으로 작동하고 완료될 때까지 현재 스레드의 실행을 차단합니다. 

| 동사   |  샘플 사용 |
|--------|---------------|
| 생성 | `azure.VirtualMachines.Create(listOfVMCreatables)` |
| 적용  | `virtualMachineScaleSet.Update().WithCapacity(6).Apply()` |
| 삭제 | `azure.Disks.DeleteById(id)` | 
| 나열   | `azure.SqlServers.List()` | 
| 가져오기    | `var vm  = azure.VirtualMachines.GetByResourceGroup(group, vmName)` |

>[!NOTE]
> `Define()` 및 `Update()`는 동사이지만 `Create()` 또는 `Apply()`가 뒤에 나오지 않으면 차단하지 않습니다.
 
일부 리소스 개체에는 Azure에서 리소스의 상태를 변경하는 동사가 있습니다. 예:

```csharp
var vmToRestart = azure.VirtualMachines.GetById(id);
vmToRestart.Restart();
```

이 섹션에서 설명하는 대부분의 메서드에는 비동기 버전(`Async` 접미사로 표시됨)도 있습니다.

```csharp
Task restartTask = azure.VirtualMachines.GetById(id).RestartAsync();
```

## <a name="lazy-resource-creation"></a>지연 리소스 만들기

Azure 리소스를 만들 때 새 리소스가 아직 존재하지 않는 다른 리소스에 종속되면 문제가 발생합니다. 한 예로, 새 가상 컴퓨터를 만들 때 공용 IP 주소를 예약하고 디스크를 설정합니다. 주소 예약 또는 디스크 만들기를 확인하지 않으려는 경우 이러한 리소스로 가상 컴퓨터를 구성하기만 하면 됩니다.

만들 수 있는(Creatable) 개체를 사용하여 코드에서 사용할 Azure 리소스를 정의하지만 Azure에서 필요할 때만 만듭니다. 만들 수 있는 개체로 작성된 코드는 Azure 환경의 리소스 만들기를 관리 API로 오프로드하여 성능을 향상시킵니다. 

`Create()` 동사 없이 리소스 컬렉션의 `Define()` 동사를 통해 만들 수 있는 개체를 생성하는 예제는 다음과 같습니다.

```csharp
// Init a creatable Public IP Address
var publicIpAddressCreatable = azure.PublicIPAddresses.Define("publicIPAddressName")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup(rgName);
```

만들 수 있는 개체에서 정의된 Azure 리소스는 아직 구독에 존재하지 않습니다. 만들 수 있는 개체는 필요할 때(`.Create()`가 호출될 때) 관리 API에서 만드는 리소스의 로컬 표현입니다. 이 리소스가 필요한 다른 Azure 리소스의 정의에서 이 만들 수 있는 개체를 사용합니다. 

```csharp
// Init a creatable VM using the creatable Public IP Address
var vmCreatable = azure.VirtualMachines.Define("creatableVM")
    // ...
    .withNewPrimaryPublicIPAddress(publicIPAddressCreatable)
    // ...
```

리소스 컬렉션에 `Create()` 메서드를 사용하여 Azure 구독에 리소스를 만듭니다. 

```csharp
// Create the VM and its Public IP Address
var virtualMachine = azure.VirtualMachines.Create(vmCreatable);
```

만들 수 있는 개체를 `Create()`에 전달하면 단일 리소스 개체 대신 `ICreatedResources` 개체가 반환됩니다.  `CreatedRelatedResource` 개체를 사용하면 리소스 컬렉션의 형식 외에도 `Create()` 호출로 만든 모든 리소스에 액세스할 수 있습니다. 위의 예제에서 만든 가상 컴퓨터에 대해 Azure에서 만든 공용 IP 주소에 액세스하려면 다음을 수행합니다.

```csharp
var pip = virtualMachine.CreatedRelatedResource(publicIPAddressCreatable.Key()) as PublicIPAddress;;
```    

## <a name="exception-handling"></a>예외 처리

관리 API에서 `Microsoft.Rest.RestException`을 확장하는 예외 클래스를 정의합니다. 관련된 `try` 문 뒤에 `catch (RestException exception)` 블록이 있는 관리 API에서 생성된 예외를 catch합니다.

## <a name="logs-and-tracing"></a>로그 및 추적

.NET용 흐름 Azure 관리 라이브러리의 로깅에서는 기본 [AutoRest](https://github.com/Azure/AutoRest) 서비스 클라이언트 추적을 활용합니다.

`Microsoft.Rest.IServiceClientTracingInterceptor`를 구현하는 클래스를 만듭니다.  이 클래스는 로그 메시지를 가로채 사용 중인 모든 로깅 메커니즘에 전달합니다.  이 예제에서는 콘솔에 메시지를 쓰지만, Log4Net, `Microsoft.Extensions.Logging` 또는 다른 로깅 프레임워크로 전달할 수도 있습니다.

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

`Microsoft.Azure.Management.Fluent.Azure` 개체를 만들기 전에 `ServiceClientTracing.AddTracingInterceptor()`를 호출하여 위에 만든 `IServiceClientTracingInterceptor`를 초기화하고 `ServiceClientTracing.IsEnabled`를 *true*로 설정합니다.  `Azure` 개체를 만들 때 `.WithDelegatingHandler()` 및 `.WithLogLevel()` 메서드를 포함하여 클라이언트를 AutoRest의 서비스 클라이언트 추적에 연결합니다.

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

`HttpLoggingDelegatingHandler` 로그 수준은 다음과 같이 정의됩니다.

| 추적 수준 | 사용되는 로깅 
| ------------ | ---------------
| HttpLoggingDelegatingHandler.Level.None | 출력 없음
| HttpLoggingDelegatingHandler.Level.Basic | 기본 REST 호출, 응답 코드 및 시간에 URL을 기록합니다.
| HttpLoggingDelegatingHandler.Level.Body | Basic의 모든 항목 및 REST 호출에 대한 요청/응답 본문
| HttpLoggingDelegatingHandler.Level.Headers | Basic의 모든 항목 및 REST 호출에 대한 요청/응답 헤더
| HttpLoggingDelegatingHandler.Level.BodyAndHeaders | Body 및 Headers 로그 수준 둘 다의 모든 항목
