---
title: Node.js용 Azure IoT Hub 모듈
description: Node.js용 Azure IoT Hub 모듈에 대한 참조
author: dominicbetts
ms.author: dobett
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 1f83e016023722f149384ac015726e9257a9f3af
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50326620"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a>Node.js용 Azure IoT Hub 모듈

Azure IoT Hub는 수백만의 IoT 장치와 솔루션 백 엔드 간에서 안정적이고 안전한 양방향 통신이 가능하도록 완전히 관리되는 서비스입니다. Azure IoT Hub
- 단방향 메시징, 파일 전송 및 요청-회신 메서드를 포함하여 여러 장치-클라우드 및 클라우드-장치 간 통신 옵션을 제공합니다.
- 다른 Azure 서비스에 기본 제공되는 선언적 메시지 라우팅을 제공합니다.
- 장치 메타데이터와 동기화된 상태 정보에 대한 쿼리 가능한 저장소를 제공합니다.
- 장치 단위 보안 키 또는 X.509 인증서를 사용하여 통신 및 액세스 제어를 보호합니다.
- 장치 연결 및 장치 ID 관리 이벤트에 대한 포괄적인 모니터링을 제공합니다.
- 가장 인기 있는 언어 및 플랫폼에 대한 장치 라이브러리를 포함합니다.

npm을 사용하여 Node.js용 Azure IoT Hub 모듈을 설치합니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure IoT Hub npm 모듈을 설치합니다.

```bash
npm install azure-arm-iothub
```

### <a name="example"></a>예

이 예제에서는 IoT Hub를 만들고 이름을 지정합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const IoTHubClient = require('azure-arm-iothub');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';
const location = 'East US';

// Describe the IoT hub you want to create
const hubDescription = {
  name: hubName,
  location: location,
  subscriptionid: subscriptionId,
  resourcegroup: resourceGroup,
  sku: { name: 'S1', capacity: 2 },
  properties: {
    enableFileUploadNotifications: false,
    ipFilterRules: [{ filterName: 'ipfilterrule', action: 'accept', ipMask: '0.0.0.0/0' }],
    operationsMonitoringProperties: {
      events: {
        C2DCommands: 'Error',
        DeviceTelemetry: 'Error',
        DeviceIdentityOperations: 'Error',
        Connections: 'Error, Information'
      }
    },
    features: 'None'
  }
};

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .createOrUpdate(resourceGroup, hubName, hubDescription)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

이 예제에서는 기존 IoT Hub를 이름별로 가져옵니다.

```javascript
const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .get(resourceGroup, hubName)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

## <a name="samples"></a>샘플

- [Raspberry Pi Azure IoT 시작 키트 시작(영문)](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [Node.js를 실행하는 Intel Edison의 데이터에서 Azure IoT 서비스로 검색된 진동 이상 트윗(영문)](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
