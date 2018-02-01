---
title: "Node.js용 Azure Redis Cache 모듈"
description: "Node.js용 Azure Redis Cache 모듈에 대한 참조"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 5d3a410fefcf6840181701763346fbfe08fe023b
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="e3a89-103">Node.js용 Azure Redis Cache 모듈</span><span class="sxs-lookup"><span data-stu-id="e3a89-103">Azure Redis Cache modules for Node.js</span></span>

<span data-ttu-id="e3a89-104">Azure Redis Cache는 인기 있는 Redis 프로젝트 오픈 소스를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a89-104">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="e3a89-105">Microsoft에서 관리하고 Azure 앱에서 액세스할 수 있는 안전한 전용 Redis 인스턴스에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a89-105">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="e3a89-106">Redis는 고급 키-값 저장소이며, 키에는 문자열, 해시, 목록, 집합, 정렬된 집합과 같은 데이터 구조가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3a89-106">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="e3a89-107">Redis는 이러한 데이터 유형에 대한 소규모 작업 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a89-107">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="e3a89-108">[Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="e3a89-108">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="e3a89-109">클라이언트 패키지</span><span class="sxs-lookup"><span data-stu-id="e3a89-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e3a89-110">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="e3a89-110">Install the npm module</span></span>

<span data-ttu-id="e3a89-111">npm을 사용하여 Node.js용 Redis 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a89-111">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="e3a89-112">예</span><span class="sxs-lookup"><span data-stu-id="e3a89-112">Example</span></span>

<span data-ttu-id="e3a89-113">이 예제에서는 Azure Redis Cache 인스턴스에 연결하고, 키/값 쌍을 저장한 다음, 해당 키로 저장된 값을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e3a89-113">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a><span data-ttu-id="e3a89-114">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="e3a89-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e3a89-115">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="e3a89-115">Install the npm module</span></span>

<span data-ttu-id="e3a89-116">npm을 사용하여 Node.js용 Azure Redis Cache 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a89-116">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="e3a89-117">예</span><span class="sxs-lookup"><span data-stu-id="e3a89-117">Example</span></span>

<span data-ttu-id="e3a89-118">이 예제에서는 Azure로 인증하고 지정된 리소스 그룹의 모든 Redis Cache 인스턴스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a89-118">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a><span data-ttu-id="e3a89-119">샘플</span><span class="sxs-lookup"><span data-stu-id="e3a89-119">Samples</span></span>

* [<span data-ttu-id="e3a89-120">Azure Redis Cache를 Node.js와 함께 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="e3a89-120">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="e3a89-121">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a89-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
