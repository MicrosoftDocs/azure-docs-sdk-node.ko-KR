---
title: "Node.js용 Azure Operational Insights 모듈"
description: "Node.js용 Azure Operational Insights 모듈에 대한 참조"
keywords: Azure, SDK, API, Operational Insights, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="1a32a-104">Node.js용 Azure Operational Insights 모듈</span><span class="sxs-lookup"><span data-stu-id="1a32a-104">Azure Operational Insights Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1a32a-105">개요</span><span class="sxs-lookup"><span data-stu-id="1a32a-105">Overview</span></span>

## <a name="management-package"></a><span data-ttu-id="1a32a-106">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="1a32a-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1a32a-107">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="1a32a-107">Install the npm module</span></span>

<span data-ttu-id="1a32a-108">npm을 사용하여 Node.js용 Azure Operational Insights 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1a32a-108">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="1a32a-109">예제</span><span class="sxs-lookup"><span data-stu-id="1a32a-109">Example</span></span> 

<span data-ttu-id="1a32a-110">이 예제에서는 클라이언트를 만들고, Operational Insights에 연결하고, 지정된 리소스 그룹별로 작업 영역 목록을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1a32a-110">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a><span data-ttu-id="1a32a-111">샘플</span><span class="sxs-lookup"><span data-stu-id="1a32a-111">Samples</span></span>

<span data-ttu-id="1a32a-112">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="1a32a-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
