---
title: "Node.js용 Azure App Service 모듈"
description: "Node.js용 Azure App Service 모듈에 대한 참조"
keywords: Azure, Node, SDK, API, Web Apps, Mobile, NodeJS, JavaScript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: c695ae6d523ea731b18382ba0906f78b40ce301f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="470fb-104">Node.js용 Azure App Service 모듈</span><span class="sxs-lookup"><span data-stu-id="470fb-104">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="470fb-105">개요</span><span class="sxs-lookup"><span data-stu-id="470fb-105">Overview</span></span>

<span data-ttu-id="470fb-106">Azure App Service는 Microsoft Azure의 PaaS(Platform-as-a-Service) 제품입니다.</span><span class="sxs-lookup"><span data-stu-id="470fb-106">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="470fb-107">플랫폼 및 장치에 웹 및 모바일 앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="470fb-107">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="470fb-108">SaaS 솔루션과 앱을 통합하고 온-프레미스 응용 프로그램을 사용하여 연결하고 비즈니스 프로세스를 자동화합니다.</span><span class="sxs-lookup"><span data-stu-id="470fb-108">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="470fb-109">Azure는 공유 VM 리소스 또는 전용 VM을 선택하여 완전히 관리되는 VM(가상 컴퓨터)에서 앱을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="470fb-109">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="470fb-110">앱 서비스는 이전에 개별적으로 Azure 웹 사이트 및 Azure 모바일 서비스로 전달한 웹 및 모바일 기능을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="470fb-110">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="470fb-111">또한 비즈니스 프로세스를 자동화하고 클라우드 API를 호스팅하는 새 기능을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="470fb-111">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="470fb-112">단일 통합 서비스인 앱 서비스를 통해 웹 사이트, 모바일 앱 백 엔드, RESTful API 및 비즈니스 프로세스 등 다양한 구성 요소를 단일 솔루션으로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="470fb-112">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="470fb-113">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="470fb-113">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="470fb-114">npm 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="470fb-114">Install the npm package</span></span>

<span data-ttu-id="470fb-115">Node.js용 Azure App Service 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="470fb-115">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="470fb-116">예제</span><span class="sxs-lookup"><span data-stu-id="470fb-116">Example</span></span>

<span data-ttu-id="470fb-117">이 예제에서는 Node.js를 사용하여 Azure에 웹 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="470fb-117">This example creates a website on Azure using Node.js.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a><span data-ttu-id="470fb-118">샘플</span><span class="sxs-lookup"><span data-stu-id="470fb-118">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="470fb-119">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="470fb-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
