---
title: Node.js용 Azure 청구 모듈
description: Node.js용 Azure 청구 모듈에 대한 참조
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 7be64d01c1bf8d247694735b8581f72678f55983
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52094475"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="5a27f-103">Node.js용 Azure 청구 모듈</span><span class="sxs-lookup"><span data-stu-id="5a27f-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5a27f-104">개요</span><span class="sxs-lookup"><span data-stu-id="5a27f-104">Overview</span></span>
<span data-ttu-id="5a27f-105">Azure 청구 API는 Azure 청구 정보 및 송장에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5a27f-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="5a27f-106">이 API를 사용하려면 계정 관리자가 Azure Portal을 통해 옵트인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a27f-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="5a27f-107">[역할을 사용하여 Azure 청구에 대한 액세스 관리](https://docs.microsoft.com/azure/billing/billing-manage-access)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a27f-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5a27f-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="5a27f-108">Install the npm module</span></span> 

<span data-ttu-id="5a27f-109">Azure 청구 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5a27f-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="5a27f-110">예</span><span class="sxs-lookup"><span data-stu-id="5a27f-110">Example</span></span> 
 
<span data-ttu-id="5a27f-111">이 예제에서는 과거의 모든 송장 목록을 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="5a27f-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="5a27f-112">샘플</span><span class="sxs-lookup"><span data-stu-id="5a27f-112">Samples</span></span>

<span data-ttu-id="5a27f-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="5a27f-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
