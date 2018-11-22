---
title: Node.js용 Azure Advisor 모듈
description: Node.js용 Azure Advisor 모듈에 대한 참조
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 54686220006d27341dbb50a249d0b2f44411b112
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52116549"
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="c2f36-103">Node.js용 Azure Advisor 모듈</span><span class="sxs-lookup"><span data-stu-id="c2f36-103">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c2f36-104">개요</span><span class="sxs-lookup"><span data-stu-id="c2f36-104">Overview</span></span>

<span data-ttu-id="c2f36-105">Azure 관리자는 Azure 배포를 최적화하기 위한 모범 사례를 따르는 데 도움이 되는 개인 설정된 클라우드 컨설턴트입니다.</span><span class="sxs-lookup"><span data-stu-id="c2f36-105">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="c2f36-106">리소스 구성 및 사용량 원격 분석을 수행한 다음, Azure 리소스의 비용 효율성, 성능, 고가용성 및 보안을 향상시키는 데 도움이 되는 해결 방법을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f36-106">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="c2f36-107">Advisor를 사용하면 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2f36-107">With Advisor, you can:</span></span>
- <span data-ttu-id="c2f36-108">사전 대응이 가능하고, 실행 가능하고, 개인화된 모범 사례 권장 사항</span><span class="sxs-lookup"><span data-stu-id="c2f36-108">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="c2f36-109">전체 Azure 사용을 줄일 수 있는 기회를 모색하면서 성능, 보안 및 고가용성 개선</span><span class="sxs-lookup"><span data-stu-id="c2f36-109">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="c2f36-110">온라인으로 작업이 제안되는 권장 사항 가져오기</span><span class="sxs-lookup"><span data-stu-id="c2f36-110">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="c2f36-111">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="c2f36-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c2f36-112">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="c2f36-112">Install the npm module</span></span>

<span data-ttu-id="c2f36-113">Azure Advisor npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f36-113">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="c2f36-114">예</span><span class="sxs-lookup"><span data-stu-id="c2f36-114">Example</span></span>

<span data-ttu-id="c2f36-115">이 예제에서는 Azure Advisor의 권장 사항 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f36-115">This example displays the list of recommendations from Azure Advisor.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a><span data-ttu-id="c2f36-116">샘플</span><span class="sxs-lookup"><span data-stu-id="c2f36-116">Samples</span></span>

<span data-ttu-id="c2f36-117">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="c2f36-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
