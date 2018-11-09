---
title: Node.js용 Azure Operational Insights 모듈
description: Node.js용 Azure Operational Insights 모듈에 대한 참조
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: c8a137c4759982e0551d9048ac271780e6a68afe
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51185532"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a>Node.js용 Azure Operational Insights 모듈

npm을 사용하여 Node.js용 Azure Operational Insights 모듈을 설치합니다.

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a>예 

이 예제에서는 클라이언트를 만들고, Operational Insights에 연결하고, 지정된 리소스 그룹별로 작업 영역 목록을 검색합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
