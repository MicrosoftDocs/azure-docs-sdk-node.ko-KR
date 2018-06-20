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
ms.openlocfilehash: 6daeb443c2f1d8560a6a455cb6d174462b483f79
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264646"
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="05b9d-103">Node.js용 Azure Backup 모듈</span><span class="sxs-lookup"><span data-stu-id="05b9d-103">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="05b9d-104">개요</span><span class="sxs-lookup"><span data-stu-id="05b9d-104">Overview</span></span>

<span data-ttu-id="05b9d-105">Azure Backup은 Microsoft 클라우드에서 데이터를 백업(또는 보호)하고 복원하는 데 사용할 수 있는 Azure 기반 서비스이며,</span><span class="sxs-lookup"><span data-stu-id="05b9d-105">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="05b9d-106">기존의 온-프레미스 또는 오프사이트 백업 솔루션을 신뢰할 수 있고 안전하며 가격 경쟁력이 있는 클라우드 기반 솔루션으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="05b9d-106">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="05b9d-107">Azure Backup에서는 컴퓨터, 서버 또는 클라우드에 적절히 다운로드하고 배포하는 여러 구성 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05b9d-107">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="05b9d-108">배포하는 구성 요소 또는 에이전트는 보호하려는 대상에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="05b9d-108">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="05b9d-109">온-프레미스 또는 클라우드에서 데이터를 보호하는지 여부에 관계 없이 모든 Azure Backup 구성 요소는 Azure에서 Recovery Services 자격 증명 모음에 데이터를 백업하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05b9d-109">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="05b9d-110">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="05b9d-110">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="05b9d-111">npm을 사용하여 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="05b9d-111">Install the modules with npm</span></span>

<span data-ttu-id="05b9d-112">npm을 사용하여 Node.js용 Azure Backup 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="05b9d-112">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="05b9d-113">예</span><span class="sxs-lookup"><span data-stu-id="05b9d-113">Example</span></span>

<span data-ttu-id="05b9d-114">이 예제에서는 지정된 자격 증명 모음 및 리소스 그룹에 대한 복구 작업을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="05b9d-114">This example lists the recovery jobs for a given vault and resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="05b9d-115">샘플</span><span class="sxs-lookup"><span data-stu-id="05b9d-115">Samples</span></span>

<span data-ttu-id="05b9d-116">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="05b9d-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
