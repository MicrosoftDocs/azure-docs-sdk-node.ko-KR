---
title: Node.js용 Azure Storage 모듈
description: Node.js용 Azure Storage 모듈에 대한 참조
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: b94c6fbb50e656e0dcc542236afe791c7ddc9be4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
ms.locfileid: "28116901"
---
# <a name="azure-storage-modules-for-nodejs"></a>Node.js용 Azure Storage 모듈

Azure Storage 클라이언트 모듈을 사용하여 다음을 수행할 수 있습니다.

- [Azure Blob 저장소](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)에서 개체와 파일 읽기 및 쓰기
- [Azure 큐 저장소](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)를 사용하여 클라우드에 연결된 응용 프로그램 간에 메시지 보내기 및 받기
- [Azure 테이블 저장소](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)를 사용하여 대규모 구조적 데이터 읽기 및 쓰기

관리 모듈을 사용하여 Azure Storage 계정을 생성, 업데이트 및 관리하고, Node.js 앱에서 액세스 키를 쿼리하고 다시 생성합니다.

## <a name="client-package"></a>클라이언트 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure 저장소 클라이언트 npm 모듈을 설치합니다

```bash
npm install azure-storage
```

### <a name="example"></a>예

이 예제에서는 저장소 컨테이너를 만들고 `data.txt` 로컬 파일을 업로드합니다.

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

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치 

Azure 저장소 관리 npm 모듈을 설치합니다.

```bash
npm install azure-arm-storage
```

### <a name="example"></a>예

이 예제에서는 저장소 계정을 나열합니다.

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

## <a name="samples"></a>샘플

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
