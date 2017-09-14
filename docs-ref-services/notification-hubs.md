---
title: "Node.js용 Azure Notification Hubs 모듈"
description: "Node.js용 Azure Notification Hubs 모듈에 대한 참조"
keywords: Azure, SDK, API, Notification Hubs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 0141760cb93c77faed4a04893fe1376e4e75c361
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="7ca3b-104">Node.js용 Azure Notification Hubs 모듈</span><span class="sxs-lookup"><span data-stu-id="7ca3b-104">Azure Notification Hubs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7ca3b-105">개요</span><span class="sxs-lookup"><span data-stu-id="7ca3b-105">Overview</span></span>

<span data-ttu-id="7ca3b-106">Azure Notification Hubs는 사용하기 쉬운 다중 플랫폼의 확장된 푸시 엔진을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-106">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="7ca3b-107">단일 플랫폼 간 API 호출을 통해 클라우드 또는 온-프레미스 백 엔드에서 모든 모바일 플랫폼으로 개인 설정된 대상 푸시 알림을 쉽게 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-107">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="7ca3b-108">Notification Hubs는 엔터프라이즈 시나리오 및 소비자 시나리오 모두에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-108">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="7ca3b-109">다음은 고객이 Notification Hubs를 사용하는 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-109">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="7ca3b-110">수백만 명의 사용자에게 대기 시간이 짧은 최신 뉴스 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-110">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="7ca3b-111">관심 있는 사용자 세그먼트에 위치 기반 쿠폰을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-111">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="7ca3b-112">미디어/스포츠/금융/게임 응용 프로그램을 위해 사용자 또는 그룹에 이벤트 관련 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-112">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="7ca3b-113">프로모션 콘텐츠를 앱에 푸시하여 고객을 참여시키고 마케팅 활동을 전개합니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-113">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="7ca3b-114">새 메시지 및 작업 항목과 같은 엔터프라이즈 이벤트를 사용자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-114">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="7ca3b-115">다단계 인증을 위한 코드를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-115">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="7ca3b-116">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="7ca3b-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7ca3b-117">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="7ca3b-117">Install the npm module</span></span>

<span data-ttu-id="7ca3b-118">Azure Notification Hubs 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-118">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="7ca3b-119">예제</span><span class="sxs-lookup"><span data-stu-id="7ca3b-119">Example</span></span>

<span data-ttu-id="7ca3b-120">이 예제에서는 모든 알림 허브를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-120">This example lists all notification hubs.</span></span>

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a><span data-ttu-id="7ca3b-121">샘플</span><span class="sxs-lookup"><span data-stu-id="7ca3b-121">Samples</span></span>

* [<span data-ttu-id="7ca3b-122">Node.js 백 엔드용 App Service Mobile Apps 빠른 시작 완성(영문)</span><span class="sxs-lookup"><span data-stu-id="7ca3b-122">App Service Mobile completed quickstart for Node.js backend</span></span>](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [<span data-ttu-id="7ca3b-123">Node.js를 실행하는 Intel Edison의 데이터에서 Azure IoT 서비스로 검색된 진동 이상 트윗(영문)</span><span class="sxs-lookup"><span data-stu-id="7ca3b-123">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="7ca3b-124">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
