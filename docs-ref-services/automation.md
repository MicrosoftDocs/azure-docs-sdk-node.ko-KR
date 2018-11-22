---
title: Node.js용 Azure Automation 모듈
description: Node.js용 Azure Automation 모듈에 대한 참조
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: f364bb09c97c1262f640a4b48514c6abaee5f14a
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52154898"
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="dd0cf-103">Node.js용 Azure Automation 모듈</span><span class="sxs-lookup"><span data-stu-id="dd0cf-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="dd0cf-104">개요</span><span class="sxs-lookup"><span data-stu-id="dd0cf-104">Overview</span></span>

<span data-ttu-id="dd0cf-105">Azure Automation은 사용자가 클라우드 및 엔터프라이즈 환경에서 일반적으로 장기간 실행되고, 오류가 발생하기 쉬우며, 자주 반복되는 수동 작업을 자동화할 수 있는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0cf-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="dd0cf-106">시간을 절약하고, 일반 관리 작업의 안정성을 높이며, 이러한 작업을 정기적으로 자동 수행하도록 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0cf-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="dd0cf-107">Runbook을 사용하는 프로세스를 자동화하거나 원하는 상태 구성을 사용하여 구성 관리를 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0cf-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="dd0cf-108">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="dd0cf-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="dd0cf-109">npm을 사용하여 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="dd0cf-109">Install the modules with npm</span></span>

<span data-ttu-id="dd0cf-110">npm을 사용하여 Node.js용 Azure Automation 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0cf-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="dd0cf-111">예</span><span class="sxs-lookup"><span data-stu-id="dd0cf-111">Example</span></span>

<span data-ttu-id="dd0cf-112">이 예제에서는 자동화 계정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0cf-112">This example lists the automation accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="dd0cf-113">샘플</span><span class="sxs-lookup"><span data-stu-id="dd0cf-113">Samples</span></span>

<span data-ttu-id="dd0cf-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0cf-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
