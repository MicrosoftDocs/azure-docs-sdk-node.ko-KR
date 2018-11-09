---
title: Node.js용 Azure Service Fabric 모듈
description: Node.js용 Azure Service Fabric 모듈 참조
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 3fd2f73bc6fddf01548bbb92cce540775d4c7c76
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51083522"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="019cb-103">Node.js용 Azure Service Fabric 모듈</span><span class="sxs-lookup"><span data-stu-id="019cb-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="019cb-104">개요</span><span class="sxs-lookup"><span data-stu-id="019cb-104">Overview</span></span>

<span data-ttu-id="019cb-105">Azure Service Fabric은 손쉽게 패키지하고 배포하며 확장 가능하고 안정성이 뛰어난 마이크로 서비스 및 컨테이너를 관리하도록 배포된 시스템 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="019cb-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="019cb-106">[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="019cb-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="019cb-107">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="019cb-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="019cb-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="019cb-108">Install the npm module</span></span>

<span data-ttu-id="019cb-109">Azure Service Fabric npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="019cb-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="019cb-110">예</span><span class="sxs-lookup"><span data-stu-id="019cb-110">Example</span></span>

<span data-ttu-id="019cb-111">이 예제에서는 Azure 구독에 대한 클러스터를 나열하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="019cb-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="019cb-112">샘플</span><span class="sxs-lookup"><span data-stu-id="019cb-112">Samples</span></span>

<span data-ttu-id="019cb-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="019cb-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
