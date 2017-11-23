---
title: "Node.js용 Azure 상거래 모듈"
description: "Node.js용 Azure 상거래 모듈에 대한 참조"
keywords: "Azure, SDK, API, 상거래, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: b337e070ee7da0b852d8cad1d4e163d7f8130857
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="b4056-104">Node.js용 Azure 상거래 모듈</span><span class="sxs-lookup"><span data-stu-id="b4056-104">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b4056-105">개요</span><span class="sxs-lookup"><span data-stu-id="b4056-105">Overview</span></span>

<span data-ttu-id="b4056-106">Azure 상거래 API를 사용하여 사용량 및 리소스 데이터를 기본 설정된 데이터 분석 도구로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4056-106">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="b4056-107">Azure 리소스 사용량 및 RateCard API를 통해 비용을 정확하게 예측하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4056-107">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="b4056-108">API는 Azure Resource Manager가 노출한 API의 제품군의 일부로서 리소스 공급자로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4056-108">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="b4056-109">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="b4056-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b4056-110">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="b4056-110">Install the npm module</span></span>

<span data-ttu-id="b4056-111">Azure 상거래 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b4056-111">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="b4056-112">예제</span><span class="sxs-lookup"><span data-stu-id="b4056-112">Example</span></span>

<span data-ttu-id="b4056-113">이 예제에서는 지난 달에 대한 Azure 예상 사용량 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b4056-113">This example retrieves your estimated Azure consumption data for the last month.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="b4056-114">샘플</span><span class="sxs-lookup"><span data-stu-id="b4056-114">Samples</span></span>

<span data-ttu-id="b4056-115">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="b4056-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
