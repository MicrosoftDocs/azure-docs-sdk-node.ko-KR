---
title: "Node.js용 Azure Data Lake Store 모듈"
description: "Node.js용 Azure Data Lake Store 모듈에 대한 참조"
keywords: Azure, SDK, API, Data Lake Store, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: 5885bf8f073e4f4f1ac2be88b8691b092e8a21d3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="aa9cf-104">Node.js용 Azure Data Lake Store 모듈</span><span class="sxs-lookup"><span data-stu-id="aa9cf-104">Azure Data Lake Store modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="aa9cf-105">개요</span><span class="sxs-lookup"><span data-stu-id="aa9cf-105">Overview</span></span>
<span data-ttu-id="aa9cf-106">Azure 데이터 레이크 저장소는 빅 데이터 분석 작업을 위한 엔터프라이즈 수준 하이퍼 스케일 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="aa9cf-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="aa9cf-107">Azure 데이터 레이크를 사용하면 작동 및 예비 분석에 대해 한 곳에서 모든 크기, 형식 및 수집 속도의 데이터를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa9cf-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="aa9cf-108">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="aa9cf-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="aa9cf-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="aa9cf-109">Install the npm module</span></span>

<span data-ttu-id="aa9cf-110">npm을 사용하여 Node.js용 Azure Data Lake Store 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9cf-110">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="aa9cf-111">예제</span><span class="sxs-lookup"><span data-stu-id="aa9cf-111">Example</span></span>

<span data-ttu-id="aa9cf-112">이 예제에서는 지정된 Azure 구독 내의 모든 Data Lake Store 계정을 나열합니다</span><span class="sxs-lookup"><span data-stu-id="aa9cf-112">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

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

## <a name="samples"></a><span data-ttu-id="aa9cf-113">샘플</span><span class="sxs-lookup"><span data-stu-id="aa9cf-113">Samples</span></span>

<span data-ttu-id="aa9cf-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9cf-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
