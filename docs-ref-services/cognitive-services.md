---
title: "Node.js용 Azure Cognitive Services 모듈"
description: "Node.js용 Azure Cognitive Services 모듈에 대한 참조"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: df6ea913ca69341fbbb730b75f547ce9c10bd45f
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="cb0cf-103">Node.js용 Azure Cognitive Services 모듈</span><span class="sxs-lookup"><span data-stu-id="cb0cf-103">Azure Cognitive Services modules for Node.js</span></span>

<span data-ttu-id="cb0cf-104">Microsoft Cognitive Services는 개발자가 자신의 응용 프로그램을 더 지능적이고 매력적이며 검색 가능하게 만드는 데 사용할 수 있는 API, SDK 및 서비스 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="cb0cf-104">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="cb0cf-105">Microsoft Cognitive Services는 진화하는 기계 학습 API 포트폴리오를 확장하고, 개발자가 응용 프로그램에 지능형 기능, 즉 감정 및 비디오 검색, 얼굴, 음성 및 영상 인식, 음성 및 언어 이해 등을 쉽게 추가할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb0cf-105">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="cb0cf-106">점점 더 많이 보고, 듣고, 말하고, 이해하고, 심지어 추론도 시작할 수 있도록 시스템에서 더욱 개인적인 컴퓨팅 환경과 향상된 생산성을 지원하는 것이 Microsoft의 비전입니다.</span><span class="sxs-lookup"><span data-stu-id="cb0cf-106">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="cb0cf-107">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="cb0cf-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="cb0cf-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="cb0cf-108">Install the npm module</span></span>

<span data-ttu-id="cb0cf-109">Azure Cognitive Services npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cb0cf-109">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="cb0cf-110">예</span><span class="sxs-lookup"><span data-stu-id="cb0cf-110">Example</span></span>

<span data-ttu-id="cb0cf-111">이 예제에서는 모든 Cognitive Services 계정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="cb0cf-111">This example lists all cognitive service accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="cb0cf-112">샘플</span><span class="sxs-lookup"><span data-stu-id="cb0cf-112">Samples</span></span>

<span data-ttu-id="cb0cf-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="cb0cf-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
