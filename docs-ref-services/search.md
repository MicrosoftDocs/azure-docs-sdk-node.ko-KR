---
title: Node.js용 Azure Search 모듈
description: Node.js용 Azure Search 모듈에 대한 참조
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: a9c34a57d7964de1713ebf4d6c0f9c000df33042
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49686158"
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="00bee-103">Node.js용 Azure Search 모듈</span><span class="sxs-lookup"><span data-stu-id="00bee-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="00bee-104">Azure Search는 서버 및 인프라 관리를 Microsoft에 위임하는 클라우드 SaaS(Search-as-a-Service) 솔루션이며, 즉시 사용 가능한 서비스를 제공하여 데이터로 채운 다음 응용 프로그램에 검색을 추가하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00bee-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="00bee-105">[Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="00bee-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="00bee-106">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="00bee-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="00bee-107">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="00bee-107">Install the npm module</span></span>

<span data-ttu-id="00bee-108">Azure Search npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="00bee-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="00bee-109">예</span><span class="sxs-lookup"><span data-stu-id="00bee-109">Example</span></span>

<span data-ttu-id="00bee-110">이 예제에서는 Azure에 새 Search 서비스를 만들고 리소스 그룹에 리소스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="00bee-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="00bee-111">샘플</span><span class="sxs-lookup"><span data-stu-id="00bee-111">Samples</span></span>

<span data-ttu-id="00bee-112">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="00bee-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
