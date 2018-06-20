---
title: Node.js용 Azure Virtual Network 모듈
description: Node.js용 Azure Virtual Network 모듈에 대한 참조
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 456839dbecb9ddd1ad0d4b3f8aa7570a04c100b1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260702"
---
# <a name="azure-virtual-network-modules-for-nodejs"></a>Node.js용 Azure Virtual Network 모듈

## <a name="overview"></a>개요

Azure Virtual Network 서비스를 사용하면 가상 네트워크(VNet)를 통해 Azure 리소스를 서로 안전하게 연결할 수 있습니다. VNet은 클라우드에 있는 사용자의 네트워크를 나타내며, 구독 전용 Azure 클라우드를 논리적으로 격리한 것입니다. 이 VNet을 온-프레미스 네트워크에 연결할 수도 있습니다.

[Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)에 대해 자세히 알아보세요.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure Virtual Network npm 모듈을 설치합니다.

```bash
npm install azure-arm-network
```

### <a name="example"></a>예

이 예제에서는 가상 네트워크 목록을 가져오고 인쇄합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
