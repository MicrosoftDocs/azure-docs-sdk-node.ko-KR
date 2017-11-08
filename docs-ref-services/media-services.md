---
title: "Node.js용 Azure Media Services 모듈"
description: "Node.js용 Azure Media Services 모듈에 대한 참조"
keywords: Azure, SDK, API, Media Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 9b304ceb0c2d0580534ae1bee5a44d01fd4d8b33
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-media-services-modules-for-nodejs"></a>Node.js용 Azure Media Services 모듈

## <a name="overview"></a>개요

Azure Media Services는 개발자가 확장 가능한 미디어 관리 및 배달 응용 프로그램을 빌드할 수 있는 확장 가능한 클라우드 기반 플랫폼입니다. Media Services는 다양한 클라이언트(예: TV, PC 및 모바일 장치)로의 주문형 및 라이브 스트리밍 배달을 위해 비디오 또는 오디오 콘텐츠를 안전하게 업로드, 저장, 인코딩 및 패키지할 수 있는 REST API를 기반으로 합니다.

Azure Media Services를 사용하여 다음을 수행할 수 있습니다.
- Media Services를 전적으로 사용하여 종단 간 워크플로를 작성합니다. 
- 워크플로의 일부에 타사 구성 요소를 사용합니다. 예를 들어 타사 인코더를 사용하여 인코딩합니다. 그런 다음 Media Services를 사용하여 업로드, 보호, 패키징 및 배달합니다.
- 콘텐츠를 라이브로 스트리밍하거나 주문형 콘텐츠를 전달합니다. 이 항목은 관련 항목으로도 연결됩니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure Media Services npm 모듈을 설치합니다.

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a>예제

이 예제에서는 리소스 그룹에 대한 모든 Media Services를 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.