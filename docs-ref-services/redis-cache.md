---
title: Node.js용 Azure Redis Cache 모듈
description: Node.js용 Azure Redis Cache 모듈에 대한 참조
author: wesmc7777
ms.author: wesmc
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: afeee19cb79b54561b6cbef4a79de8b1606adb4d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-redis-cache-modules-for-nodejs"></a>Node.js용 Azure Redis Cache 모듈

Azure Redis Cache는 인기 있는 Redis 프로젝트 오픈 소스를 기반으로 합니다. Microsoft에서 관리하고 Azure 앱에서 액세스할 수 있는 안전한 전용 Redis 인스턴스에 대한 액세스를 제공합니다.

Redis는 고급 키-값 저장소이며, 키에는 문자열, 해시, 목록, 집합, 정렬된 집합과 같은 데이터 구조가 포함될 수 있습니다. Redis는 이러한 데이터 유형에 대한 소규모 작업 집합을 지원합니다.

[Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/)에 대해 자세히 알아보세요.

## <a name="client-package"></a>클라이언트 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

npm을 사용하여 Node.js용 Redis 모듈을 설치합니다.

```bash
npm install redis
```

### <a name="example"></a>예

이 예제에서는 Azure Redis Cache 인스턴스에 연결하고, 키/값 쌍을 저장한 다음, 해당 키로 저장된 값을 읽습니다.

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

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

npm을 사용하여 Node.js용 Azure Redis Cache 모듈을 설치합니다.

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a>예

이 예제에서는 Azure로 인증하고 지정된 리소스 그룹의 모든 Redis Cache 인스턴스를 나열합니다.

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


## <a name="samples"></a>샘플

* [Azure Redis Cache를 Node.js와 함께 사용하는 방법](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
