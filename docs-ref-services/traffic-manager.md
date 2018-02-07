---
title: "Node.js용 Azure Traffic Manager 모듈"
description: "Node.js용 Azure Traffic Manager 모듈 참조"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: cf0834a0eadc67868efb165d60d39c681d4435eb
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="deb1a-103">Node.js용 Azure Traffic Manager 모듈</span><span class="sxs-lookup"><span data-stu-id="deb1a-103">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="deb1a-104">개요</span><span class="sxs-lookup"><span data-stu-id="deb1a-104">Overview</span></span>

<span data-ttu-id="deb1a-105">Microsoft Azure Traffic Manager를 사용하면 다양한 데이터 센터에서 서비스 끝점에 대한 사용자 트래픽의 배포를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb1a-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="deb1a-106">Traffic Manager에서 지원되는 서비스 끝점은 Azure VM, Web Apps 및 클라우드 서비스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="deb1a-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="deb1a-107">또한 외부, Azure가 아닌 끝점으로 Traffic Manager를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deb1a-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="deb1a-108">[Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="deb1a-108">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="deb1a-109">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="deb1a-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="deb1a-110">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="deb1a-110">Install the npm module</span></span>

<span data-ttu-id="deb1a-111">Azure Traffic Manager npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="deb1a-111">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="deb1a-112">예</span><span class="sxs-lookup"><span data-stu-id="deb1a-112">Example</span></span>

<span data-ttu-id="deb1a-113">이 예제에서는 지정된 리소스 그룹에 대한 모든 Traffic Manager를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="deb1a-113">This example lists all Traffic Managers for a given resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a><span data-ttu-id="deb1a-114">샘플</span><span class="sxs-lookup"><span data-stu-id="deb1a-114">Samples</span></span>

<span data-ttu-id="deb1a-115">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="deb1a-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
