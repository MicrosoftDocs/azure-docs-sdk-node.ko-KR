---
title: "Node.js를 통해 Azure 데이터베이스를 사용하는 샘플 코드"
description: "Node.js를 통해 Azure 데이터베이스를 사용하는 샘플 코드입니다."
author: tomarcher
manager: douge
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: tarcher
ms.openlocfilehash: 8292a8fd0353ae84ac2b1622e5c622e60be04c9b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="sample-code-for-using-azure-databases-with-nodejs"></a><span data-ttu-id="6002c-103">Node.js를 통해 Azure 데이터베이스를 사용하는 샘플 코드</span><span class="sxs-lookup"><span data-stu-id="6002c-103">Sample code for using Azure databases with Node.js</span></span>

<span data-ttu-id="6002c-104">다음 샘플 코드에서는 Node.js를 통해 Azure 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6002c-104">The following sample code illustrate using Azure databases with Node.js.</span></span>

<span data-ttu-id="6002c-105">다른 작업에 대한 코드가 필요하면 [Azure Node.js 샘플 ](https://azure.microsoft.com/resources/samples/?term=nodejs)의 전체 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6002c-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="6002c-106">**Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="6002c-106">**Cosmos DB**</span></span> ||
| [<span data-ttu-id="6002c-107">Azure Cosmos DB 및 Graph API 사용(영문)</span><span class="sxs-lookup"><span data-stu-id="6002c-107">Use the Azure Cosmos DB and Graph API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/) | <span data-ttu-id="6002c-108">Azure Cosmos DB를 Graph API와 함께 사용하여 Node.js 응용 프로그램의 데이터를 저장하고 액세스하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6002c-108">Shows you how to use the Azure Cosmos DB with the Graph API to store and access data from a Node.js application.</span></span> |
| [<span data-ttu-id="6002c-109">Azure Cosmos DB 및 DocumentDB API 사용(영문)</span><span class="sxs-lookup"><span data-stu-id="6002c-109">Use the Azure Cosmos DB and Document DB API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/) | <span data-ttu-id="6002c-110">Azure Cosmos DB를 DocumentDB API와 함께 사용하여 Node.js 응용 프로그램의 데이터를 저장하고 액세스하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6002c-110">Shows you how to use the Azure Cosmos DB with the DocumentDB API to store and access data from a Node.js application.</span></span> |
| <span data-ttu-id="6002c-111">**DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="6002c-111">**DocumentDB**</span></span> ||
| [<span data-ttu-id="6002c-112">DocumentDB를 사용하여 Node.js 및 Express를 통한 웹 응용 프로그램 개발(영문)</span><span class="sxs-lookup"><span data-stu-id="6002c-112">Web application development with Node.js and Express using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-todo-app/) | <span data-ttu-id="6002c-113">Azure에서 Azure DocumentDB를 사용하여 Node.js Express 응용 프로그램의 데이터를 저장하고 액세스하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6002c-113">Shows how to use Azure DocumentDB to store and access data from a Node.js Express application on Azure.</span></span> |
| [<span data-ttu-id="6002c-114">DocumentDB를 사용하여 Node.js 콘솔 앱 개발(영문)</span><span class="sxs-lookup"><span data-stu-id="6002c-114">Developing a Node.js console app using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-getting-started/) | <span data-ttu-id="6002c-115">이 샘플에서는 Microsoft Azure DocumentDB 서비스 및 Node.js를 빠르게 시작하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6002c-115">This sample shows you how get started quickly with Microsoft Azure DocumentDB service and Node.js.</span></span> |
| <span data-ttu-id="6002c-116">**MongoDB**</span><span class="sxs-lookup"><span data-stu-id="6002c-116">**MongoDB**</span></span> ||
| [<span data-ttu-id="6002c-117">Azure의 Node.js 및 MongoDB 웹앱(영문)</span><span class="sxs-lookup"><span data-stu-id="6002c-117">Node.js and MongoDB web app in Azure</span></span>](https://azure.microsoft.com/resources/samples/meanjs/) | <span data-ttu-id="6002c-118">[Azure에서 Node.js 및 MongoDB 웹앱 작성](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json) 자습서와 함께 수행하는 데 사용할 수 있는 샘플 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="6002c-118">Sample application that you can use to follow along with the tutorial, [Build a Node.js and MongoDB web app in Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json).</span></span> |
| <span data-ttu-id="6002c-119">**SQL 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="6002c-119">**SQL Database**</span></span> ||
| [<span data-ttu-id="6002c-120">Azure SQL Database: Node.js를 사용하여 데이터 연결 및 쿼리</span><span class="sxs-lookup"><span data-stu-id="6002c-120">Azure SQL Database: Use Node.js to connect and query data</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | <span data-ttu-id="6002c-121">Node.js를 사용하여 Azure SQL Database에 연결한 다음, Transact-SQL 문을 사용하여 Windows, Ubuntu Linux 및 Mac 플랫폼에서 데이터베이스의 데이터를 쿼리, 삽입, 업데이트 및 삭제하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6002c-121">Demonstrates how to connect to an Azure SQL database using Node.js; then use Transact-SQL statements to query, insert, update, and delete data in the database from Windows, Ubuntu Linux, and Mac platforms.</span></span> |