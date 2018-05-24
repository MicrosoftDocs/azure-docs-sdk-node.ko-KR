---
title: Node.js용 Azure Container Registry 모듈
description: Node.js용 Azure Container Registry 모듈에 대한 참조
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: ca83b97e94312498f4f93c587cf0c90485136841
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="a91bd-103">Node.js용 Azure Container Registry 모듈</span><span class="sxs-lookup"><span data-stu-id="a91bd-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="a91bd-104">Azure Container Registry는 Docker 레지스트리 2.0 오픈 소스에 기반한 관리되는 Docker 레지스트리 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="a91bd-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="a91bd-105">Azure 컨테이너 레지스트리를 만들고 유지 관리하여 개인 Docker 컨테이너 이미지를 저장하고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="a91bd-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="a91bd-106">기존 컨테이너 배포 및 배포 파이프라인을 통해 Azure에서 컨테이너 레지스트리를 사용하고 Docker 커뮤니티 전문 기술 단체에 의지합니다.</span><span class="sxs-lookup"><span data-stu-id="a91bd-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="a91bd-107">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="a91bd-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a91bd-108">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="a91bd-108">Install the npm module</span></span>

<span data-ttu-id="a91bd-109">Azure Container Registry npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a91bd-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="a91bd-110">예</span><span class="sxs-lookup"><span data-stu-id="a91bd-110">Example</span></span>

<span data-ttu-id="a91bd-111">이 예제에서는 사용 가능한 컨테이너 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a91bd-111">This example gets a list of the available containers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="a91bd-112">샘플</span><span class="sxs-lookup"><span data-stu-id="a91bd-112">Samples</span></span>

<span data-ttu-id="a91bd-113">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="a91bd-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
