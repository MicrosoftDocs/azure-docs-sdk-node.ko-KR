---
title: "Node.js용 Azure Search 모듈"
description: "Node.js용 Azure Search 모듈에 대한 참조"
keywords: Azure, SDK, API, Search, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: dc9d4c5128c99a9518bd059e191bb11e4de4b78f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-search-modules-for-nodejs"></a>Node.js용 Azure Search 모듈

## <a name="overview"></a>개요

Azure Search는 서버 및 인프라 관리를 Microsoft에 위임하는 클라우드 SaaS(Search-as-a-Service) 솔루션이며, 즉시 사용 가능한 서비스를 제공하여 데이터로 채운 다음 응용 프로그램에 검색을 추가하는 데 사용할 수 있습니다.

[Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search)에 대해 자세히 알아보세요.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure Search npm 모듈을 설치합니다.

```bash
npm install azure-arm-search
```

### <a name="example"></a>예제

이 예제에서는 Azure에 새 Search 서비스를 만들고 리소스 그룹에 리소스를 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
