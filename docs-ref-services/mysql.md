---
title: "Node.js용 Azure MySQL 모듈"
description: "Node.js용 Azure MySQL 모듈에 대한 참조"
keywords: "Azure, Node, SDK, API, NodeJS, JavaScript, 데이터베이스, MySQL"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 3efc0fcccb7cb01711ad1ce98e9ff9a2d87b77fe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="110e5-104">Node.js용 Azure MySQL 모듈</span><span class="sxs-lookup"><span data-stu-id="110e5-104">Azure MySQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="110e5-105">개요</span><span class="sxs-lookup"><span data-stu-id="110e5-105">Overview</span></span>

<span data-ttu-id="110e5-106">Azure Database for MySQL에 액세스하는 데 권장되는 클라이언트 라이브러리는 [Azure Database for MySQL용 Node.js 연결 라이브러리(영문)](https://github.com/sidorares/node-mysql2) 오픈 소스입니다.</span><span class="sxs-lookup"><span data-stu-id="110e5-106">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="110e5-107">[Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="110e5-107">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="110e5-108">클라이언트 패키지</span><span class="sxs-lookup"><span data-stu-id="110e5-108">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="110e5-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="110e5-109">Install the npm module</span></span>

<span data-ttu-id="110e5-110">npm을 사용하여 MySQL 클라이언트 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="110e5-110">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="110e5-111">예제</span><span class="sxs-lookup"><span data-stu-id="110e5-111">Example</span></span>

<span data-ttu-id="110e5-112">이 예제에서는 MySQL 데이터베이스에 연결하고 간단한 쿼리를 수행하여 모든 고객을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="110e5-112">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="110e5-113">샘플</span><span class="sxs-lookup"><span data-stu-id="110e5-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="110e5-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="110e5-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
