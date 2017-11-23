---
title: "Node.js용 Azure Service Fabric 모듈"
description: "Node.js용 Azure Service Fabric 모듈에 대한 참조"
keywords: Azure, SDK, API, Service Fabric, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: d3de9af4e8ca834963cf2ac0275ed02b8021f29f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="a0744-104">Node.js용 Azure Service Fabric 모듈</span><span class="sxs-lookup"><span data-stu-id="a0744-104">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a0744-105">개요</span><span class="sxs-lookup"><span data-stu-id="a0744-105">Overview</span></span>

<span data-ttu-id="a0744-106">Azure Service Fabric은 손쉽게 패키지하고 배포하며 확장 가능하고 안정성이 뛰어난 마이크로 서비스 및 컨테이너를 관리하도록 배포된 시스템 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="a0744-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="a0744-107">[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="a0744-107">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="a0744-108">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="a0744-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a0744-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="a0744-109">Install the npm module</span></span>

<span data-ttu-id="a0744-110">Azure Service Fabric npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a0744-110">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="a0744-111">예제</span><span class="sxs-lookup"><span data-stu-id="a0744-111">Example</span></span>

<span data-ttu-id="a0744-112">이 예제에서는 Azure 구독에 대한 클러스터를 나열하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a0744-112">This example shows how you can list the clusters for an Azure subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="a0744-113">샘플</span><span class="sxs-lookup"><span data-stu-id="a0744-113">Samples</span></span>

<span data-ttu-id="a0744-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="a0744-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
