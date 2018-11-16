---
title: Node.js용 Azure Virtual Network 모듈
description: Node.js용 Azure Virtual Network 모듈에 대한 참조
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 11341fdff5df3b7521319d841707493db1d07732
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51444347"
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="19980-103">Node.js용 Azure Virtual Network 모듈</span><span class="sxs-lookup"><span data-stu-id="19980-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="19980-104">개요</span><span class="sxs-lookup"><span data-stu-id="19980-104">Overview</span></span>

<span data-ttu-id="19980-105">Azure Virtual Network 서비스를 사용하면 가상 네트워크(VNet)를 통해 Azure 리소스를 서로 안전하게 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19980-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="19980-106">VNet은 클라우드에 있는 사용자의 네트워크를 나타내며,</span><span class="sxs-lookup"><span data-stu-id="19980-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="19980-107">구독 전용 Azure 클라우드를 논리적으로 격리한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="19980-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="19980-108">이 VNet을 온-프레미스 네트워크에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19980-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="19980-109">[Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="19980-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="19980-110">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="19980-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="19980-111">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="19980-111">Install the npm module</span></span>

<span data-ttu-id="19980-112">Azure Virtual Network npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="19980-113">예</span><span class="sxs-lookup"><span data-stu-id="19980-113">Example</span></span>

<span data-ttu-id="19980-114">이 예제에서는 가상 네트워크 목록을 가져오고 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-114">This example gets and prints the list of virtual networks</span></span>

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

## <a name="samples"></a><span data-ttu-id="19980-115">샘플</span><span class="sxs-lookup"><span data-stu-id="19980-115">Samples</span></span>

<span data-ttu-id="19980-116">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="19980-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
