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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51071868"
---
# <a name="javascript-azure-cognitive-services-modules"></a><span data-ttu-id="bb5a1-103">JavaScript Azure Cognitive Services 모듈</span><span class="sxs-lookup"><span data-stu-id="bb5a1-103">JavaScript Azure Cognitive Services modules</span></span>

## <a name="vision-modules"></a><span data-ttu-id="bb5a1-104">비전 모듈</span><span class="sxs-lookup"><span data-stu-id="bb5a1-104">Vision modules</span></span>

### <a name="computer-vision"></a><span data-ttu-id="bb5a1-105">Computer Vision</span><span class="sxs-lookup"><span data-stu-id="bb5a1-105">Computer Vision</span></span> 

<span data-ttu-id="bb5a1-106">이미지에서 찾은 시각적 콘텐츠에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-106">Returns information about visual content found in an image:</span></span>

- <span data-ttu-id="bb5a1-107">태그 지정, 설명 및 도메인 특정 모델을 사용하여 자신 있게 콘텐츠를 파악하고 레이블을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-107">Use tagging, descriptions, and domain-specific models to identify content and label it with confidence.</span></span>
- <span data-ttu-id="bb5a1-108">성인 콘텐츠를 자동으로 제한할 수 있도록 성인/외설 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-108">Apply adult/racy settings to enable automated restriction of adult content.</span></span>
- <span data-ttu-id="bb5a1-109">사진의 이미지 형식과 색 구성표를 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-109">Identify image types and color schemes in pictures.</span></span>

