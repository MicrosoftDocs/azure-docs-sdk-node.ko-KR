---
title: Node.js용 Azure Key Vault 모듈
description: Node.js용 Azure Key Vault 모듈에 대한 참조
author: barclayn
ms.author: barclayn
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: 72bf4bc5443618f5f1bb9b4d1bb4d905669ff8c8
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-key-vault-modules-for-nodejs"></a>Node.js용 Azure Key Vault 모듈

Azure Key Vault는 클라우드 응용 프로그램 및 서비스에서 사용되는 암호화 키 및 비밀을 보호하는데 도움이 됩니다. Key Vault를 사용하여, 키와 비밀(예: 인증 키, 저장소 계정 키, 데이터 암호화 키, PFX 파일 및 암호)을 암호화에 하드웨어 보안 모듈(HSM)로 보호된 키를 사용합니다. 추가된 보증을 위해, HSM에서 키를 생성하거나 가져올 수 있습니다. 이 작업을 수행하려면 Microsoft는 FIPS 140-2 Level 2 유효성 검사가 적용된 HSM(하드웨어 및 펌웨어)에서 키를 처리합니다.

키 자격 증명 모음은 키 관리 프로세스를 간소화하고 데이터를 액세스하고 암호화 하는 키의 제어를 유지할 수 있습니다. 개발자는 개발 및 테스트(분)을 위한 키를 만든 다음, 프로덕션 키로 원활하게 마이그레이션할 수 있습니다. 보안 관리자는 필요한 경우 권한을 키로 부여(및 해지)할 수 있습니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치 

Azure Key Vault npm 모듈을 설치합니다.

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a>예

이 예제에서는 Azure에서 새 Key Vault 서비스를 만듭니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const KeyVaultManagementClient = require('azure-arm-keyvault');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const vaultName = 'your-new-vault';
const tenantGUID = 'your-tenant-guid';

// Interactive Login
let client;
msRestAzure
  .interactiveLogin()
  .then(credentials => {
    client = new KeyVaultManagementClient(credentials, subscriptionId);
    return client.vaults.list();
  })
  .then(vaults => {
    console.dir(vaults, { depth: null, colors: true });
    const parameters = {
      location: 'East US',
      properties: {
        sku: { family: 'A', name: 'standard' },
        accessPolicies: [],
        enabledForDeployment: false,
        tenantId: tenantGUID
      }
    };
    console.info('Creating vault ${vaultName} ...');
    return client.vaults.createOrUpdate(resourceGroup, vaultName, parameters);
  })
  .then(vault => console.dir(vault, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error occured');
    console.dir(err, { depth: null, colors: true });
    return err;
  });
```

## <a name="samples"></a>샘플

- [Node.js에서 Key Vault 시작](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [Node.js를 사용하여 Azure 리소스 및 리소스 그룹 관리](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [Azure AD를 NodeJS 웹 응용 프로그램에 통합(영문)](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
