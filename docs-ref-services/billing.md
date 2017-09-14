---
title: "Node.js용 Azure 청구 모듈"
description: "Node.js용 Azure 청구 모듈에 대한 참조"
keywords: "Azure, SDK, API, 청구, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="56436-104">Node.js용 Azure 청구 모듈</span><span class="sxs-lookup"><span data-stu-id="56436-104">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="56436-105">개요</span><span class="sxs-lookup"><span data-stu-id="56436-105">Overview</span></span>
<span data-ttu-id="56436-106">Azure 청구 API는 Azure 청구 정보 및 송장에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56436-106">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="56436-107">이 API를 사용하려면 계정 관리자가 Azure Portal을 통해 옵트인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56436-107">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="56436-108">[역할을 사용하여 Azure 청구에 대한 액세스 관리](https://docs.microsoft.com/azure/billing/billing-manage-access)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56436-108">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="56436-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="56436-109">Install the npm module</span></span> 

<span data-ttu-id="56436-110">Azure 청구 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="56436-110">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="56436-111">예제</span><span class="sxs-lookup"><span data-stu-id="56436-111">Example</span></span> 
 
<span data-ttu-id="56436-112">이 예제에서는 과거의 모든 송장 목록을 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="56436-112">This example prints a list of all of your past invoices.</span></span>
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a><span data-ttu-id="56436-113">샘플</span><span class="sxs-lookup"><span data-stu-id="56436-113">Samples</span></span>

<span data-ttu-id="56436-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="56436-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
