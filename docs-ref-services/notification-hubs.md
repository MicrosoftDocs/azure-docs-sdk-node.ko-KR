---
title: Node.js용 Azure Notification Hubs 모듈
description: Node.js용 Azure Notification Hubs 모듈에 대한 참조
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 18eae632b41b71bc64b052852b677507da2678e9
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51099032"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a>Node.js용 Azure Notification Hubs 모듈

Azure Notification Hubs는 사용하기 쉬운 다중 플랫폼의 확장된 푸시 엔진을 제공합니다. 단일 플랫폼 간 API 호출을 통해 클라우드 또는 온-프레미스 백 엔드에서 모든 모바일 플랫폼으로 개인 설정된 대상 푸시 알림을 쉽게 보낼 수 있습니다.

Notification Hubs는 엔터프라이즈 시나리오 및 소비자 시나리오 모두에 적합합니다. 다음은 고객이 Notification Hubs를 사용하는 몇 가지 예입니다.
- 수백만 명의 사용자에게 대기 시간이 짧은 최신 뉴스 알림을 보냅니다.
- 관심 있는 사용자 세그먼트에 위치 기반 쿠폰을 보냅니다.
- 미디어/스포츠/금융/게임 응용 프로그램을 위해 사용자 또는 그룹에 이벤트 관련 알림을 보냅니다.
- 프로모션 콘텐츠를 앱에 푸시하여 고객을 참여시키고 마케팅 활동을 전개합니다.
- 새 메시지 및 작업 항목과 같은 엔터프라이즈 이벤트를 사용자에게 알립니다.
- 다단계 인증을 위한 코드를 보냅니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure Notification Hubs 모듈을 설치합니다. 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a>예

이 예제에서는 모든 알림 허브를 나열합니다.

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a>샘플

* [Node.js 백 엔드용 App Service Mobile Apps 빠른 시작 완성(영문)](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [Node.js를 실행하는 Intel Edison의 데이터에서 Azure IoT 서비스로 검색된 진동 이상 트윗(영문)](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
