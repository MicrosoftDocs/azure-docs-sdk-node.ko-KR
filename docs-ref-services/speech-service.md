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
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50402389"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>JavaScript용 Cognitive Services Speech SDK

## <a name="overview"></a>개요

음성 지원 응용 프로그램의 개발을 간소화하기 위해 Microsoft는 Speech 서비스에서 사용할 [Speech SDK](https://aka.ms/csspeech)를 제공합니다.
Speech SDK는 일관된 네이티브 Speech to Text 및 Speech Translation API를 제공합니다.

> [!NOTE]
> Cognitive Services Speech SDK는 현재 브라우저에 대해서만 사용할 수 있습니다.
> NPM 패키지가 곧 뒤따를 예정입니다.

### <a name="install-the-speech-sdk"></a>Speech SDK 설치하기

Speech SDK를 [.zip 패키지](https://aka.ms/csspeech/jsbrowserpackage)로 다운로드하여 압축 해체합니다.
이렇게 하면 `microsoft.cognitiveservices.speech.sdk.bundle.js` 파일을 포함하여 여러 개의 파일이 압축 해제됩니다.
Speech SDK를 사용하려면 웹 페이지에서 스크립트 리소스로 이 파일을 로드합니다.

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a>예 

다음 코드 조각에서는 브라우저에서 간단한 speech 인식을 수행하는 방법을 보여줍니다.

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

[단계별 빠른 시작](/azure/cognitive-services/speech-service/quickstart-js-browser)을 확인합니다.

## <a name="samples"></a>샘플

[Speech SDK 샘플 리포지토리](https://aka.ms/csspeech/samples)에서 더 많은 샘플 탐색합니다.
