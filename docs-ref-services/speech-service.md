---
title: JavaScript용 Cognitive Services Speech SDK
description: JavaScript용 Cognitive Services Speech SDK 참조
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 12/18/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 43a6921d4ec782287cc041ecaabab4567b0fe677
ms.sourcegitcommit: 74417c10aee8987c3e0343728efac75823c902d9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54185990"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="03c71-103">JavaScript용 Cognitive Services Speech SDK</span><span class="sxs-lookup"><span data-stu-id="03c71-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="03c71-104">개요</span><span class="sxs-lookup"><span data-stu-id="03c71-104">Overview</span></span>

<span data-ttu-id="03c71-105">음성 지원 애플리케이션의 개발을 간소화하기 위해 Microsoft는 Speech 서비스에서 사용할 [Speech SDK](https://aka.ms/csspeech)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="03c71-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="03c71-106">Speech SDK는 일관된 네이티브 Speech to Text 및 Speech Translation API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="03c71-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="03c71-107">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="03c71-107">Install the npm module</span></span>

<span data-ttu-id="03c71-108">Cognitive Services Speech SDK npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="03c71-108">Install the Cognitive Services Speech SDK npm module</span></span>

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a><span data-ttu-id="03c71-109">예</span><span class="sxs-lookup"><span data-stu-id="03c71-109">Example</span></span> 

<span data-ttu-id="03c71-110">다음 코드 조각에서는 파일에서 간단한 음성 인식을 수행하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="03c71-110">The following code snippets illustrates how to do simple speech recognition from a file:</span></span>

```javascript 
// Pull in the required packages.
var sdk = require("microsoft-cognitiveservices-speech-sdk");
var fs = require("fs");

// Replace with your own subscription key, service region (e.g., "westus"), and
// the name of the file you want to run through the speech recognizer.
var subscriptionKey = "YourSubscriptionKey";
var serviceRegion = "YourServiceRegion"; // e.g., "westus"
var filename = "YourAudioFile.wav"; // 16000 Hz, Mono

// Create the push stream we need for the speech sdk.
var pushStream = sdk.AudioInputStream.createPushStream();

// Open the file and push it to the push stream.
fs.createReadStream(filename).on('data', function(arrayBuffer) {
  pushStream.write(arrayBuffer.buffer);
}).on('end', function() {
  pushStream.close();
});

// We are done with the setup
console.log("Now recognizing from: " + filename);

// Create the audio-config pointing to our stream and
// the speech config specifying the language.
var audioConfig = sdk.AudioConfig.fromStreamInput(pushStream);
var speechConfig = sdk.SpeechConfig.fromSubscription(subscriptionKey, serviceRegion);

// Setting the recognition language to English.
speechConfig.speechRecognitionLanguage = "en-US";

// Create the speech recognizer.
var recognizer = new sdk.SpeechRecognizer(speechConfig, audioConfig);

// Start the recognizer and wait for a result.
recognizer.recognizeOnceAsync(
  function (result) {
    console.log(result);

    recognizer.close();
    recognizer = undefined;
  },
  function (err) {
    console.trace("err - " + err);

    recognizer.close();
    recognizer = undefined;
  });
``` 

<span data-ttu-id="03c71-111">[단계별 빠른 시작](/azure/cognitive-services/speech-service/quickstart-js-node)을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="03c71-111">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>

## <a name="samples"></a><span data-ttu-id="03c71-112">샘플</span><span class="sxs-lookup"><span data-stu-id="03c71-112">Samples</span></span>

* <span data-ttu-id="03c71-113">[Node.js용 단계별 빠른 시작](/azure/cognitive-services/speech-service/quickstart-js-node).</span><span class="sxs-lookup"><span data-stu-id="03c71-113">[Step-by-step quickstart for Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>
* <span data-ttu-id="03c71-114">[브라우저용 단계별 빠른 시작](/azure/cognitive-services/speech-service/quickstart-js-browser).</span><span class="sxs-lookup"><span data-stu-id="03c71-114">[Step-by-step quickstart for the browser](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>
* <span data-ttu-id="03c71-115">[Speech SDK 샘플 리포지토리](https://aka.ms/csspeech/samples)에서 더 많은 샘플을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03c71-115">More samples can be found in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
