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
ms.openlocfilehash: 33e290343f9188a1f78e53f6b8ed89594e2d9b46
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-commerce-modules-for-nodejs"></a>Node.js용 Azure 상거래 모듈

## <a name="overview"></a>개요

Azure 상거래 API를 사용하여 사용량 및 리소스 데이터를 기본 설정된 데이터 분석 도구로 끌어옵니다. Azure 리소스 사용량 및 RateCard API를 통해 비용을 정확하게 예측하고 관리할 수 있습니다. API는 Azure Resource Manager가 노출한 API의 제품군의 일부로서 리소스 공급자로 구현됩니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure 상거래 npm 모듈을 설치합니다.

```bash
npm install azure-arm-commerce
```

### <a name="example"></a>예

이 예제에서는 지난 달에 대한 Azure 예상 사용량 데이터를 검색합니다.

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

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
