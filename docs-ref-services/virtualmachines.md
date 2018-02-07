---
title: "Node.js용 Virtual Machine 모듈 - Azure"
description: "Node.js용 Azure Virtual Machine 모듈 참조"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 608a915499d7c32c2c8b04464f716fa4fd17243d
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a>Node.js용 Azure Virtual Machine 모듈

## <a name="overview"></a>개요

Node.js용 Azure 관리 모듈을 사용하여 코드에서 새 Windows 및 Linux 가상 머신 및 가상 머신 확장 집합을 정의, 구성 및 배포합니다. 이 모듈을 사용하면 기존 가상 머신을 시작 및 중지하고 Azure 구독에서 중지된 VM에 디스크를 연결하거나 분리할 수 있습니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure Compute npm 모듈을 설치합니다.

```bash
npm install azure-arm-compute
```   

### <a name="example"></a>예

다음 예제에서는 Azure에 로그인하여 관리 클라이언트를 만들고, 지정된 위치, 게시자, 제품 및 SKU에 대한 모든 VM 이미지를 나열하는 방법을 보여 줍니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>샘플

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
