---
title: "Node.js용 Azure Monitor 모듈"
description: "Node.js용 Azure Monitor 모듈에 대한 참조"
keywords: Azure, SDK, API, Monitor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8d27d837bddaa5258dde47b769cf601f6f5a861f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="bb85d-104">Node.js용 Azure Monitor 모듈</span><span class="sxs-lookup"><span data-stu-id="bb85d-104">Azure Monitor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bb85d-105">개요</span><span class="sxs-lookup"><span data-stu-id="bb85d-105">Overview</span></span>
<span data-ttu-id="bb85d-106">클라우드 응용 프로그램은 이동하는 부분이 많아 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="bb85d-106">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="bb85d-107">모니터링은 응용 프로그램을 유지하고 정상 상태에서 실행할 수 있는 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bb85d-107">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="bb85d-108">또한 잠재적 문제를 방지하거나 지난 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb85d-108">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="bb85d-109">또한 응용 프로그램에 대해 깊이 이해하는 데 모니터링 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb85d-109">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="bb85d-110">이러한 정보를 통해 응용 프로그램 성능이나 유지 관리를 개선하거나 그렇지 않으면 수동 개입이 필요한 작업을 자동화하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb85d-110">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="bb85d-111">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="bb85d-111">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="bb85d-112">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="bb85d-112">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="bb85d-113">예제</span><span class="sxs-lookup"><span data-stu-id="bb85d-113">Example</span></span>

<span data-ttu-id="bb85d-114">이 코드 예제에서는 리소스 그룹과 연결된 모든 경고 규칙을 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="bb85d-114">This code example prints all the alerting rules associated with a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });

```

### <a name="samples"></a><span data-ttu-id="bb85d-115">샘플</span><span class="sxs-lookup"><span data-stu-id="bb85d-115">Samples</span></span>

<span data-ttu-id="bb85d-116">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="bb85d-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
