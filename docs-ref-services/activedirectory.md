---
title: Node.js용 Azure Active Directory 모듈
description: Node.js용 Azure Active Directory 모듈에 대한 참조
author: celestedg
ms.author: celested
manager: mtillman
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.openlocfilehash: 1189bf084fc7d77a1e5eed7f01f2f9bee2295b45
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406429"
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Node.js용 Azure Active Directory 모듈

## <a name="overview"></a>개요

> [!IMPORTANT]
> Azure Active Directory 리소스에 액세스하려면 Azure AD Graph API 대신 [Microsoft Graph](https://graph.microsoft.io/)를 사용하는 것이 좋습니다. 이제 Microsoft는 Azure AD Graph API를 더 이상 개선하지 않을 것이며 Microsoft Graph에 주력하고 있습니다. Azure AD Graph API가 적절할 수 있는 시나리오는 매우 제한적입니다. 자세한 내용은 Office 개발자 센터에서 [Microsoft Graph 또는 Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) 블로그 게시물을 참조하세요.

[Node.js용 Azure ADAL(Active Directory Authentication Library)(영문)](https://www.npmjs.com/package/adal-node)을 사용하면 Node.js 응용 프로그램에서 AAD에 인증하여 AAD 보호된 웹 리소스에 액세스할 수 있습니다.

## <a name="client-package"></a>클라이언트 패키지

### <a name="install-the-npm-modules"></a>npm 모듈 설치

npm을 사용하여 Azure 저장소 클라이언트 또는 관리 모듈을 설치합니다.

```bash
npm install adal-node
```   

### <a name="example"></a>예

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
