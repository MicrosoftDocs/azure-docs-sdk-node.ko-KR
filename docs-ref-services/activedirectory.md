---
title: "Node.js용 Azure Active Directory 모듈"
description: "Node.js용 Azure Active Directory 모듈에 대한 참조"
keywords: Azure, Node, SDK, API, Storage, NodeJS, JavaScript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: d0084faa78986bd5518526c6eb84b9c13fdb10bf
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Node.js용 Azure Active Directory 모듈

## <a name="overview"></a>개요

[Node.js용 Azure ADAL(Active Directory Authentication Library)(영문)](https://www.npmjs.com/package/adal-node)을 사용하면 Node.js 응용 프로그램에서 AAD에 인증하여 AAD 보호된 웹 리소스에 액세스할 수 있습니다.

## <a name="client-package"></a>클라이언트 패키지

### <a name="install-the-npm-modules"></a>npm 모듈 설치

npm을 사용하여 Azure 저장소 클라이언트 또는 관리 모듈을 설치합니다.

```bash
npm install adal-node
```   

### <a name="example"></a>예제

[클라이언트 자격 증명 샘플](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)의 이 예제에서는 클라이언트 자격 증명을 통한 서버 간 인증을 보여 줍니다.

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a>샘플

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
