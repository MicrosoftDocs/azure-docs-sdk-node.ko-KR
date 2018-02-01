---
title: "Node.js용 Azure Site Recovery 모듈"
description: "Node.js용 Azure Site Recovery 모듈에 대한 참조"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: a1f3e1c18be68dd7e68f38e353e0c2ba224fbaa1
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-site-recovery-modules-for-nodejs"></a>Node.js용 Azure Site Recovery 모듈

Site Recovery를 사용하면 지역, 온-프레미스 가상 머신 및 물리적 서버 사이의 Azure VM을 Azure로 복제하거나 온-프레미스 컴퓨터를 보조 데이터 센터로 복제하도록 자동화할 수 있습니다.

[Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)에 대해 자세히 알아보세요.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure Site Recovery 서비스 npm 모듈을 설치합니다.

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a>예

이 예제에서는 리소스 그룹에 대한 Site Recovery 서비스를 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
