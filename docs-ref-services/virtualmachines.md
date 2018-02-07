---
title: "Node.js용 Virtual Machine 모듈 - Azure"
description: "Node.js용 Azure Virtual Machine 모듈 참조"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 608a915499d7c32c2c8b04464f716fa4fd17243d
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="03f3b-103">Node.js용 Azure Virtual Machine 모듈</span><span class="sxs-lookup"><span data-stu-id="03f3b-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="03f3b-104">개요</span><span class="sxs-lookup"><span data-stu-id="03f3b-104">Overview</span></span>

<span data-ttu-id="03f3b-105">Node.js용 Azure 관리 모듈을 사용하여 코드에서 새 Windows 및 Linux 가상 머신 및 가상 머신 확장 집합을 정의, 구성 및 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="03f3b-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="03f3b-106">이 모듈을 사용하면 기존 가상 머신을 시작 및 중지하고 Azure 구독에서 중지된 VM에 디스크를 연결하거나 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03f3b-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="03f3b-107">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="03f3b-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="03f3b-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="03f3b-108">Install the npm module</span></span>

<span data-ttu-id="03f3b-109">Azure Compute npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="03f3b-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="03f3b-110">예</span><span class="sxs-lookup"><span data-stu-id="03f3b-110">Example</span></span>

<span data-ttu-id="03f3b-111">다음 예제에서는 Azure에 로그인하여 관리 클라이언트를 만들고, 지정된 위치, 게시자, 제품 및 SKU에 대한 모든 VM 이미지를 나열하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="03f3b-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="03f3b-112">샘플</span><span class="sxs-lookup"><span data-stu-id="03f3b-112">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="03f3b-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="03f3b-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
