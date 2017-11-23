---
title: "Node.js용 Azure Virtual Machine 모듈"
description: "Node.js용 Azure Virtual Machine 모듈에 대한 참조"
keywords: Azure, Node, SDK, API, Virtual Machine, VM, NodeJS, JavaScript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="8cf0b-104">Node.js용 Azure Virtual Machine 모듈</span><span class="sxs-lookup"><span data-stu-id="8cf0b-104">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="8cf0b-105">개요</span><span class="sxs-lookup"><span data-stu-id="8cf0b-105">Overview</span></span>

<span data-ttu-id="8cf0b-106">Node.js용 Azure 관리 모듈을 사용하여 코드에서 새 Windows 및 Linux 가상 컴퓨터 및 가상 컴퓨터 확장 집합을 정의, 구성 및 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="8cf0b-106">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="8cf0b-107">이 모듈을 사용하면 기존 가상 컴퓨터를 시작 및 중지하고 Azure 구독에서 중지된 VM에 디스크를 연결하거나 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cf0b-107">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="8cf0b-108">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="8cf0b-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="8cf0b-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="8cf0b-109">Install the npm module</span></span>

<span data-ttu-id="8cf0b-110">Azure Compute npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="8cf0b-110">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="8cf0b-111">예제</span><span class="sxs-lookup"><span data-stu-id="8cf0b-111">Example</span></span>

<span data-ttu-id="8cf0b-112">다음 예제에서는 Azure에 로그인하여 관리 클라이언트를 만들고, 지정된 위치, 게시자, 제품 및 SKU에 대한 모든 VM 이미지를 나열하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8cf0b-112">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="8cf0b-113">샘플</span><span class="sxs-lookup"><span data-stu-id="8cf0b-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="8cf0b-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="8cf0b-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
