---
title: Node.js용 Azure 상거래 모듈
description: Node.js용 Azure 상거래 모듈에 대한 참조
author: rloutlaw
ms.author: ROutlaw
manager: angrobew
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 87a0e8d689d8d782a705a4525fdbe9b681403c07
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49757398"
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="af0fc-103">Node.js용 Azure 상거래 모듈</span><span class="sxs-lookup"><span data-stu-id="af0fc-103">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="af0fc-104">개요</span><span class="sxs-lookup"><span data-stu-id="af0fc-104">Overview</span></span>

<span data-ttu-id="af0fc-105">Azure 상거래 API를 사용하여 사용량 및 리소스 데이터를 기본 설정된 데이터 분석 도구로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="af0fc-105">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="af0fc-106">Azure 리소스 사용량 및 RateCard API를 통해 비용을 정확하게 예측하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af0fc-106">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="af0fc-107">API는 Azure Resource Manager가 노출한 API의 제품군의 일부로서 리소스 공급자로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="af0fc-107">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="af0fc-108">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="af0fc-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="af0fc-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="af0fc-109">Install the npm module</span></span>

<span data-ttu-id="af0fc-110">Azure 상거래 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="af0fc-110">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="af0fc-111">예</span><span class="sxs-lookup"><span data-stu-id="af0fc-111">Example</span></span>

<span data-ttu-id="af0fc-112">이 예제에서는 지난 달에 대한 Azure 예상 사용량 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="af0fc-112">This example retrieves your estimated Azure consumption data for the last month.</span></span>

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

## <a name="samples"></a><span data-ttu-id="af0fc-113">샘플</span><span class="sxs-lookup"><span data-stu-id="af0fc-113">Samples</span></span>

<span data-ttu-id="af0fc-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="af0fc-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
