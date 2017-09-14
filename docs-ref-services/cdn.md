---
title: "Node.js용 Azure CDN 모듈"
description: "Node.js용 Azure CDN 모듈에 대한 참조"
keywords: Azure, SDK, API, CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="9c1f8-104">Node.js용 Azure CDN 모듈</span><span class="sxs-lookup"><span data-stu-id="9c1f8-104">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9c1f8-105">개요</span><span class="sxs-lookup"><span data-stu-id="9c1f8-105">Overview</span></span>

<span data-ttu-id="9c1f8-106">Azure CDN(Content Delivery Network)은 Azure 또는 다른 위치에서 호스팅되는 고대역폭 콘텐츠를 개발자에게 제공하는 글로벌 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1f8-106">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="9c1f8-107">CDN을 사용하여 Azure Blob Storage, 웹 응용 프로그램, 가상 컴퓨터, 응용 프로그램 폴더 또는 기타 HTTP/HTTPS 위치에서 로드된 공개적으로 사용 가능한 개체를 캐시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c1f8-107">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="9c1f8-108">전략적 위치에 CDN 캐시를 보유하여 사용자에게 콘텐츠를 배달하기 위해 최대 대역폭을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c1f8-108">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="9c1f8-109">CDN은 일반적으로 이미지, 스타일 시트, 문서, 파일, 클라이언트쪽 스크립트 및 HTML 페이지와 같은 정적 콘텐츠를 제공하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c1f8-109">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="9c1f8-110">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="9c1f8-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9c1f8-111">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="9c1f8-111">Install the npm module</span></span>

<span data-ttu-id="9c1f8-112">Azure CDN npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1f8-112">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="9c1f8-113">예제</span><span class="sxs-lookup"><span data-stu-id="9c1f8-113">Example</span></span>

<span data-ttu-id="9c1f8-114">이 예제에서는 모든 CDN 프로필을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1f8-114">This example lists all of the CDN profiles.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9c1f8-115">샘플</span><span class="sxs-lookup"><span data-stu-id="9c1f8-115">Samples</span></span>

<span data-ttu-id="9c1f8-116">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1f8-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
