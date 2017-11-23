---
title: "Node.js용 Azure SQL 모듈"
description: "Node.js용 Azure SQL 모듈에 대한 참조"
keywords: Azure, Node, SDK, API, NodeJS, JavaScript, SQL
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 65ee90b4e6ca248b9d19a3685163211ca547cad4
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="85f62-104">Node.js용 Azure SQL 모듈</span><span class="sxs-lookup"><span data-stu-id="85f62-104">Azure SQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="85f62-105">개요</span><span class="sxs-lookup"><span data-stu-id="85f62-105">Overview</span></span>

<span data-ttu-id="85f62-106">Node.js에서 [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)에 저장된 데이터를 사용하여 작업합니다.</span><span class="sxs-lookup"><span data-stu-id="85f62-106">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="85f62-107">관리 라이브러리는 Microsoft Azure SQL 데이터베이스를 쉽게 관리할 수 있는 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="85f62-107">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="85f62-108">클라이언트 패키지</span><span class="sxs-lookup"><span data-stu-id="85f62-108">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="85f62-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="85f62-109">Install the npm module</span></span>

<span data-ttu-id="85f62-110">SQL Server 클라이언트 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="85f62-110">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="85f62-111">예제</span><span class="sxs-lookup"><span data-stu-id="85f62-111">Example</span></span>

<span data-ttu-id="85f62-112">이 예제에서는 SQL Server 데이터베이스에 연결하고 간단한 쿼리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="85f62-112">This example connects to a SQL Server database and perform a simple query.</span></span>

```javascript
const Connection = require('tedious').Connection;
const Request = require('tedious').Request;

const config = {
  userName: 'your-username',
  password: 'your-password',
  server: 'path-to-server',
  options: {
    database: 'database-name',
    encrypt: true
  }
};

const connection = new Connection(config);
connection.on('connect', err => {
  err ? console.log(err) : executeStatement();
});

const query = 'SELECT * from TableName';
const executeStatement = () => {
  const request = new Request(query, (err, rowCount) => {
    err ? console.log(err) : console.log(rowCount);
  });

  request.on('row', columns => {
    columns.forEach(column => console.log(column.value));
  });

  connection.execSql(request);
};
```

## <a name="management-package"></a><span data-ttu-id="85f62-113">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="85f62-113">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="85f62-114">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="85f62-114">Install npm modules</span></span>

<span data-ttu-id="85f62-115">Azure SQL Server 관리 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="85f62-115">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="85f62-116">예제</span><span class="sxs-lookup"><span data-stu-id="85f62-116">Example</span></span>

<span data-ttu-id="85f62-117">인증하고, 클라이언트를 만들고, 모든 서버를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="85f62-117">Authenticate, create a client, and list all servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SQLManagement = require('azure-arm-sql');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SQLManagement(credentials, 'your-subscription-id');
    return client.servers.list();
  })
  .then(servers => console.dir(servers, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="85f62-118">샘플</span><span class="sxs-lookup"><span data-stu-id="85f62-118">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="85f62-119">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="85f62-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
