---
title: Node.js용 Azure Machine Learning 모듈
description: Node.js용 Azure Machine Learning 모듈에 대한 참조
author: hning86
ms.author: haining
manager: mwinkle
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 7e39084c65a40e47ed61cc01daf994aff447690e
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50270563"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="48de2-103">Node.js용 Azure Machine Learning 모듈</span><span class="sxs-lookup"><span data-stu-id="48de2-103">Azure Machine Learning modules for Node.js</span></span>

<span data-ttu-id="48de2-104">기계 학습은 미래 동작, 결과 및 추세를 예측하기 위해 기존 데이터를 컴퓨터가 학습하도록 돕는 데이터 과학 기법입니다.</span><span class="sxs-lookup"><span data-stu-id="48de2-104">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="48de2-105">이러한 기계 학습을 통한 예측은 좀 더 똑똑한 앱 및 장치를 만드는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="48de2-105">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="48de2-106">온라인 쇼핑 시 기계 학습은 사용자가 구매한 제품에 따라 좋아할만한 다른 제품을 추천하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="48de2-106">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="48de2-107">신용 카드를 읽을 때 기계 학습은 해당 거래를 거래 데이터베이스와 비교하여 부정 행위를 검색하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="48de2-107">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="48de2-108">로봇 진공 청소기가 방을 청소할 때, 기계 학습은 작업이 완료되었는지 여부를 판단하도록 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="48de2-108">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="48de2-109">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="48de2-109">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="48de2-110">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="48de2-110">Install the npm module</span></span>

<span data-ttu-id="48de2-111">Azure Machine Learning npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="48de2-111">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="48de2-112">예</span><span class="sxs-lookup"><span data-stu-id="48de2-112">Example</span></span>

<span data-ttu-id="48de2-113">이 예제에서는 모든 기계 학습 약정 계획을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="48de2-113">This example lists all machine learning committment plans.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="48de2-114">샘플</span><span class="sxs-lookup"><span data-stu-id="48de2-114">Samples</span></span>

<span data-ttu-id="48de2-115">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="48de2-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
