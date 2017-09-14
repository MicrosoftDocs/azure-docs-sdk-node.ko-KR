---
title: "Node.js용 Azure PostgreSQL 모듈"
description: "Node.js용 Azure PostgreSQL 모듈에 대한 참조"
keywords: "Azure, Node, SDK, API, NodeJS, JavaScript, 데이터베이스, PostgreSQL"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: a5130c96b3ae922358b6898c15510282fbaa97f0
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Node.js용 Azure PostgreSQL 모듈

## <a name="overview"></a>개요

Azure Database for PostgreSQL에 액세스하는 데 권장되는 클라이언트 라이브러리는 [Azure Database for PostgreSQL용 Node.js 연결 라이브러리(영문)](https://www.npmjs.com/package/pg) 오픈 소스입니다. 이 라이브러리는 순수 JavaScript 및 와 선택적 네이티브 libpq 바인딩을 지원하는 Node.js용 비차단 PostgreSQL 클라이언트입니다.

[Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)에 대해 자세히 알아보세요.

## <a name="client-package"></a>클라이언트 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

npm을 사용하여 PostgreSQL 클라이언트 모듈을 설치합니다.

```bash
npm install pg
```   

### <a name="example"></a>예제

이 예제에서는 클라이언트 연결을 열고 간단한 쿼리를 실행합니다.

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a>샘플

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
