---
title: "Node.js용 Azure DevTest Labs 모듈"
description: "Node.js용 Azure DevTest Labs 모듈에 대한 참조"
keywords: Azure, SDK, API, DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>Node.js용 Azure DevTest Labs 모듈

## <a name="overview"></a>개요

Azure DevTest Lab은 개발자와 테스터가 낭비를 최소화하고 비용을 제어하면서 Azure에서 빠르게 환경을 만들 수 있도록 돕는 서비스입니다. 재사용이 가능한 템플릿과 아티팩트를 사용하여 Windows와 Linux 환경을 빠르게 프로비전함으로써 최신 버전의 응용 프로그램을 테스트할 수 있습니다. 배포 파이프라인과 DevTest Lab을 쉽게 통합하여 주문형 환경으로 프로비전할 수 있습니다. 여러 개의 테스트 에이전트를 프로비전하여 부하 테스트를 확장하고 교육 및 데모를 위해 미리 프로비전된 환경을 만듭니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure DevTest Labs npm 모듈을 설치합니다.

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a>예제

이 예제에서는 랩의 세부 정보를 가져오고 인쇄합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.