---
title: Node.js용 Azure Cognitive Services 모듈
description: Node.js용 Azure Cognitive Services 모듈에 대한 참조
author: brapel
ms.author: v-brapel
manager: ehansen
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fb0319965f7ea9d1bcab25e0e213998052b78ae0
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49714628"
---
# <a name="javascript-azure-cognitive-services-modules"></a>JavaScript Azure Cognitive Services 모듈

## <a name="vision-modules"></a>비전 모듈

### <a name="computer-vision"></a>Computer Vision 

이미지에서 찾은 시각적 콘텐츠에 대한 정보를 반환합니다.

- 태그 지정, 설명 및 도메인 특정 모델을 사용하여 자신 있게 콘텐츠를 파악하고 레이블을 지정하세요.
- 성인 콘텐츠를 자동으로 제한할 수 있도록 성인/외설 설정을 적용합니다.
- 사진의 이미지 형식과 색 구성표를 파악합니다.

브라우저에서 무료로 [Computer Vision을 사용](https://azure.microsoft.com/services/cognitive-services/computer-vision/)해 보세요.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-computervision
```

Computer Vision API에 대해 [자세히 알아보고](/azure/cognitive-services/computer-vision/home) [Computer Vision API JavaScript 빠른 시작](/azure/cognitive-services/computer-vision/quickstarts/javascript)을 시작하세요.

### <a name="content-moderator"></a>Content Moderator

사용자 검토 도구로 확대된, 텍스트, 비디오 및 이미지의 기계 지원 조정.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-contentmoderator
```

Content Moderator 서비스에 대해 [자세히 알아보세요](/azure/cognitive-services/content-moderator/overview).

### <a name="face-api"></a>Face API

사진에서 얼굴을 감지, 식별, 분석, 구성하고 태그를 지정합니다. 

브라우저에서 [Face API를 사용](https://azure.microsoft.com/services/cognitive-services/face/)해 보세요.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-face
```

Face API에 대해 [자세히 알아보고](/azure/cognitive-services/face/overview) [Face API JavaScript 빠른 시작](/azure/cognitive-services/Face/quickstarts/javascript)을 시작하세요.

## <a name="search-modules"></a>검색 모듈

### <a name="web-search"></a>Web Search

Bing Web Search API로 인덱싱된 웹 문서를 검색하고 결과 형식, 최신성 등을 기준으로 결과의 범위를 축소해 보세요. 

브라우저에서 [Web Search API를 사용](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/)해 보세요.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-websearch
```

Bing Web Search API에 대해 [자세히 알아보고](/azure/cognitive-services/bing-web-search/overview) [Web Search API Node.js 빠른 시작](/azure/cognitive-services/bing-web-search/quickstarts/nodejs)을 시작하세요.

### <a name="image-search"></a>이미지 검색

이미지를 검색하고 결과에 썸네일, 전체 이미지 URL, 이미지 메타데이터 등을 가져오세요.

브라우저에서 [Image Search API를 사용](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/)해 보세요.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-imagesearch
```

Bing Image Search API에 대해 [자세히 알아보고](/azure/cognitive-services/bing-image-search/overview) [Image Search API Node.js 빠른 시작](/azure/cognitive-services/bing-image-search/quickstarts/nodejs)을 시작하세요.


### <a name="entity-search"></a>Entity Search

특정 검색어 또는 위치와 가장 관련 있는 엔터티(장소, 사람 또는 물건)를 검색하세요.

브라우저에서 [Entity Search API를 사용](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/)해 보세요.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-entitysearch
```

Bing Entity Search API에 대해 [자세히 알아보고](/azure/cognitive-services/bing-entities-search/search-the-web) [Entity Search API Node.js 빠른 시작](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs)을 시작하세요.

### <a name="custom-search"></a>Custom Search

특정 검색 도메인에 맞는 사용자 지정 웹 검색을 빌드해 보세요.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-customsearch
```

Bing Custom Search 서비스에 대해 [자세히 알아보고](/azure/cognitive-services/bing-custom-search/) [Custom Search API Node.js 빠른 시작](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs)을 사용하여 앱에서 사용자 지정 검색 쿼리를 시작하세요.

### <a name="video-search"></a>Video Search

웹에서 비디오를 검색하고 작성자, 인코딩, 길이 및 조회수 메타데이터가 포함된 결과를 가져오세요.

브라우저에서 [Video Search API를 사용](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/)해 보세요.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-videosearch
```

Bing Video Search 서비스에 대해 [자세히 알아보고](/azure/cognitive-services/bing-video-search/search-the-web) [Video Search API Node.js 빠른 시작](/azure/cognitive-services/bing-video-search/nodejs)을 시작하세요.


### <a name="news-search"></a>News Search

웹에서 뉴스 기사를 검색하고, 기사, 관련 뉴스, 이미지 및 공급자 정보 메타데이터로 작업하세요.

브라우저에서 [News Search API를 사용](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/)해 보세요.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-newssearch
```

Bing News Search 서비스에 대해 [자세히 알아보고](/azure/cognitive-services/bing-news-search/search-the-web) [News Search API JavaScript 빠른 시작](/azure/cognitive-services/bing-news-search/nodejs)을 시작하세요.


## <a name="language-modules"></a>언어 모듈

### <a name="text-analytics"></a>텍스트 분석 

텍스트 분석 API는 원시 텍스트에 대한 자연어 처리를 제공하는 클라우드 기반 서비스입니다. 이 API에는 세 가지 주요 기능이 포함되어 있습니다.

- 정서 분석
- 핵심 문구 추출
- 언어 검색

브라우저에서 [텍스트 분석 API를 사용](https://azure.microsoft.com/services/cognitive-services/text-analytics/)해 보세요.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-textanalytics
```

텍스트 분석 API에 대해 [자세히 알아보고](/azure/cognitive-services/text-analytics/overview) [텍스트 분석 API Node.js 빠른 시작](/azure/cognitive-services/text-analytics/quickstarts/nodejs)을 시작하세요.


### <a name="spell-check"></a>Spell Check

Bing Spell Check API를 사용하여 상황별 문법 및 맞춤법 검사를 수행하세요.

브라우저에서 [Spell Check API를 사용](https://azure.microsoft.com/services/cognitive-services/spell-check/)해 보세요.

[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.

```
npm install azure-cognitiveservices-spellcheck
```

Spell Check API에 대해 [자세히 알아보고](/azure/cognitive-services/bing-spell-check/proof-text) [Spell Check API Node.js 빠른 시작](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs)을 시작하세요.

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
