---
title: Node.js용 Azure SQL 모듈
description: Node.js용 Azure SQL 모듈에 대한 참조
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 095a54a0919b237891ea89f4c826be0fc3060bbe
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259448"
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="766d1-103">Node.js용 Azure SQL 모듈</span><span class="sxs-lookup"><span data-stu-id="766d1-103">Azure SQL modules for Node.js</span></span>

<span data-ttu-id="766d1-104">Node.js에서 [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)에 저장된 데이터를 사용하여 작업합니다.</span><span class="sxs-lookup"><span data-stu-id="766d1-104">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="766d1-105">관리 라이브러리는 Microsoft Azure SQL 데이터베이스를 쉽게 관리할 수 있는 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="766d1-105">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="766d1-106">클라이언트 패키지</span><span class="sxs-lookup"><span data-stu-id="766d1-106">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="766d1-107">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="766d1-107">Install the npm module</span></span>

<span data-ttu-id="766d1-108">SQL Server 클라이언트 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="766d1-108">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="766d1-109">예</span><span class="sxs-lookup"><span data-stu-id="766d1-109">Example</span></span>

<span data-ttu-id="766d1-110">이 예제에서는 SQL Server 데이터베이스에 연결하고 간단한 쿼리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="766d1-110">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="766d1-111">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="766d1-111">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="766d1-112">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="766d1-112">Install npm modules</span></span>

<span data-ttu-id="766d1-113">Azure SQL Server 관리 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="766d1-113">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="766d1-114">예</span><span class="sxs-lookup"><span data-stu-id="766d1-114">Example</span></span>

<span data-ttu-id="766d1-115">인증하고, 클라이언트를 만들고, 모든 서버를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="766d1-115">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="766d1-116">샘플</span><span class="sxs-lookup"><span data-stu-id="766d1-116">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="766d1-117">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="766d1-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
