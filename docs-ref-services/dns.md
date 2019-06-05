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
# <a name="azure-dns-modules-for-nodejs"></a>Node.js용 Azure DNS 모듈

Azure DNS을 사용하여 Azure에서 DNS(Domain Name System) 도메인을 호스팅합니다. 다른 Azure 서비스와 동일한 자격 증명, 청구 및 지원 계약을 사용하여 DNS 레코드를 관리합니다. Azure 기반 서비스를 해당 DNS 업데이트와 원활하게 통합하고 엔드투엔드 배포 프로세스를 간소화합니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure DNS npm 모듈을 설치합니다.

```bash
npm install azure-arm-dns
```

### <a name="example"></a>예

이 예제에서는 DNS 관리 영역을 나열합니다.

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

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
