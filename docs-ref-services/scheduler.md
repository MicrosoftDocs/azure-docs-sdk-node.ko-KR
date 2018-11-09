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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51122082"
---
# <a name="azure-scheduler-modules-for-nodejs"></a>Node.js용 Azure Scheduler 모듈

Azure Scheduler는 HTTP, HTTPS, 저장소 큐 또는 [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview)를 통해 예약된 작업을 생성, 유지 관리 및 호출합니다.

[Azure Scheduler](/azure/scheduler/scheduler-intro)에 대해 자세히 알아보세요.

## <a name="management-package"></a>관리 패키지

관리 API를 사용하여 다양한 통신 채널에서 예약된 작업을 생성, 유지 관리 및 호출합니다.

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure Scheduler npm 모듈을 설치합니다.

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a>예

이 예제에서는 현재 스케줄러를 나열합니다.

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

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
