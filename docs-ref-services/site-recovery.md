---
title: "Node.js용 Azure Site Recovery 모듈"
description: "Node.js용 Azure Site Recovery 모듈에 대한 참조"
keywords: Azure, SDK, API, Site Recovery, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="f8c0a-104">Node.js용 Azure Site Recovery 모듈</span><span class="sxs-lookup"><span data-stu-id="f8c0a-104">Azure Site Recovery modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f8c0a-105">개요</span><span class="sxs-lookup"><span data-stu-id="f8c0a-105">Overview</span></span>

<span data-ttu-id="f8c0a-106">Site Recovery를 사용하면 지역, 온-프레미스 가상 컴퓨터 및 물리적 서버 사이의 Azure VM을 Azure로 복제하거나 온-프레미스 컴퓨터를 보조 데이터 센터로 복제하도록 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8c0a-106">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="f8c0a-107">[Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="f8c0a-107">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="f8c0a-108">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="f8c0a-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f8c0a-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="f8c0a-109">Install the npm module</span></span>

<span data-ttu-id="f8c0a-110">Azure Site Recovery 서비스 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c0a-110">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="f8c0a-111">예제</span><span class="sxs-lookup"><span data-stu-id="f8c0a-111">Example</span></span>

<span data-ttu-id="f8c0a-112">이 예제에서는 리소스 그룹에 대한 Site Recovery 서비스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c0a-112">This example lists the Site Recovery service for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a><span data-ttu-id="f8c0a-113">샘플</span><span class="sxs-lookup"><span data-stu-id="f8c0a-113">Samples</span></span>

<span data-ttu-id="f8c0a-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c0a-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
