---
title: "Node.js용 Azure Automation 모듈"
description: "Node.js용 Azure Automation 모듈에 대한 참조"
keywords: Azure, SDK, API, Automation, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 96861efce8eb95f567aa25f2304cb271d932d949
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-automation-modules-for-nodejs"></a>Node.js용 Azure Automation 모듈

## <a name="overview"></a>개요

Azure Automation은 사용자가 클라우드 및 엔터프라이즈 환경에서 일반적으로 장기간 실행되고, 오류가 발생하기 쉬우며, 자주 반복되는 수동 작업을 자동화할 수 있는 방법을 제공합니다. 시간을 절약하고, 일반 관리 작업의 안정성을 높이며, 이러한 작업을 정기적으로 자동 수행하도록 예약합니다. Runbook을 사용하는 프로세스를 자동화하거나 원하는 상태 구성을 사용하여 구성 관리를 자동화할 수 있습니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-modules-with-npm"></a>npm을 사용하여 모듈 설치

npm을 사용하여 Node.js용 Azure Automation 모듈을 설치합니다.

```bash
npm install azure-arm-automation
```

### <a name="example"></a>예제

이 예제에서는 자동화 계정을 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
