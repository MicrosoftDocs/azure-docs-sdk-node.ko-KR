---
title: "Node.js용 Azure Storage 모듈"
description: "Node.js용 Azure Storage 모듈에 대한 참조"
keywords: Azure, Node, SDK, API, Storage, NodeJS, JavaScript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: 61d3f3bb49d10e63a353c474067a155223bb6c76
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="f98b2-104">Node.js용 Azure Storage 모듈</span><span class="sxs-lookup"><span data-stu-id="f98b2-104">Azure Storage modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f98b2-105">개요</span><span class="sxs-lookup"><span data-stu-id="f98b2-105">Overview</span></span>

<span data-ttu-id="f98b2-106">Azure Storage 클라이언트 모듈을 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f98b2-106">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="f98b2-107">[Azure Blob 저장소](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)에서 개체와 파일 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="f98b2-107">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="f98b2-108">[Azure 큐 저장소](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)를 사용하여 클라우드에 연결된 응용 프로그램 간에 메시지 보내기 및 받기</span><span class="sxs-lookup"><span data-stu-id="f98b2-108">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="f98b2-109">[Azure 테이블 저장소](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)를 사용하여 대규모 구조적 데이터 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="f98b2-109">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="f98b2-110">관리 모듈을 사용하여 Azure Storage 계정을 생성, 업데이트 및 관리하고, Node.js 앱에서 액세스 키를 쿼리하고 다시 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f98b2-110">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="f98b2-111">클라이언트 패키지</span><span class="sxs-lookup"><span data-stu-id="f98b2-111">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f98b2-112">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="f98b2-112">Install the npm module</span></span>

<span data-ttu-id="f98b2-113">Azure 저장소 클라이언트 npm 모듈을 설치합니다</span><span class="sxs-lookup"><span data-stu-id="f98b2-113">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="f98b2-114">예제</span><span class="sxs-lookup"><span data-stu-id="f98b2-114">Example</span></span>

<span data-ttu-id="f98b2-115">이 예제에서는 저장소 컨테이너를 만들고 `data.txt` 로컬 파일을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f98b2-115">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a><span data-ttu-id="f98b2-116">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="f98b2-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f98b2-117">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="f98b2-117">Install the npm module</span></span> 

<span data-ttu-id="f98b2-118">Azure 저장소 관리 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f98b2-118">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="f98b2-119">예제</span><span class="sxs-lookup"><span data-stu-id="f98b2-119">Example</span></span>

<span data-ttu-id="f98b2-120">이 예제에서는 저장소 계정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f98b2-120">This example list the storage accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="f98b2-121">샘플</span><span class="sxs-lookup"><span data-stu-id="f98b2-121">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="f98b2-122">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="f98b2-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
