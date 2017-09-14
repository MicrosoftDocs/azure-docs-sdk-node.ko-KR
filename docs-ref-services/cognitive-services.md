---
title: "Node.js용 Azure Cognitive Services 모듈"
description: "Node.js용 Azure Cognitive Services 모듈에 대한 참조"
keywords: Azure, SDK, API, Cognitive Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fba98930fccaf4fa40dd1d0224031276f5fb7f84
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a>Node.js용 Azure Cognitive Services 모듈

## <a name="overview"></a>개요

Microsoft Cognitive Services는 개발자가 자신의 응용 프로그램을 더 지능적이고 매력적이며 검색 가능하게 만드는 데 사용할 수 있는 API, SDK 및 서비스 집합입니다. Microsoft Cognitive Services는 진화하는 기계 학습 API 포트폴리오를 확장하고, 개발자가 응용 프로그램에 지능형 기능, 즉 감정 및 비디오 검색, 얼굴, 음성 및 영상 인식, 음성 및 언어 이해 등을 쉽게 추가할 수 있게 합니다. 점점 더 많이 보고, 듣고, 말하고, 이해하고, 심지어 추론도 시작할 수 있도록 시스템에서 더욱 개인적인 컴퓨팅 환경과 향상된 생산성을 지원하는 것이 Microsoft의 비전입니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure Cognitive Services npm 모듈을 설치합니다.

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a>예제

이 예제에서는 모든 Cognitive Services 계정을 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
