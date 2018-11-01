---
title: Node.js용 Azure PowerBI Embedded 모듈
description: Node.js용 Azure PowerBI Embedded 모듈에 대한 참조
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 58251dd1cd3a672a5167193f74d311952d70e84e
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50405759"
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="2dfeb-103">Node.js용 Azure PowerBI Embedded 모듈</span><span class="sxs-lookup"><span data-stu-id="2dfeb-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="2dfeb-104">Azure Power BI Embedded 서비스를 사용하면 노드 응용 프로그램에 Power BI 보고서를 바로 통합하여 차트와 보고서를 만들거나 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dfeb-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="2dfeb-105">[Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="2dfeb-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="2dfeb-106">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="2dfeb-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2dfeb-107">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="2dfeb-107">Install the npm module</span></span>

<span data-ttu-id="2dfeb-108">Azure Power BI npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2dfeb-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="2dfeb-109">예</span><span class="sxs-lookup"><span data-stu-id="2dfeb-109">Example</span></span>

<span data-ttu-id="2dfeb-110">이 예제에서는 기존 리소스 그룹에 작업 영역 컬렉션을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2dfeb-110">This example creates a workspace collection in an existing resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2dfeb-111">샘플</span><span class="sxs-lookup"><span data-stu-id="2dfeb-111">Samples</span></span>

<span data-ttu-id="2dfeb-112">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="2dfeb-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
