---
title: "Node.js용 Azure Logic Apps 모듈"
description: "Node.js용 Azure Logic Apps 모듈에 대한 참조"
keywords: Azure, SDK, API, Logic Apps, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 70380dbf1fd199ba4909975b05ade72efaa4e0ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>Node.js용 Azure Logic Apps 모듈

## <a name="overview"></a>개요
Logic Apps는 클라우드에서 확장 가능한 통합 및 워크플로를 단순화하고 구현하는 방법을 제공합니다. 모델에 비주얼 디자이너를 제공하고 프로세스를 워크플로로 알려진 일련의 단계로 자동화합니다. 서비스 및 프로토콜에 걸쳐 신속하게 통합하기 위해 클라우드 및 온-프레미스에 많은 커넥터가 있습니다. 'Dynamics CRM에 계정을 추가하는 경우'와 같이 논리 앱은 트리거로 시작하고, 실행 후에 작업, 변환 및 조건 논리의 다양한 조합을 시작할 수 있습니다.

Logic Apps를 사용하는 이점은 다음과 같습니다.
- 설계 도구를 쉽게 이해하기 위해 사용하는 복잡한 프로세스를 설계하여 시간 절약
- 코드에서 구현하기 어려운 패턴 및 워크플로를 원활하게 구현
- 템플릿에서 신속하게 시작
- 고유의 사용자 지정 API, 코드 및 작업을 사용하여 논리 앱 사용자 지정
- 온-프레미스 및 클라우드에 서로 다른 시스템 연결 및 동기화
- 강력한 통합 지원을 통해 BizTalk Server, API Management, Azure Functions 및 Azure Service Bus 구축

Logic Apps는 완전히 관리되는 iPaaS(integration Platform as a Service)로서 개발자가 호스팅, 확장성, 가용성 및 관리를 구축하는 방법에 대해 걱정하지 않도록 합니다. Logic Apps는 수요에 맞게 자동으로 강화됩니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Node.js용 Azure 논리 모듈을 설치합니다.

```bash
npm install azure-arm-logic
```

### <a name="example"></a>예제

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
