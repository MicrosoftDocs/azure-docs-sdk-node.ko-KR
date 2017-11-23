---
title: "Node.js용 Azure PowerBI Embedded 모듈"
description: "Node.js용 Azure PowerBI Embedded 모듈에 대한 참조"
keywords: Azure, SDK, API, PowerBI Embedded, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 74e69421d372ff4ccaebf2b811152dd83b9b4e7b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="7d094-104">Node.js용 Azure PowerBI Embedded 모듈</span><span class="sxs-lookup"><span data-stu-id="7d094-104">Azure PowerBI Embedded modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7d094-105">개요</span><span class="sxs-lookup"><span data-stu-id="7d094-105">Overview</span></span>

<span data-ttu-id="7d094-106">Azure Power BI Embedded 서비스를 사용하면 노드 응용 프로그램에 Power BI 보고서를 바로 통합하여 차트와 보고서를 만들거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d094-106">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="7d094-107">[Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="7d094-107">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="7d094-108">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="7d094-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7d094-109">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="7d094-109">Install the npm module</span></span>

<span data-ttu-id="7d094-110">Azure Power BI npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7d094-110">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="7d094-111">예제</span><span class="sxs-lookup"><span data-stu-id="7d094-111">Example</span></span>

<span data-ttu-id="7d094-112">이 예제에서는 기존 리소스 그룹에 작업 영역 컬렉션을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="7d094-112">This example creates a workspace collection in an existing resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="7d094-113">샘플</span><span class="sxs-lookup"><span data-stu-id="7d094-113">Samples</span></span>

<span data-ttu-id="7d094-114">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="7d094-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
