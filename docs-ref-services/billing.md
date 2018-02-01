---
title: "Node.js용 Azure 청구 모듈"
description: "Node.js용 Azure 청구 모듈에 대한 참조"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: 58eed8996f543e845a53a741f8684d9e7f6cc1e4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-billing-modules-for-nodejs"></a>Node.js용 Azure 청구 모듈

## <a name="overview"></a>개요
Azure 청구 API는 Azure 청구 정보 및 송장에 대한 액세스를 제공합니다.

이 API를 사용하려면 계정 관리자가 Azure Portal을 통해 옵트인해야 합니다. [역할을 사용하여 Azure 청구에 대한 액세스 관리](https://docs.microsoft.com/azure/billing/billing-manage-access)를 참조하세요.

### <a name="install-the-npm-module"></a>npm 모듈 설치 

Azure 청구 npm 모듈을 설치합니다. 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>예 
 
이 예제에서는 과거의 모든 송장 목록을 인쇄합니다.
 
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


## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
