---
title: Node.js용 Azure PostgreSQL 모듈
description: Node.js용 Azure PostgreSQL 모듈에 대한 참조
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: ed9373b767684e4893ca84de1030d062178b7ea4
ms.sourcegitcommit: 0d439a88f38a085e2be0616c8bdb0ffcca2e54ad
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49027417"
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="99c0c-103">Node.js용 Azure PostgreSQL 모듈</span><span class="sxs-lookup"><span data-stu-id="99c0c-103">Azure PostgreSQL modules for Node.js</span></span>

<span data-ttu-id="99c0c-104">Azure Database for PostgreSQL에 액세스하는 데 권장되는 클라이언트 라이브러리는 [Azure Database for PostgreSQL용 Node.js 연결 라이브러리(영문)](https://www.npmjs.com/package/pg) 오픈 소스입니다.</span><span class="sxs-lookup"><span data-stu-id="99c0c-104">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="99c0c-105">이 라이브러리는 순수 JavaScript 및 와 선택적 네이티브 libpq 바인딩을 지원하는 Node.js용 비차단 PostgreSQL 클라이언트입니다.</span><span class="sxs-lookup"><span data-stu-id="99c0c-105">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="99c0c-106">[Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="99c0c-106">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="99c0c-107">클라이언트 패키지</span><span class="sxs-lookup"><span data-stu-id="99c0c-107">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="99c0c-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="99c0c-108">Install the npm module</span></span>

<span data-ttu-id="99c0c-109">npm을 사용하여 PostgreSQL 클라이언트 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="99c0c-109">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="99c0c-110">예</span><span class="sxs-lookup"><span data-stu-id="99c0c-110">Example</span></span>

<span data-ttu-id="99c0c-111">이 예제에서는 클라이언트 연결을 열고 간단한 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="99c0c-111">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="99c0c-112">샘플</span><span class="sxs-lookup"><span data-stu-id="99c0c-112">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="99c0c-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="99c0c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
