---
title: "Node.js용 Azure Relay 모듈"
description: "Node.js용 Azure Relay 모듈에 대한 참조"
keywords: Azure, SDK, API, Relay, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 7e958433e0d3cc6b464bb5980d4f161323a18ab2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="dda81-104">Node.js용 Azure Relay 모듈</span><span class="sxs-lookup"><span data-stu-id="dda81-104">Azure Relay modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="dda81-105">개요</span><span class="sxs-lookup"><span data-stu-id="dda81-105">Overview</span></span>

<span data-ttu-id="dda81-106">Azure Relay 서비스는 방화벽 연결을 열거나 회사 네트워크 인프라를 주입식으로 변경하지 않고도 회사 엔터프라이즈 네트워크 내에 있는 서비스를 공용 클라우드에 안전하게 노출할 수 있게 함으로써 하이브리드 응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dda81-106">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="dda81-107">릴레이는 다양한 전송 프로토콜 및 웹 서비스 표준을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dda81-107">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="dda81-108">[Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="dda81-108">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="dda81-109">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="dda81-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="dda81-110">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="dda81-110">Install the npm module</span></span>

<span data-ttu-id="dda81-111">Azure Relay npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="dda81-111">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="dda81-112">예제</span><span class="sxs-lookup"><span data-stu-id="dda81-112">Example</span></span>

<span data-ttu-id="dda81-113">이 예제에서는 Relay 클라이언트에 대한 네임스페이스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="dda81-113">This example lists the namespaces for a Relay client.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="dda81-114">샘플</span><span class="sxs-lookup"><span data-stu-id="dda81-114">Samples</span></span>

<span data-ttu-id="dda81-115">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="dda81-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
