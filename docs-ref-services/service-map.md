---
title: Node.js용 Azure 서비스 맵 모듈
description: Node.js용 Azure 서비스 맵 모듈에 대한 참조
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: db064603e32446ba2f094da2a1601520b99a7304
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265984"
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="b373c-103">Node.js용 Azure 서비스 맵 모듈</span><span class="sxs-lookup"><span data-stu-id="b373c-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="b373c-104">서비스 맵은 Windows 및 Linux 시스템에서 응용 프로그램 구성 요소를 자동으로 검색하고 서비스 간 통신을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="b373c-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="b373c-105">서비스 맵은 서버, 프로세스 및 에이전트 설치 이외에 구성이 필요 없는 TCP 연결 아키텍처의 포트 간 연결을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b373c-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="b373c-106">[서비스 맵](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="b373c-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="b373c-107">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="b373c-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b373c-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="b373c-108">Install the npm module</span></span>

<span data-ttu-id="b373c-109">Azure 서비스 맵 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b373c-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="b373c-110">예</span><span class="sxs-lookup"><span data-stu-id="b373c-110">Example</span></span>

<span data-ttu-id="b373c-111">이 예제에서는 지정된 리소스 그룹 및 작업 영역에 대한 모든 서비스 맵을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b373c-111">This example lists all service maps for the specified resource group and workspace.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a><span data-ttu-id="b373c-112">샘플</span><span class="sxs-lookup"><span data-stu-id="b373c-112">Samples</span></span>

<span data-ttu-id="b373c-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="b373c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