<span data-ttu-id="bb5a1-110">브라우저에서 무료로 [Computer Vision을 사용](https://azure.microsoft.com/services/cognitive-services/computer-vision/)해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-110">[Try Computer Vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/) for free in your browser.</span></span>

<span data-ttu-id="bb5a1-111">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-111">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-computervision
```

<span data-ttu-id="bb5a1-112">Computer Vision API에 대해 [자세히 알아보고](/azure/cognitive-services/computer-vision/home) [Computer Vision API JavaScript 빠른 시작](/azure/cognitive-services/computer-vision/quickstarts/javascript)을 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-112">[Learn more](/azure/cognitive-services/computer-vision/home) about the Computer Vision API and get started with the [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span></span>

### <a name="content-moderator"></a><span data-ttu-id="bb5a1-113">Content Moderator</span><span class="sxs-lookup"><span data-stu-id="bb5a1-113">Content Moderator</span></span>

<span data-ttu-id="bb5a1-114">사용자 검토 도구로 확대된, 텍스트, 비디오 및 이미지의 기계 지원 조정.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-114">Machine-assisted moderation of text, video and images, augmented with human review tools.</span></span>

<span data-ttu-id="bb5a1-115">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-115">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-contentmoderator
```

<span data-ttu-id="bb5a1-116">Content Moderator 서비스에 대해 [자세히 알아보세요](/azure/cognitive-services/content-moderator/overview).</span><span class="sxs-lookup"><span data-stu-id="bb5a1-116">[Learn more](/azure/cognitive-services/content-moderator/overview) about the Content Moderator service.</span></span>

### <a name="face-api"></a><span data-ttu-id="bb5a1-117">Face API</span><span class="sxs-lookup"><span data-stu-id="bb5a1-117">Face API</span></span>

<span data-ttu-id="bb5a1-118">사진에서 얼굴을 감지, 식별, 분석, 구성하고 태그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-118">Detect, identify, analyze, organize, and tag faces in photos.</span></span> 

<span data-ttu-id="bb5a1-119">브라우저에서 [Face API를 사용](https://azure.microsoft.com/services/cognitive-services/face/)해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-119">[Try the Face API](https://azure.microsoft.com/services/cognitive-services/face/) in your browser.</span></span>

<span data-ttu-id="bb5a1-120">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-120">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-face
```

<span data-ttu-id="bb5a1-121">Face API에 대해 [자세히 알아보고](/azure/cognitive-services/face/overview) [Face API JavaScript 빠른 시작](/azure/cognitive-services/Face/quickstarts/javascript)을 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-121">[Learn more](/azure/cognitive-services/face/overview) about the Face API and get started with the [Face API JavaScript quickstart](/azure/cognitive-services/Face/quickstarts/javascript).</span></span>

## <a name="search-modules"></a><span data-ttu-id="bb5a1-122">검색 모듈</span><span class="sxs-lookup"><span data-stu-id="bb5a1-122">Search modules</span></span>

### <a name="web-search"></a><span data-ttu-id="bb5a1-123">Web Search</span><span class="sxs-lookup"><span data-stu-id="bb5a1-123">Web search</span></span>

<span data-ttu-id="bb5a1-124">Bing Web Search API로 인덱싱된 웹 문서를 검색하고 결과 형식, 최신성 등을 기준으로 결과의 범위를 축소해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-124">Retrieve web documents indexed by the Bing Web Search API and narrow down the results by result type, freshness and more.</span></span> 

<span data-ttu-id="bb5a1-125">브라우저에서 [Web Search API를 사용](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/)해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-125">[Try the Web Search API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) in your browser.</span></span>

<span data-ttu-id="bb5a1-126">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-126">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-websearch
```

<span data-ttu-id="bb5a1-127">Bing Web Search API에 대해 [자세히 알아보고](/azure/cognitive-services/bing-web-search/overview) [Web Search API Node.js 빠른 시작](/azure/cognitive-services/bing-web-search/quickstarts/nodejs)을 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-127">[Learn more](/azure/cognitive-services/bing-web-search/overview) about the Bing Web Search API and get started with the [Web Search API Node.js quickstart](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span></span>

### <a name="image-search"></a><span data-ttu-id="bb5a1-128">이미지 검색</span><span class="sxs-lookup"><span data-stu-id="bb5a1-128">Image search</span></span>

<span data-ttu-id="bb5a1-129">이미지를 검색하고 결과에 썸네일, 전체 이미지 URL, 이미지 메타데이터 등을 가져오세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-129">Search for images and get thumbnails, full image URLs, image metadata and more in your results.</span></span>

<span data-ttu-id="bb5a1-130">브라우저에서 [Image Search API를 사용](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/)해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-130">[Try the Image Search API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) in your browser.</span></span>

<span data-ttu-id="bb5a1-131">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-131">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-imagesearch
```

<span data-ttu-id="bb5a1-132">Bing Image Search API에 대해 [자세히 알아보고](/azure/cognitive-services/bing-image-search/overview) [Image Search API Node.js 빠른 시작](/azure/cognitive-services/bing-image-search/quickstarts/nodejs)을 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-132">[Learn more](/azure/cognitive-services/bing-image-search/overview) about the Bing Image Search API and get started with the [Image Search API Node.js quickstart](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span></span>


### <a name="entity-search"></a><span data-ttu-id="bb5a1-133">Entity Search</span><span class="sxs-lookup"><span data-stu-id="bb5a1-133">Entity search</span></span>

<span data-ttu-id="bb5a1-134">특정 검색어 또는 위치와 가장 관련 있는 엔터티(장소, 사람 또는 물건)를 검색하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-134">Search for the most relevant entity (place, person, or thing) for a given search term or location.</span></span>

<span data-ttu-id="bb5a1-135">브라우저에서 [Entity Search API를 사용](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/)해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-135">[Try the Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in your browser.</span></span>

<span data-ttu-id="bb5a1-136">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-136">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-entitysearch
```

<span data-ttu-id="bb5a1-137">Bing Entity Search API에 대해 [자세히 알아보고](/azure/cognitive-services/bing-entities-search/search-the-web) [Entity Search API Node.js 빠른 시작](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs)을 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-137">[Learn more](/azure/cognitive-services/bing-entities-search/search-the-web) about the Bing Entity Search API and get started with the [Entity Search API Node.js quickstart](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span></span>

### <a name="custom-search"></a><span data-ttu-id="bb5a1-138">Custom Search</span><span class="sxs-lookup"><span data-stu-id="bb5a1-138">Custom search</span></span>

<span data-ttu-id="bb5a1-139">특정 검색 도메인에 맞는 사용자 지정 웹 검색을 빌드해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-139">Build and a custom web search that meets your specific search domain.</span></span>

<span data-ttu-id="bb5a1-140">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-140">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-customsearch
```

<span data-ttu-id="bb5a1-141">Bing Custom Search 서비스에 대해 [자세히 알아보고](/azure/cognitive-services/bing-custom-search/) [Custom Search API Node.js 빠른 시작](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs)을 사용하여 앱에서 사용자 지정 검색 쿼리를 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-141">[Learn more](/azure/cognitive-services/bing-custom-search/) about the Bing Custom Search service and get started with querying your custom search from your apps with the [Custom Search API Node.js quickstart](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span></span>

### <a name="video-search"></a><span data-ttu-id="bb5a1-142">Video Search</span><span class="sxs-lookup"><span data-stu-id="bb5a1-142">Video search</span></span>

<span data-ttu-id="bb5a1-143">웹에서 비디오를 검색하고 작성자, 인코딩, 길이 및 조회수 메타데이터가 포함된 결과를 가져오세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-143">Find videos across the web and get results with creator, encoding, length, and view count metadata.</span></span>

<span data-ttu-id="bb5a1-144">브라우저에서 [Video Search API를 사용](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/)해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-144">[Try the Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in your browser.</span></span>

<span data-ttu-id="bb5a1-145">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-145">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-videosearch
```

<span data-ttu-id="bb5a1-146">Bing Video Search 서비스에 대해 [자세히 알아보고](/azure/cognitive-services/bing-video-search/search-the-web) [Video Search API Node.js 빠른 시작](/azure/cognitive-services/bing-video-search/nodejs)을 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-146">[Learn more](/azure/cognitive-services/bing-video-search/search-the-web) about the Bing Video Search service and get started with the [Video Search API Node.js quickstart](/azure/cognitive-services/bing-video-search/nodejs).</span></span>


### <a name="news-search"></a><span data-ttu-id="bb5a1-147">News Search</span><span class="sxs-lookup"><span data-stu-id="bb5a1-147">News search</span></span>

<span data-ttu-id="bb5a1-148">웹에서 뉴스 기사를 검색하고, 기사, 관련 뉴스, 이미지 및 공급자 정보 메타데이터로 작업하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-148">Search the web for news articles and work with article, related news, images, and provider info metadata.</span></span>

<span data-ttu-id="bb5a1-149">브라우저에서 [News Search API를 사용](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/)해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-149">[Try the News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in your browser.</span></span>

<span data-ttu-id="bb5a1-150">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-150">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-newssearch
```

<span data-ttu-id="bb5a1-151">Bing News Search 서비스에 대해 [자세히 알아보고](/azure/cognitive-services/bing-news-search/search-the-web) [News Search API JavaScript 빠른 시작](/azure/cognitive-services/bing-news-search/nodejs)을 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-151">[Learn more](/azure/cognitive-services/bing-news-search/search-the-web) about the Bing News Search service and get started with the [News Search API JavaScript quickstart](/azure/cognitive-services/bing-news-search/nodejs).</span></span>


## <a name="language-modules"></a><span data-ttu-id="bb5a1-152">언어 모듈</span><span class="sxs-lookup"><span data-stu-id="bb5a1-152">Language modules</span></span>

### <a name="text-analytics"></a><span data-ttu-id="bb5a1-153">텍스트 분석</span><span class="sxs-lookup"><span data-stu-id="bb5a1-153">Text Analytics</span></span> 

<span data-ttu-id="bb5a1-154">텍스트 분석 API는 원시 텍스트에 대한 자연어 처리를 제공하는 클라우드 기반 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-154">The Text Analytics API is a cloud-based service that provides  natural language processing over raw text.</span></span> <span data-ttu-id="bb5a1-155">이 API에는 세 가지 주요 기능이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-155">The API includes three main functions:</span></span>

- <span data-ttu-id="bb5a1-156">정서 분석</span><span class="sxs-lookup"><span data-stu-id="bb5a1-156">Sentiment analysis</span></span>
- <span data-ttu-id="bb5a1-157">핵심 문구 추출</span><span class="sxs-lookup"><span data-stu-id="bb5a1-157">Key phrase extraction</span></span>
- <span data-ttu-id="bb5a1-158">언어 검색</span><span class="sxs-lookup"><span data-stu-id="bb5a1-158">Language detection</span></span>

<span data-ttu-id="bb5a1-159">브라우저에서 [텍스트 분석 API를 사용](https://azure.microsoft.com/services/cognitive-services/text-analytics/)해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-159">[Try the Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) in your browser.</span></span>

<span data-ttu-id="bb5a1-160">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-160">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-textanalytics
```

<span data-ttu-id="bb5a1-161">텍스트 분석 API에 대해 [자세히 알아보고](/azure/cognitive-services/text-analytics/overview) [텍스트 분석 API Node.js 빠른 시작](/azure/cognitive-services/text-analytics/quickstarts/nodejs)을 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-161">[Learn more](/azure/cognitive-services/text-analytics/overview) about the Text Analytics API and get started with the [Text Analytics API Node.js quickstart](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span></span>


### <a name="spell-check"></a><span data-ttu-id="bb5a1-162">Spell Check</span><span class="sxs-lookup"><span data-stu-id="bb5a1-162">Spell Check</span></span>

<span data-ttu-id="bb5a1-163">Bing Spell Check API를 사용하여 상황별 문법 및 맞춤법 검사를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-163">Perform contextual grammar and spell checking with the Bing Spell Check API.</span></span>

<span data-ttu-id="bb5a1-164">브라우저에서 [Spell Check API를 사용](https://azure.microsoft.com/services/cognitive-services/spell-check/)해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-164">[Try the Spell Check API](https://azure.microsoft.com/services/cognitive-services/spell-check/) in your browser.</span></span>

<span data-ttu-id="bb5a1-165">[npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)을 사용하여 JavaScript 모듈을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-165">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-spellcheck
```

<span data-ttu-id="bb5a1-166">Spell Check API에 대해 [자세히 알아보고](/azure/cognitive-services/bing-spell-check/proof-text) [Spell Check API Node.js 빠른 시작](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs)을 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-166">[Learn more](/azure/cognitive-services/bing-spell-check/proof-text) about the Spell Check API and get started with the [Spell Check API Node.js quickstart](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span></span>

## <a name="samples"></a><span data-ttu-id="bb5a1-167">샘플</span><span class="sxs-lookup"><span data-stu-id="bb5a1-167">Samples</span></span>

<span data-ttu-id="bb5a1-168">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="bb5a1-168">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
