---
title: Node.js용 Azure Monitor 모듈
description: Node.js용 Azure Monitor 모듈에 대한 참조
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: fb2cc5ba927fe03fb5fe3114919ed1b0b6e969ae
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49670778"
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="bd492-103">Node.js용 Azure Monitor 모듈</span><span class="sxs-lookup"><span data-stu-id="bd492-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="bd492-104">클라우드 응용 프로그램은 이동하는 부분이 많아 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="bd492-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="bd492-105">모니터링은 응용 프로그램을 유지하고 정상 상태에서 실행할 수 있는 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bd492-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="bd492-106">또한 잠재적 문제를 방지하거나 지난 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd492-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="bd492-107">또한 응용 프로그램에 대해 깊이 이해하는 데 모니터링 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd492-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="bd492-108">이러한 정보를 통해 응용 프로그램 성능이나 유지 관리를 개선하거나 그렇지 않으면 수동 개입이 필요한 작업을 자동화하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd492-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="bd492-109">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="bd492-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="bd492-110">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="bd492-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="bd492-111">예</span><span class="sxs-lookup"><span data-stu-id="bd492-111">Example</span></span>

<span data-ttu-id="bd492-112">이 코드 예제에서는 리소스 그룹과 연결된 모든 경고 규칙을 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="bd492-112">This code example prints all the alerting rules associated with a resource group.</span></span>

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

### <a name="samples"></a><span data-ttu-id="bd492-113">샘플</span><span class="sxs-lookup"><span data-stu-id="bd492-113">Samples</span></span>

<span data-ttu-id="bd492-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="bd492-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
