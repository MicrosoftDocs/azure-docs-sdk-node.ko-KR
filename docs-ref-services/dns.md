---
title: Node.js용 Azure DNS 모듈
description: Node.js용 Azure DNS 모듈에 대한 참조
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 93eec1890fc15d19c0545086a53b751d0886988a
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52106334"
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="5a18a-103">Node.js용 Azure DNS 모듈</span><span class="sxs-lookup"><span data-stu-id="5a18a-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="5a18a-104">Azure DNS을 사용하여 Azure에서 DNS(Domain Name System) 도메인을 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="5a18a-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="5a18a-105">다른 Azure 서비스와 동일한 자격 증명, 청구 및 지원 계약을 사용하여 DNS 레코드를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5a18a-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="5a18a-106">Azure 기반 서비스를 해당 DNS 업데이트와 원활하게 통합하고 종단 간 배포 프로세스를 간소화합니다.</span><span class="sxs-lookup"><span data-stu-id="5a18a-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="5a18a-107">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="5a18a-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5a18a-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="5a18a-108">Install the npm module</span></span>

<span data-ttu-id="5a18a-109">Azure DNS npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5a18a-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="5a18a-110">예</span><span class="sxs-lookup"><span data-stu-id="5a18a-110">Example</span></span>

<span data-ttu-id="5a18a-111">이 예제에서는 DNS 관리 영역을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="5a18a-111">This example lists the DNS Management zones.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="5a18a-112">샘플</span><span class="sxs-lookup"><span data-stu-id="5a18a-112">Samples</span></span>

<span data-ttu-id="5a18a-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="5a18a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
