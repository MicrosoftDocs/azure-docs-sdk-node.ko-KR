---
title: "Node.js용 Azure Virtual Network 모듈"
description: "Node.js용 Azure Virtual Network 모듈에 대한 참조"
keywords: Azure, SDK, API, Virtual Network, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: a17615a832c6dddeb7fef0a8a327dbf86ae281a7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="5cd09-104">Node.js용 Azure Virtual Network 모듈</span><span class="sxs-lookup"><span data-stu-id="5cd09-104">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5cd09-105">개요</span><span class="sxs-lookup"><span data-stu-id="5cd09-105">Overview</span></span>

<span data-ttu-id="5cd09-106">Azure Virtual Network 서비스를 사용하면 Azure 리소스와 가상 네트워크(VNet)를 서로 안전하게 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd09-106">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="5cd09-107">VNet은 클라우드의 사용자 네트워크를 나타내는 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd09-107">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="5cd09-108">구독 전용 Azure 클라우드를 논리적으로 격리한 것이 VNet입니다.</span><span class="sxs-lookup"><span data-stu-id="5cd09-108">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="5cd09-109">또한 온-프레미스 네트워크에 VNet을 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cd09-109">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="5cd09-110">[Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="5cd09-110">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="5cd09-111">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="5cd09-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5cd09-112">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="5cd09-112">Install the npm module</span></span>

<span data-ttu-id="5cd09-113">Azure Virtual Network npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd09-113">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="5cd09-114">예제</span><span class="sxs-lookup"><span data-stu-id="5cd09-114">Example</span></span>

<span data-ttu-id="5cd09-115">이 예제에서는 가상 네트워크 목록을 가져오고 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd09-115">This example gets and prints the list of virtual networks</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a><span data-ttu-id="5cd09-116">샘플</span><span class="sxs-lookup"><span data-stu-id="5cd09-116">Samples</span></span>

<span data-ttu-id="5cd09-117">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="5cd09-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
