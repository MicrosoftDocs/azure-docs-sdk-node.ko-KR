---
title: "Node.js용 Azure 권한 부여 모듈"
description: "Node.js용 Azure 권한 부여 모듈에 대한 참조"
keywords: "Azure, SDK, API, 권한 부여, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: de843bf1afed77afdb9bde035962a1c151d9c1bb
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="4a60a-104">Node.js용 Azure 권한 부여 모듈</span><span class="sxs-lookup"><span data-stu-id="4a60a-104">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4a60a-105">개요</span><span class="sxs-lookup"><span data-stu-id="4a60a-105">Overview</span></span>

<span data-ttu-id="4a60a-106">Azure App Service 인증/권한 부여는 앱 백 엔드에서 코드를 변경할 필요가 없도록 사용자가 응용 프로그램에 로그인하는 방법을 제공하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="4a60a-106">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="4a60a-107">권한 부여는 응용 프로그램을 보호하고 사용자별 데이터로 작업하는 쉬운 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4a60a-107">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="4a60a-108">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="4a60a-108">Management package</span></span>

<span data-ttu-id="4a60a-109">npm을 사용하여 Node.js용 Azure 권한 부여 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="4a60a-109">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4a60a-110">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="4a60a-110">Install the npm module</span></span>

<span data-ttu-id="4a60a-111">Azure 권한 부여 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="4a60a-111">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="4a60a-112">예제</span><span class="sxs-lookup"><span data-stu-id="4a60a-112">Example</span></span>

<span data-ttu-id="4a60a-113">이 예제에서는 요청된 리소스 그룹에 대한 모든 역할 할당을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4a60a-113">This example lists all role assignments for the requested resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a><span data-ttu-id="4a60a-114">샘플</span><span class="sxs-lookup"><span data-stu-id="4a60a-114">Samples</span></span>

<span data-ttu-id="4a60a-115">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="4a60a-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
