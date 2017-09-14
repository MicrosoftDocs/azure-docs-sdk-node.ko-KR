---
title: "Node.js용 Azure Event Hub 모듈"
description: "Node.js용 Azure Event Hub 모듈에 대한 참조"
keywords: Azure, SDK, API, Event Hub, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: 5ac6fc3f86419602756c354393078b399a6cba23
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="b6472-104">Node.js용 Azure Event Hub 모듈</span><span class="sxs-lookup"><span data-stu-id="b6472-104">Azure Event Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b6472-105">개요</span><span class="sxs-lookup"><span data-stu-id="b6472-105">Overview</span></span>
<span data-ttu-id="b6472-106">Azure Event Hubs는 초당 수백만 개의 이벤트를 수신하고 처리할 수 있는 확장성이 뛰어난 데이터 스트리밍 플랫폼 및 이벤트 수집 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="b6472-106">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="b6472-107">Event Hubs는 분산된 소프트웨어와 장치에서 생성된 이벤트, 데이터 또는 원격 분석을 처리하고 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6472-107">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="b6472-108">Event Hub로 전송된 데이터는 실시간 분석 공급자 또는 일괄 처리/저장소 어댑터를 사용하여 변환하고 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6472-108">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="b6472-109">짧은 대기 시간과 엄청난 규모로 게시-구독 기능을 제공하는 기능을 사용하여 이벤트 허브는 빅 데이터에 대해 "램프"로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b6472-109">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="b6472-110">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="b6472-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b6472-111">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="b6472-111">Install the npm module</span></span> 

<span data-ttu-id="b6472-112">npm을 사용하여 Node.js용 Azure Event Hub 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b6472-112">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="b6472-113">예제</span><span class="sxs-lookup"><span data-stu-id="b6472-113">Example</span></span>

<span data-ttu-id="b6472-114">이 예제에서는 기존 이벤트 허브에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b6472-114">This example retrieves information about an existing event hub.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b6472-115">샘플</span><span class="sxs-lookup"><span data-stu-id="b6472-115">Samples</span></span>

<span data-ttu-id="b6472-116">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="b6472-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
