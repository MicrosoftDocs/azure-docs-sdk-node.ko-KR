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
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="d23ff-104">Node.js용 Azure Active Directory 모듈</span><span class="sxs-lookup"><span data-stu-id="d23ff-104">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d23ff-105">개요</span><span class="sxs-lookup"><span data-stu-id="d23ff-105">Overview</span></span>

<span data-ttu-id="d23ff-106">[Node.js용 Azure ADAL(Active Directory Authentication Library)(영문)](https://www.npmjs.com/package/adal-node)을 사용하면 Node.js 응용 프로그램에서 AAD에 인증하여 AAD 보호된 웹 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d23ff-106">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="d23ff-107">클라이언트 패키지</span><span class="sxs-lookup"><span data-stu-id="d23ff-107">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="d23ff-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="d23ff-108">Install the npm modules</span></span>

<span data-ttu-id="d23ff-109">npm을 사용하여 Azure 저장소 클라이언트 또는 관리 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d23ff-109">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="d23ff-110">예제</span><span class="sxs-lookup"><span data-stu-id="d23ff-110">Example</span></span>

<span data-ttu-id="d23ff-111">[클라이언트 자격 증명 샘플](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)의 이 예제에서는 클라이언트 자격 증명을 통한 서버 간 인증을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d23ff-111">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d23ff-112">샘플</span><span class="sxs-lookup"><span data-stu-id="d23ff-112">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="d23ff-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="d23ff-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
