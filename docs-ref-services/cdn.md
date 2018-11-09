---
title: Node.js용 Azure CDN 모듈
description: Node.js용 Azure CDN 모듈에 대한 참조
author: dksimpson
ms.author: v-deasim
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: 1117f8fabfe364d3e5602ee89f652fe98851fef4
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51178882"
---
# <a name="azure-cdn-modules-for-nodejs"></a>Node.js용 Azure CDN 모듈

## <a name="overview"></a>개요

Azure CDN(Content Delivery Network)은 Azure 또는 다른 위치에서 호스팅되는 고대역폭 콘텐츠를 개발자에게 제공하는 글로벌 솔루션을 제공합니다. CDN을 사용하여 Azure Blob Storage, 웹 응용 프로그램, 가상 머신, 응용 프로그램 폴더 또는 기타 HTTP/HTTPS 위치에서 로드된 공개적으로 사용 가능한 개체를 캐시할 수 있습니다. 전략적 위치에 CDN 캐시를 보유하여 사용자에게 콘텐츠를 배달하기 위해 최대 대역폭을 제공할 수 있습니다. CDN은 일반적으로 이미지, 스타일 시트, 문서, 파일, 클라이언트쪽 스크립트 및 HTML 페이지와 같은 정적 콘텐츠를 제공하기 위해 사용됩니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure CDN npm 모듈을 설치합니다.

```bash
npm install azure-arm-cdn
```

### <a name="example"></a>예

이 예제에서는 모든 CDN 프로필을 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
