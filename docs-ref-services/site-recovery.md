---
title: Node.js용 Azure Site Recovery 모듈
description: Node.js용 Azure Site Recovery 모듈에 대한 참조
author: rayne-wiselman
ms.author: raynew
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: f8cddf806b921d5445cd0757b64aeb0dc5df03cf
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49739678"
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="4ba18-103">Node.js용 Azure Site Recovery 모듈</span><span class="sxs-lookup"><span data-stu-id="4ba18-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="4ba18-104">Site Recovery를 사용하면 지역, 온-프레미스 가상 머신 및 물리적 서버 사이의 Azure VM을 Azure로 복제하거나 온-프레미스 컴퓨터를 보조 데이터 센터로 복제하도록 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba18-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="4ba18-105">[Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="4ba18-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="4ba18-106">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="4ba18-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4ba18-107">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="4ba18-107">Install the npm module</span></span>

<span data-ttu-id="4ba18-108">Azure Site Recovery 서비스 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba18-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="4ba18-109">예</span><span class="sxs-lookup"><span data-stu-id="4ba18-109">Example</span></span>

<span data-ttu-id="4ba18-110">이 예제에서는 리소스 그룹에 대한 Site Recovery 서비스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba18-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="4ba18-111">샘플</span><span class="sxs-lookup"><span data-stu-id="4ba18-111">Samples</span></span>

<span data-ttu-id="4ba18-112">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba18-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
