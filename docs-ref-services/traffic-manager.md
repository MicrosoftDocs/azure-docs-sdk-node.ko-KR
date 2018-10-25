---
title: Node.js용 Azure Traffic Manager 모듈
description: Node.js용 Azure Traffic Manager 모듈 참조
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: 2a32eed460c6076011fdcf31d77200502ef61a3d
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49675758"
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a>Node.js용 Azure Traffic Manager 모듈

## <a name="overview"></a>개요

Microsoft Azure Traffic Manager를 사용하면 다양한 데이터 센터에서 서비스 엔드포인트에 대한 사용자 트래픽의 배포를 제어할 수 있습니다. Traffic Manager에서 지원되는 서비스 엔드포인트는 Azure VM, Web Apps 및 클라우드 서비스를 포함합니다. 또한 외부, Azure가 아닌 엔드포인트로 Traffic Manager를 사용할 수 있습니다.

[Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)에 대해 자세히 알아보세요.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure Traffic Manager npm 모듈을 설치합니다.

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a>예

이 예제에서는 지정된 리소스 그룹에 대한 모든 Traffic Manager를 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
