---
title: Node.js용 Azure Logic Apps 모듈
description: Node.js용 Azure Logic Apps 모듈에 대한 참조
author: ecfan
ms.author: estfan
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 021f57c7f4f1b86a3c0e97f345d2f934351669b8
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50281536"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="83dbb-103">Node.js용 Azure Logic Apps 모듈</span><span class="sxs-lookup"><span data-stu-id="83dbb-103">Azure Logic Apps modules for Node.js</span></span>

<span data-ttu-id="83dbb-104">Logic Apps는 클라우드에서 확장 가능한 통합 및 워크플로를 단순화하고 구현하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="83dbb-104">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="83dbb-105">모델에 비주얼 디자이너를 제공하고 프로세스를 워크플로로 알려진 일련의 단계로 자동화합니다.</span><span class="sxs-lookup"><span data-stu-id="83dbb-105">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="83dbb-106">서비스 및 프로토콜에 걸쳐 신속하게 통합하기 위해 클라우드 및 온-프레미스에 많은 커넥터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83dbb-106">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="83dbb-107">'Dynamics CRM에 계정을 추가하는 경우'와 같이 논리 앱은 트리거로 시작하고, 실행 후에 작업, 변환 및 조건 논리의 다양한 조합을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83dbb-107">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="83dbb-108">Logic Apps를 사용하는 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="83dbb-108">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="83dbb-109">설계 도구를 쉽게 이해하기 위해 사용하는 복잡한 프로세스를 설계하여 시간 절약</span><span class="sxs-lookup"><span data-stu-id="83dbb-109">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="83dbb-110">코드에서 구현하기 어려운 패턴 및 워크플로를 원활하게 구현</span><span class="sxs-lookup"><span data-stu-id="83dbb-110">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="83dbb-111">템플릿에서 신속하게 시작</span><span class="sxs-lookup"><span data-stu-id="83dbb-111">Getting started quickly from templates</span></span>
- <span data-ttu-id="83dbb-112">고유의 사용자 지정 API, 코드 및 작업을 사용하여 논리 앱 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="83dbb-112">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="83dbb-113">온-프레미스 및 클라우드에 서로 다른 시스템 연결 및 동기화</span><span class="sxs-lookup"><span data-stu-id="83dbb-113">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="83dbb-114">강력한 통합 지원을 통해 BizTalk Server, API Management, Azure Functions 및 Azure Service Bus 구축</span><span class="sxs-lookup"><span data-stu-id="83dbb-114">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="83dbb-115">Logic Apps는 완전히 관리되는 iPaaS(integration Platform as a Service)로서 개발자가 호스팅, 확장성, 가용성 및 관리를 구축하는 방법에 대해 걱정하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="83dbb-115">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="83dbb-116">Logic Apps는 수요에 맞게 자동으로 강화됩니다.</span><span class="sxs-lookup"><span data-stu-id="83dbb-116">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="83dbb-117">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="83dbb-117">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="83dbb-118">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="83dbb-118">Install the npm module</span></span>

<span data-ttu-id="83dbb-119">Node.js용 Azure 논리 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="83dbb-119">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="83dbb-120">예</span><span class="sxs-lookup"><span data-stu-id="83dbb-120">Example</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a><span data-ttu-id="83dbb-121">샘플</span><span class="sxs-lookup"><span data-stu-id="83dbb-121">Samples</span></span>

<span data-ttu-id="83dbb-122">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="83dbb-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
