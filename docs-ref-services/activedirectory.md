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
ms.sourcegitcommit: 0d439a88f38a085e2be0616c8bdb0ffcca2e54ad
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2018
ms.locfileid: "48915651"
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="095a2-103">Node.js용 Azure Active Directory 모듈</span><span class="sxs-lookup"><span data-stu-id="095a2-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="095a2-104">개요</span><span class="sxs-lookup"><span data-stu-id="095a2-104">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="095a2-105">Azure Active Directory 리소스에 액세스하려면 Azure AD Graph API 대신 [Microsoft Graph](https://graph.microsoft.io/)를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="095a2-105">We strongly recommend that you use [Microsoft Graph](https://graph.microsoft.io/) instead of Azure AD Graph API to access Azure Active Directory resources.</span></span> <span data-ttu-id="095a2-106">이제 Microsoft는 Azure AD Graph API를 더 이상 개선하지 않을 것이며 Microsoft Graph에 주력하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="095a2-106">Our development efforts are now concentrated on Microsoft Graph and no further enhancements are planned for Azure AD Graph API.</span></span> <span data-ttu-id="095a2-107">Azure AD Graph API가 적절할 수 있는 시나리오는 매우 제한적입니다. 자세한 내용은 Office 개발자 센터에서 [Microsoft Graph 또는 Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) 블로그 게시물을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="095a2-107">There are a very limited number of scenarios for which Azure AD Graph API might still be appropriate; for more information, see the [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) blog post in the Office Dev Center.</span></span>

<span data-ttu-id="095a2-108">[Node.js용 Azure ADAL(Active Directory Authentication Library)(영문)](https://www.npmjs.com/package/adal-node)을 사용하면 Node.js 응용 프로그램에서 AAD에 인증하여 AAD 보호된 웹 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="095a2-108">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="095a2-109">클라이언트 패키지</span><span class="sxs-lookup"><span data-stu-id="095a2-109">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="095a2-110">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="095a2-110">Install the npm modules</span></span>

<span data-ttu-id="095a2-111">npm을 사용하여 Azure 저장소 클라이언트 또는 관리 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="095a2-111">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="095a2-112">예</span><span class="sxs-lookup"><span data-stu-id="095a2-112">Example</span></span>

<span data-ttu-id="095a2-113">[클라이언트 자격 증명 샘플](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js)의 이 예제에서는 클라이언트 자격 증명을 통한 서버 간 인증을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="095a2-113">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="095a2-114">샘플</span><span class="sxs-lookup"><span data-stu-id="095a2-114">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="095a2-115">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="095a2-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
