---
title: Node.js용 Azure Media Services 모듈
description: Node.js용 Azure Media Services 모듈에 대한 참조
author: Juliako
ms.author: juliako
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: bfd4402c215a81c9ed8753cfe9ad9dbfaa52bd6f
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52145808"
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="bda51-103">Node.js용 Azure Media Services 모듈</span><span class="sxs-lookup"><span data-stu-id="bda51-103">Azure Media Services modules for Node.js</span></span>

<span data-ttu-id="bda51-104">Azure Media Services는 개발자가 확장 가능한 미디어 관리 및 배달 애플리케이션을 빌드할 수 있는 확장 가능한 클라우드 기반 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-104">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="bda51-105">Media Services는 다양한 클라이언트(예: TV, PC 및 모바일 디바이스)로의 주문형 및 라이브 스트리밍 배달을 위해 비디오 또는 오디오 콘텐츠를 안전하게 업로드, 저장, 인코딩 및 패키지할 수 있는 REST API를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-105">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="bda51-106">Azure Media Services를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-106">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="bda51-107">Media Services를 전적으로 사용하여 종단 간 워크플로를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-107">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="bda51-108">워크플로의 일부에 타사 구성 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-108">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="bda51-109">예를 들어 타사 인코더를 사용하여 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-109">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="bda51-110">그런 다음 Media Services를 사용하여 업로드, 보호, 패키징 및 배달합니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-110">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="bda51-111">콘텐츠를 라이브로 스트리밍하거나 주문형 콘텐츠를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-111">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="bda51-112">이 항목은 관련 항목으로도 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-112">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="bda51-113">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="bda51-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bda51-114">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="bda51-114">Install the npm module</span></span>

<span data-ttu-id="bda51-115">Azure Media Services npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-115">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="bda51-116">예</span><span class="sxs-lookup"><span data-stu-id="bda51-116">Example</span></span>

<span data-ttu-id="bda51-117">이 예제에서는 리소스 그룹에 대한 모든 Media Services를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-117">This example lists all media services for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a><span data-ttu-id="bda51-118">샘플</span><span class="sxs-lookup"><span data-stu-id="bda51-118">Samples</span></span>

<span data-ttu-id="bda51-119">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="bda51-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
