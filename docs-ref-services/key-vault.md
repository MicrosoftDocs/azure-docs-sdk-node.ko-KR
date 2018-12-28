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
ms.openlocfilehash: 36bc5e97a5eea6e821f66bff9b3e8f610baa2dd0
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52098868"
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="9a884-103">Node.js용 Azure Key Vault 모듈</span><span class="sxs-lookup"><span data-stu-id="9a884-103">Azure Key Vault modules for Node.js</span></span>

<span data-ttu-id="9a884-104">Azure Key Vault는 클라우드 애플리케이션 및 서비스에서 사용되는 암호화 키 및 비밀을 보호하는데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a884-104">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="9a884-105">Key Vault를 사용하여, 키와 비밀(예: 인증 키, 저장소 계정 키, 데이터 암호화 키, PFX 파일 및 암호)을 암호화에 하드웨어 보안 모듈(HSM)로 보호된 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9a884-105">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="9a884-106">추가된 보증을 위해, HSM에서 키를 생성하거나 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a884-106">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="9a884-107">이 작업을 수행하려면 Microsoft는 FIPS 140-2 Level 2 유효성 검사가 적용된 HSM(하드웨어 및 펌웨어)에서 키를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="9a884-107">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="9a884-108">키 자격 증명 모음은 키 관리 프로세스를 간소화하고 데이터를 액세스하고 암호화 하는 키의 제어를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a884-108">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="9a884-109">개발자는 개발 및 테스트(분)을 위한 키를 만든 다음, 프로덕션 키로 원활하게 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a884-109">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="9a884-110">보안 관리자는 필요한 경우 권한을 키로 부여(및 해지)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a884-110">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="9a884-111">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="9a884-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9a884-112">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="9a884-112">Install the npm module</span></span> 

<span data-ttu-id="9a884-113">Azure Key Vault npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="9a884-113">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="9a884-114">예</span><span class="sxs-lookup"><span data-stu-id="9a884-114">Example</span></span>

<span data-ttu-id="9a884-115">이 예제에서는 Azure에서 새 Key Vault 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9a884-115">This example creates a new Key Vault service in Azure.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9a884-116">샘플</span><span class="sxs-lookup"><span data-stu-id="9a884-116">Samples</span></span>

- [<span data-ttu-id="9a884-117">Node.js에서 Key Vault 시작</span><span class="sxs-lookup"><span data-stu-id="9a884-117">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="9a884-118">Node.js를 사용하여 Azure 리소스 및 리소스 그룹 관리</span><span class="sxs-lookup"><span data-stu-id="9a884-118">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [<span data-ttu-id="9a884-119">Azure AD를 NodeJS 웹 응용 프로그램에 통합(영문)</span><span class="sxs-lookup"><span data-stu-id="9a884-119">Integrating Azure AD into a NodeJS web application</span></span>](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

<span data-ttu-id="9a884-120">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="9a884-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
