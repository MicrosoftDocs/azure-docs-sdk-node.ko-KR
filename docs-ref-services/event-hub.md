---
title: Node.js용 Azure Event Hub 모듈
description: Node.js용 Azure Event Hub 모듈에 대한 참조
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: ff167e911b68b82b880e792e7ff2649cbe5af342
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="48e29-103">Node.js용 Azure Event Hub 모듈</span><span class="sxs-lookup"><span data-stu-id="48e29-103">Azure Event Hub modules for Node.js</span></span>

<span data-ttu-id="48e29-104">Azure Event Hubs는 초당 수백만 개의 이벤트를 수신하고 처리할 수 있는 확장성이 뛰어난 데이터 스트리밍 플랫폼 및 이벤트 수집 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="48e29-104">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="48e29-105">Event Hubs는 분산된 소프트웨어와 장치에서 생성된 이벤트, 데이터 또는 원격 분석을 처리하고 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e29-105">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="48e29-106">Event Hub로 전송된 데이터는 실시간 분석 공급자 또는 일괄 처리/저장소 어댑터를 사용하여 변환하고 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e29-106">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="48e29-107">짧은 대기 시간과 엄청난 규모로 게시-구독 기능을 제공하는 기능을 사용하여 Event Hubs는 빅 데이터에 대해 "램프"로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="48e29-107">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="48e29-108">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="48e29-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="48e29-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="48e29-109">Install the npm module</span></span> 

<span data-ttu-id="48e29-110">npm을 사용하여 Node.js용 Azure Event Hub 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="48e29-110">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="48e29-111">예</span><span class="sxs-lookup"><span data-stu-id="48e29-111">Example</span></span>

<span data-ttu-id="48e29-112">이 예제에서는 기존 이벤트 허브에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="48e29-112">This example retrieves information about an existing event hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="48e29-113">샘플</span><span class="sxs-lookup"><span data-stu-id="48e29-113">Samples</span></span>

<span data-ttu-id="48e29-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="48e29-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
