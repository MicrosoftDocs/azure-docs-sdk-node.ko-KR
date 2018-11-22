---
title: Node.js용 Azure Backup 모듈
description: Node.js용 Azure Backup 모듈에 대한 참조
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: bf3e66ac8341cebd28dee20b6370ed3e5fbfbfa0
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52038218"
---
# <a name="azure-backup-modules-for-nodejs"></a>Node.js용 Azure Backup 모듈

## <a name="overview"></a>개요

Azure Backup은 Microsoft 클라우드에서 데이터를 백업(또는 보호)하고 복원하는 데 사용할 수 있는 Azure 기반 서비스이며, 기존의 온-프레미스 또는 오프사이트 백업 솔루션을 신뢰할 수 있고 안전하며 가격 경쟁력이 있는 클라우드 기반 솔루션으로 대체합니다. Azure Backup에서는 컴퓨터, 서버 또는 클라우드에 적절히 다운로드하고 배포하는 여러 구성 요소를 제공합니다. 배포하는 구성 요소 또는 에이전트는 보호하려는 대상에 따라 달라집니다. 온-프레미스 또는 클라우드에서 데이터를 보호하는지 여부에 관계 없이 모든 Azure Backup 구성 요소는 Azure에서 Recovery Services 자격 증명 모음에 데이터를 백업하는 데 사용할 수 있습니다. 

## <a name="management-package"></a>관리 패키지

### <a name="install-the-modules-with-npm"></a>npm을 사용하여 모듈 설치

npm을 사용하여 Node.js용 Azure Backup 모듈을 설치합니다.

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a>예

이 예제에서는 지정된 자격 증명 모음 및 리소스 그룹에 대한 복구 작업을 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
