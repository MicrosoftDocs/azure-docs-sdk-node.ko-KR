---
title: Node.js용 Azure 권한 부여 모듈
description: Node.js용 Azure 권한 부여 모듈에 대한 참조
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 0b0ecd088d8b7728e56f352597e2db038678945f
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51480847"
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="c9727-103">Node.js용 Azure 권한 부여 모듈</span><span class="sxs-lookup"><span data-stu-id="c9727-103">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c9727-104">개요</span><span class="sxs-lookup"><span data-stu-id="c9727-104">Overview</span></span>

<span data-ttu-id="c9727-105">Azure App Service 인증/권한 부여는 앱 백 엔드에서 코드를 변경할 필요가 없도록 사용자가 응용 프로그램에 로그인하는 방법을 제공하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="c9727-105">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="c9727-106">권한 부여는 응용 프로그램을 보호하고 사용자별 데이터로 작업하는 쉬운 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c9727-106">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="c9727-107">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="c9727-107">Management package</span></span>

<span data-ttu-id="c9727-108">npm을 사용하여 Node.js용 Azure 권한 부여 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c9727-108">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c9727-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="c9727-109">Install the npm module</span></span>

<span data-ttu-id="c9727-110">Azure 권한 부여 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c9727-110">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="c9727-111">예</span><span class="sxs-lookup"><span data-stu-id="c9727-111">Example</span></span>

<span data-ttu-id="c9727-112">이 예제에서는 요청된 리소스 그룹에 대한 모든 역할 할당을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c9727-112">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="c9727-113">샘플</span><span class="sxs-lookup"><span data-stu-id="c9727-113">Samples</span></span>

<span data-ttu-id="c9727-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="c9727-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
