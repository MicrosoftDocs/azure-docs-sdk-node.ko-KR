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
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49702848"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="1f694-103">Node.js용 Azure IoT Hub 모듈</span><span class="sxs-lookup"><span data-stu-id="1f694-103">Azure IoT Hub modules for Node.js</span></span>

<span data-ttu-id="1f694-104">Azure IoT Hub는 수백만의 IoT 장치와 솔루션 백 엔드 간에서 안정적이고 안전한 양방향 통신이 가능하도록 완전히 관리되는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-104">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="1f694-105">Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="1f694-105">Azure IoT Hub:</span></span>
- <span data-ttu-id="1f694-106">단방향 메시징, 파일 전송 및 요청-회신 메서드를 포함하여 여러 장치-클라우드 및 클라우드-장치 간 통신 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-106">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="1f694-107">다른 Azure 서비스에 기본 제공되는 선언적 메시지 라우팅을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-107">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="1f694-108">장치 메타데이터와 동기화된 상태 정보에 대한 쿼리 가능한 저장소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-108">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="1f694-109">장치 단위 보안 키 또는 X.509 인증서를 사용하여 통신 및 액세스 제어를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-109">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="1f694-110">장치 연결 및 장치 ID 관리 이벤트에 대한 포괄적인 모니터링을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-110">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="1f694-111">가장 인기 있는 언어 및 플랫폼에 대한 장치 라이브러리를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-111">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="1f694-112">npm을 사용하여 Node.js용 Azure IoT Hub 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-112">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="1f694-113">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="1f694-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1f694-114">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="1f694-114">Install the npm module</span></span>

<span data-ttu-id="1f694-115">Azure IoT Hub npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-115">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="1f694-116">예</span><span class="sxs-lookup"><span data-stu-id="1f694-116">Example</span></span>

<span data-ttu-id="1f694-117">이 예제에서는 IoT Hub를 만들고 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-117">This example creates and names an IoT hub.</span></span>

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

<span data-ttu-id="1f694-118">이 예제에서는 기존 IoT Hub를 이름별로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-118">This example gets the existing IoT hub, by name.</span></span>

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

## <a name="samples"></a><span data-ttu-id="1f694-119">샘플</span><span class="sxs-lookup"><span data-stu-id="1f694-119">Samples</span></span>

- [<span data-ttu-id="1f694-120">Raspberry Pi Azure IoT 시작 키트 시작(영문)</span><span class="sxs-lookup"><span data-stu-id="1f694-120">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [<span data-ttu-id="1f694-121">Node.js를 실행하는 Intel Edison의 데이터에서 Azure IoT 서비스로 검색된 진동 이상 트윗(영문)</span><span class="sxs-lookup"><span data-stu-id="1f694-121">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="1f694-122">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="1f694-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
