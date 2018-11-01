---
title: Node.js용 Azure Scheduler 모듈
description: Node.js용 Azure Scheduler 모듈에 대한 참조
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 9a842919fddb3d6448d5a4e951dc58dd0d3211e0
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406479"
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="5f95a-103">Node.js용 Azure Scheduler 모듈</span><span class="sxs-lookup"><span data-stu-id="5f95a-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="5f95a-104">Azure Scheduler는 HTTP, HTTPS, 저장소 큐 또는 [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview)를 통해 예약된 작업을 생성, 유지 관리 및 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="5f95a-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="5f95a-105">[Azure Scheduler](/azure/scheduler/scheduler-intro)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="5f95a-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="5f95a-106">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="5f95a-106">Management package</span></span>

<span data-ttu-id="5f95a-107">관리 API를 사용하여 다양한 통신 채널에서 예약된 작업을 생성, 유지 관리 및 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="5f95a-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5f95a-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="5f95a-108">Install the npm module</span></span>

<span data-ttu-id="5f95a-109">Azure Scheduler npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5f95a-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="5f95a-110">예</span><span class="sxs-lookup"><span data-stu-id="5f95a-110">Example</span></span>

<span data-ttu-id="5f95a-111">이 예제에서는 현재 스케줄러를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="5f95a-111">This examples lists the current schedulers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a><span data-ttu-id="5f95a-112">샘플</span><span class="sxs-lookup"><span data-stu-id="5f95a-112">Samples</span></span>

<span data-ttu-id="5f95a-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="5f95a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
