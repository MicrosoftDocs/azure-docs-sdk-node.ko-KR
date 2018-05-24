---
title: Node.js용 Azure Analysis Services 모듈
description: Node.js용 Azure Analysis Services 모듈에 대한 참조
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 166d0450ac9b2d005f3ce4ecba5ce36e1786ae09
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="e789b-103">Node.js용 Azure Analysis Services 모듈</span><span class="sxs-lookup"><span data-stu-id="e789b-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e789b-104">개요</span><span class="sxs-lookup"><span data-stu-id="e789b-104">Overview</span></span>
<span data-ttu-id="e789b-105">이 패키지는 Microsoft Azure Analysis Services를 쉽게 관리할 수 있게 하는 Node.js를 모듈을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e789b-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="e789b-106">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="e789b-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e789b-107">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="e789b-107">Install the npm module</span></span>

<span data-ttu-id="e789b-108">Azure Analysis Services npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e789b-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="e789b-109">예</span><span class="sxs-lookup"><span data-stu-id="e789b-109">Example</span></span>

<span data-ttu-id="e789b-110">이 예제에서는 사용 가능한 모든 Analysis Services 서버를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e789b-110">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e789b-111">샘플</span><span class="sxs-lookup"><span data-stu-id="e789b-111">Samples</span></span>

<span data-ttu-id="e789b-112">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="e789b-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
