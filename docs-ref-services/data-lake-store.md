---
title: Node.js용 Azure Data Lake Store 모듈
description: Node.js용 Azure Data Lake Store 모듈에 대한 참조
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: da7e71a9ee1f6936924b1ec966b441756e9b0dfe
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51185142"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="f6ee1-103">Node.js용 Azure Data Lake Store 모듈</span><span class="sxs-lookup"><span data-stu-id="f6ee1-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="f6ee1-104">Azure 데이터 레이크 저장소는 빅 데이터 분석 작업을 위한 엔터프라이즈 수준 하이퍼 스케일 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ee1-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="f6ee1-105">Azure 데이터 레이크를 사용하면 작동 및 예비 분석에 대해 한 곳에서 모든 크기, 형식 및 수집 속도의 데이터를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ee1-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="f6ee1-106">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="f6ee1-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f6ee1-107">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="f6ee1-107">Install the npm module</span></span>

<span data-ttu-id="f6ee1-108">npm을 사용하여 Node.js용 Azure Data Lake Store 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ee1-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="f6ee1-109">예</span><span class="sxs-lookup"><span data-stu-id="f6ee1-109">Example</span></span>

<span data-ttu-id="f6ee1-110">이 예제에서는 지정된 Azure 구독 내의 모든 Data Lake Store 계정을 나열합니다</span><span class="sxs-lookup"><span data-stu-id="f6ee1-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="f6ee1-111">샘플</span><span class="sxs-lookup"><span data-stu-id="f6ee1-111">Samples</span></span>

<span data-ttu-id="f6ee1-112">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ee1-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
