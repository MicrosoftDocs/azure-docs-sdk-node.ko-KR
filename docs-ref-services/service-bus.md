---
title: Node.js용 Azure Service Bus 모듈
description: Node.js용 Azure Service Bus 모듈에 대한 참조
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 76d7c615cbe64fa38f9c28ea8dfc6d1c854bb0c9
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52089718"
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="bd560-103">Node.js용 Azure Service Bus 모듈</span><span class="sxs-lookup"><span data-stu-id="bd560-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="bd560-104">Azure Service Bus는 분리된 시스템 간에 데이터를 보낼 수 있도록 하는 비동기 메시지 클라우드 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="bd560-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="bd560-105">[Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="bd560-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="bd560-106">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="bd560-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bd560-107">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="bd560-107">Install the npm module</span></span>

<span data-ttu-id="bd560-108">npm을 사용하여 Node.js용 Azure Service Bus 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="bd560-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="bd560-109">예</span><span class="sxs-lookup"><span data-stu-id="bd560-109">Example</span></span>

<span data-ttu-id="bd560-110">이 예제에서는 클라이언트를 만든 다음, 지정된 구독과 연결된 모든 Service Bus 네임스페이스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bd560-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a><span data-ttu-id="bd560-111">샘플</span><span class="sxs-lookup"><span data-stu-id="bd560-111">Samples</span></span>

<span data-ttu-id="bd560-112">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="bd560-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
