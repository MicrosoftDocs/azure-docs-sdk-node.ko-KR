---
title: "Node.js용 Azure Cosmos DB 모듈"
description: "Node.js용 Azure Cosmos DB 모듈에 대한 참조"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 575c276ec755dabe8e7b9ed76ba98ef8073c4f1b
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="9a763-103">Node.js용 Azure Cosmos DB 모듈</span><span class="sxs-lookup"><span data-stu-id="9a763-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="9a763-104">Azure Cosmos DB는 전 세계에 배포된 Microsoft의 멀티모델 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="9a763-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="9a763-105">Azure Cosmos DB를 사용하면 Azure의 여러 지리적 영역에서 처리량 및 저장소를 탄력적이고 독립적으로 크기 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a763-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="9a763-106">포괄적인 SLA(서비스 수준 계약)를 통해 처리량, 대기 시간, 가용성 및 일관성을 보장하며, 다른 데이터베이스 서비스에서 제공할 수 없는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9a763-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="9a763-107">Azure Cosmos DB에는 기본적으로 키-값, 문서, 그래프, 다각형 등, 다양한 데이터 모델을 지원하며 쓰기에 최적화되고, 리소스가 관리하며, 모든 스키마에 적용되는 엔진이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a763-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="9a763-108">또한 MongoDB, DocumentDB SQL, Gremlin(미리 보기) 및 Azure Tables(미리 보기)를 포함하여 데이터에 액세스하기 위한 다양한 API를 확장 가능한 방식으로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9a763-108">It also supports many APIs for accessing data including MongoDB, DocumentDB SQL, Gremlin (preview), and Azure Tables (preview), in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="9a763-109">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="9a763-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9a763-110">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="9a763-110">Install the npm module</span></span> 

<span data-ttu-id="9a763-111">Azure Cosmos DB npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="9a763-111">Install the Azure Cosmos DB npm module</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="9a763-112">예</span><span class="sxs-lookup"><span data-stu-id="9a763-112">Example</span></span>

<span data-ttu-id="9a763-113">이 예제에서는 모든 Cosmos DB 계정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="9a763-113">This example lists all Cosmos DB accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a><span data-ttu-id="9a763-114">샘플</span><span class="sxs-lookup"><span data-stu-id="9a763-114">Samples</span></span>

* [<span data-ttu-id="9a763-115">Azure Cosmos DB를 사용하여 Node.js 앱 개발 - DocumentDB(영문)</span><span class="sxs-lookup"><span data-stu-id="9a763-115">Developing a Node.js app using Azure Cosmos DB - DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="9a763-116">Azure Cosmos DB를 사용하여 Node.js 앱 개발 - Gremlin(영문)</span><span class="sxs-lookup"><span data-stu-id="9a763-116">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="9a763-117">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="9a763-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
