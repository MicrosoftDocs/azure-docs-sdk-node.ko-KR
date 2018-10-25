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
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49772228"
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
