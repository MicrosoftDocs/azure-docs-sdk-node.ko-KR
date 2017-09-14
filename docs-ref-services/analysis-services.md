---
title: "Node.js용 Azure Analysis Services 모듈"
description: "Node.js용 Azure Analysis Services 모듈에 대한 참조"
keywords: Azure, SDK, API, Analysis Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: ff38883eed2de5d95fb5bd5fd951c6b9564a4b35
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="e6aac-104">Node.js용 Azure Analysis Services 모듈</span><span class="sxs-lookup"><span data-stu-id="e6aac-104">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e6aac-105">개요</span><span class="sxs-lookup"><span data-stu-id="e6aac-105">Overview</span></span>
<span data-ttu-id="e6aac-106">이 패키지는 Microsoft Azure Analysis Services를 쉽게 관리할 수 있게 하는 Node.js를 모듈을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e6aac-106">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="e6aac-107">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="e6aac-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e6aac-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="e6aac-108">Install the npm module</span></span>

<span data-ttu-id="e6aac-109">Azure Analysis Services npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e6aac-109">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="e6aac-110">예제</span><span class="sxs-lookup"><span data-stu-id="e6aac-110">Example</span></span>

<span data-ttu-id="e6aac-111">이 예제에서는 사용 가능한 모든 Analysis Services 서버를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e6aac-111">This example lists all available Analysis Service servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a><span data-ttu-id="e6aac-112">샘플</span><span class="sxs-lookup"><span data-stu-id="e6aac-112">Samples</span></span>

<span data-ttu-id="e6aac-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="e6aac-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
