---
title: Node.js용 Azure MySQL 모듈
description: Node.js용 Azure MySQL 모듈에 대한 참조
author: ajlam
ms.author: andrela
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 557645774ecb0ea5e774f99d03251a303ad19660
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51354147"
---
# <a name="azure-mysql-modules-for-nodejs"></a>Node.js용 Azure MySQL 모듈

Azure Database for MySQL에 액세스하는 데 권장되는 클라이언트 라이브러리는 [Azure Database for MySQL용 Node.js 연결 라이브러리(영문)](https://github.com/sidorares/node-mysql2) 오픈 소스입니다. 

[Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)에 대해 자세히 알아보세요.

## <a name="client-package"></a>클라이언트 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

npm을 사용하여 MySQL 클라이언트 모듈을 설치합니다.

```bash
npm install mysql2
```   

### <a name="example"></a>예

이 예제에서는 MySQL 데이터베이스에 연결하고 간단한 쿼리를 수행하여 모든 고객을 검색합니다.

```javascript
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'mysqldemo.mysql.database.azure.com',
  user: 'myadmin@mysqldemo',
  password: 'your_password',
  database: 'my_db',
  port: 3306,
  ssl: true
});

connection.connect();
const query = 'SELECT * FROM customers';
connection.query(query, (err, res) =>
  console.log(`We have ${res.length} customers`)
);

connection.end();
```

## <a name="samples"></a>샘플

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
