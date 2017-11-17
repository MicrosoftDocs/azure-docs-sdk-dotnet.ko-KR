---
title: "Azure의 데이터 분석에 대한 .NET 자습서 | Microsoft Docs"
description: "Microsoft Azure 서비스를 사용하여 데이터 분석 응용 프로그램을 개발합니다."
author: camsoper
ms.author: casoper
manager: wpickett
ms.date: 10/19/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.custom: devcenter
ms.openlocfilehash: 44491f7debdc585a52b7455f4eaecd92d39de232
ms.sourcegitcommit: fe3e1475208ba47d4630788bac88b952cc3fe61f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2017
---
# <a name="data-analytics-tutorials-with-net-on-azure"></a><span data-ttu-id="074cd-103">Azure에서 .NET을 사용한 데이터 분석에 대한 자습서</span><span class="sxs-lookup"><span data-stu-id="074cd-103">Data analytics tutorials with .NET on Azure</span></span>

<span data-ttu-id="074cd-104">다음 표에서는 Azure에서 .NET을 사용하여 데이터 분석 솔루션을 개발하는 자세한 자습서로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="074cd-104">The following table links to in-depth tutorials for developing data analytics solutions using .NET on Azure.</span></span> 

<span data-ttu-id="074cd-105">샘플 소스 코드는 [Azure 서비스 샘플](https://azure.microsoft.com/resources/samples/?platform=dotnet) 목록을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="074cd-105">For sample source code, see the list of [Azure service samples](https://azure.microsoft.com/resources/samples/?platform=dotnet).</span></span>

| | |
|---|---|
| <span data-ttu-id="074cd-106">**HDInsight**</span><span class="sxs-lookup"><span data-stu-id="074cd-106">**HDInsight**</span></span> | |
| <span data-ttu-id="074cd-107">[Apache Storm 토폴로지 만들기][1]</span><span class="sxs-lookup"><span data-stu-id="074cd-107">[Create an Apache Storm topology][1]</span></span> | <span data-ttu-id="074cd-108">샘플 앱을 구현하는 토폴로지를 정의한 다음 프로젝트를 빌드하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="074cd-108">Define a topology that implements a sample app, then build and run the project.</span></span> | 
| <span data-ttu-id="074cd-109">[HDInsight의 Storm으로 Azure Event Hubs에서 이벤트 처리][2]</span><span class="sxs-lookup"><span data-stu-id="074cd-109">[Process events from Azure Event Hubs with Storm on HDInsight][2]</span></span> | <span data-ttu-id="074cd-110">HDInsight의 Apache Storm에서 Event Hub Spout를 사용하여 웹 사이트, 앱 및 장치의 데이터를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="074cd-110">Process data from websites, apps, and devices using the Event Hub spout with Apache Storm on HDInsight.</span></span>
| <span data-ttu-id="074cd-111">[MapReduce 앱 개발 및 HDInsight Hadoop 클러스터에서 실행][3]</span><span class="sxs-lookup"><span data-stu-id="074cd-111">[Develop a MapReduce app and run it on a HDInsight Hadoop cluster][3]</span></span> | <span data-ttu-id="074cd-112">간단한 MapReduce 응용 프로그램을 만들어 단어 수를 계산하고, Linux에서 실행되는 HDInsight Hadoop 클러스터에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="074cd-112">Create a simple MapReduce application to count words and deploy it in a HDInsight Hadoop cluster running on Linux.</span></span> |
| <span data-ttu-id="074cd-113">**데이터 레이크 분석**</span><span class="sxs-lookup"><span data-stu-id="074cd-113">**Data Lake Analytics**</span></span> | |
| <span data-ttu-id="074cd-114">[Data Lake Analytics 시작][4]</span><span class="sxs-lookup"><span data-stu-id="074cd-114">[Get started with Data Lake Analytics][4]</span></span> | <span data-ttu-id="074cd-115">Azure .NET SDK를 사용하여 U-SQL로 작성된 작업을 Data Lake Analytics에 제출하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="074cd-115">Learn how to use the Azure .NET SDK to submit jobs written in U-SQL to Data Lake Analytics.</span></span>|


[1]: /azure/hdinsight/hdinsight-storm-develop-csharp-event-hub-topology
[2]: /azure/hdinsight/hdinsight-storm-develop-csharp-visual-studio-topology
[3]: /azure/hdinsight/hdinsight-hadoop-dotnet-csharp-mapreduce-streaming
[4]: /azure/data-lake-analytics/data-lake-analytics-get-started-net-sdk