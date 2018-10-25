---
title: Node.js용 Azure Analysis Services 모듈
description: Node.js용 Azure Analysis Services 모듈에 대한 참조
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 5214cd2f171074ba330bc639643dfba490540856
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49702687"
---
# <a name="azure-analysis-services-modules-for-nodejs"></a>Node.js용 Azure Analysis Services 모듈

## <a name="overview"></a>개요
이 패키지는 Microsoft Azure Analysis Services를 쉽게 관리할 수 있게 하는 Node.js를 모듈을 제공합니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure Analysis Services npm 모듈을 설치합니다.

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a>예

이 예제에서는 사용 가능한 모든 Analysis Services 서버를 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
