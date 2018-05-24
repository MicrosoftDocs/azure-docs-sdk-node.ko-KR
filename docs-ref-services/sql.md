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
---
# <a name="azure-sql-modules-for-nodejs"></a>Node.js용 Azure SQL 모듈

Node.js에서 [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)에 저장된 데이터를 사용하여 작업합니다.
관리 라이브러리는 Microsoft Azure SQL 데이터베이스를 쉽게 관리할 수 있는 인터페이스를 제공합니다.

## <a name="client-package"></a>클라이언트 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

SQL Server 클라이언트 npm 모듈을 설치합니다.

```bash
npm install tedious
```

### <a name="example"></a>예

이 예제에서는 SQL Server 데이터베이스에 연결하고 간단한 쿼리를 수행합니다.

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

## <a name="management-package"></a>관리 패키지

### <a name="install-npm-modules"></a>npm 모듈 설치

Azure SQL Server 관리 npm 모듈을 설치합니다.

```
npm install azure-arm-sql
```   

### <a name="example"></a>예

인증하고, 클라이언트를 만들고, 모든 서버를 나열합니다.

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

## <a name="samples"></a>샘플

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
