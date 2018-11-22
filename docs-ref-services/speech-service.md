---
title: JavaScript용 Cognitive Services Speech SDK
description: JavaScript용 Cognitive Services Speech SDK 참조
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 09/24/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 69167faa5b2677fc15561ed33beccf7925efbe39
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52015527"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="b728a-103">JavaScript용 Cognitive Services Speech SDK</span><span class="sxs-lookup"><span data-stu-id="b728a-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="b728a-104">개요</span><span class="sxs-lookup"><span data-stu-id="b728a-104">Overview</span></span>

<span data-ttu-id="b728a-105">음성 지원 응용 프로그램의 개발을 간소화하기 위해 Microsoft는 Speech 서비스에서 사용할 [Speech SDK](https://aka.ms/csspeech)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b728a-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="b728a-106">Speech SDK는 일관된 네이티브 Speech to Text 및 Speech Translation API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b728a-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="b728a-107">Cognitive Services Speech SDK는 현재 브라우저에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b728a-107">The Cognitive Services Speech SDK is currently available only for browsers.</span></span>
> <span data-ttu-id="b728a-108">NPM 패키지가 곧 뒤따를 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b728a-108">An NPM package will follow soon.</span></span>

### <a name="install-the-speech-sdk"></a><span data-ttu-id="b728a-109">Speech SDK 설치하기</span><span class="sxs-lookup"><span data-stu-id="b728a-109">Install the Speech SDK</span></span>

<span data-ttu-id="b728a-110">Speech SDK를 [.zip 패키지](https://aka.ms/csspeech/jsbrowserpackage)로 다운로드하여 압축 해체합니다.</span><span class="sxs-lookup"><span data-stu-id="b728a-110">Download the Speech SDK as a [.zip package](https://aka.ms/csspeech/jsbrowserpackage) and unpack it.</span></span>
<span data-ttu-id="b728a-111">이렇게 하면 `microsoft.cognitiveservices.speech.sdk.bundle.js` 파일을 포함하여 여러 개의 파일이 압축 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b728a-111">This should result in a number of files being unpacked including a file named `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span></span>
<span data-ttu-id="b728a-112">Speech SDK를 사용하려면 웹 페이지에서 스크립트 리소스로 이 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="b728a-112">Load this file as a script resource in your web page to start using the Speech SDK:</span></span>

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a><span data-ttu-id="b728a-113">예</span><span class="sxs-lookup"><span data-stu-id="b728a-113">Example</span></span> 

<span data-ttu-id="b728a-114">다음 코드 조각에서는 브라우저에서 간단한 speech 인식을 수행하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="b728a-114">The following code snippets illustrates how to do simple speech recognition from your browser:</span></span>

```javascript 
var SpeechSDK = window.SpeechSDK;
var speechConfig = SpeechSDK.SpeechConfig.fromSubscription("your-subscription-key", "your-service-region");
speechConfig.language = "en-US";
var audioConfig = SpeechSDK.AudioConfig.fromDefaultMicrophoneInput();
recognizer = new SpeechSDK.SpeechRecognizer(speechConfig, audioConfig);

recognizer.recognizeOnceAsync(
  function (result) {
    alert("Recognition result:" + JSON.stringify(result));
    recognizer.close();
  },
  function (err) {
    alert("An error occurred:" + JSON.stringify(err));
    recognizer.close();
  }
);
``` 

<span data-ttu-id="b728a-115">[단계별 빠른 시작](/azure/cognitive-services/speech-service/quickstart-js-browser)을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b728a-115">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>

## <a name="samples"></a><span data-ttu-id="b728a-116">샘플</span><span class="sxs-lookup"><span data-stu-id="b728a-116">Samples</span></span>

<span data-ttu-id="b728a-117">[Speech SDK 샘플 리포지토리](https://aka.ms/csspeech/samples)에서 더 많은 샘플 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="b728a-117">Explore more samples in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
