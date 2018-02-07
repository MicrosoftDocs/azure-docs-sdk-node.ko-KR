---
title: "Azure의 Node.js 개발자용 도구 | Microsoft Docs"
description: "Azure에 Node.js 개발을 위한 개별 도구를 설치합니다."
services: multiple
author: craigshoemaker
manager: routlaw
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 11/07/2017
ms.author: cshoe
ms.openlocfilehash: e9fe95ce6c02d50a70ea51284174c938796148fe
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-tools-for-nodejs-developers"></a><span data-ttu-id="2ec6a-103">Node.js 개발자용 Azure 도구</span><span class="sxs-lookup"><span data-stu-id="2ec6a-103">Azure tools for Node.js developers</span></span>
<span data-ttu-id="2ec6a-104">Node.js를 통해 Azure를 사용하는 개발에서는 다음과 같은 도구를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2ec6a-104">The following tools are recommended for developing with Azure on Node.js.</span></span>

## <a name="azure-cli"></a><span data-ttu-id="2ec6a-105">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="2ec6a-105">Azure CLI</span></span>
<span data-ttu-id="2ec6a-106">Azure CLI는 명령줄에서 Azure 리소스를 관리하기 위해 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ec6a-106">Azure CLI is optimized for managing Azure resources from the command line.</span></span>

![CLI](media/node-azure-tools/cli.png)
 
> [!div class="nextstepaction"]
> [<span data-ttu-id="2ec6a-108">Azure CLI 2.0 설치</span><span class="sxs-lookup"><span data-stu-id="2ec6a-108">Install the Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)

## <a name="visual-studio-code"></a><span data-ttu-id="2ec6a-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2ec6a-109">Visual Studio Code</span></span>
<span data-ttu-id="2ec6a-110">모든 OS에서 Node.js 앱을 편집하고 디버그합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec6a-110">Edit and debug Node.js apps on any OS.</span></span>

![Visual Studio Code](media/node-azure-tools/vs-code.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ec6a-112">Visual Studio Code 다운로드</span><span class="sxs-lookup"><span data-stu-id="2ec6a-112">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="azure-extensions"></a><span data-ttu-id="2ec6a-113">Azure 확장</span><span class="sxs-lookup"><span data-stu-id="2ec6a-113">Azure Extensions</span></span>
<span data-ttu-id="2ec6a-114">Visual Studio Code에서 직접 Azure 서비스를 통해 인터페이스에 다음과 같은 사용 가능한 확장을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec6a-114">Use the following free extensions to interface with Azure services directly in Visual Studio Code.</span></span>

| <span data-ttu-id="2ec6a-115">도구</span><span class="sxs-lookup"><span data-stu-id="2ec6a-115">Tool</span></span> | <span data-ttu-id="2ec6a-116">설명</span><span class="sxs-lookup"><span data-stu-id="2ec6a-116">Description</span></span>  |
|:---------:|---------|
| [<span data-ttu-id="2ec6a-117">Azure 기능</span><span class="sxs-lookup"><span data-stu-id="2ec6a-117">Azure Functions</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions) <br> <span data-ttu-id="2ec6a-118">[![Azure Functions 도구](media/node-azure-tools/icon-azure-functions.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)</span><span class="sxs-lookup"><span data-stu-id="2ec6a-118">[![Azure Functions Tools](media/node-azure-tools/icon-azure-functions.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)</span></span> | <span data-ttu-id="2ec6a-119">함수 만들기, 관리, 보기, 디버그 및 배포</span><span class="sxs-lookup"><span data-stu-id="2ec6a-119">Create, manage, view, debug, and deploy functions</span></span>|
| [<span data-ttu-id="2ec6a-120">Azure App Service</span><span class="sxs-lookup"><span data-stu-id="2ec6a-120">Azure App Service</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice) <br> <span data-ttu-id="2ec6a-121">[![App Service 도구](media/node-azure-tools/icon-azure-app-service.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice)</span><span class="sxs-lookup"><span data-stu-id="2ec6a-121">[![App Service Tools](media/node-azure-tools/icon-azure-app-service.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice)</span></span> | <span data-ttu-id="2ec6a-122">사이트 및 Azure Portal 찾아보기, 새 사이트 만들기(Node.js의 Linux 전용) 및 슬롯에 배포</span><span class="sxs-lookup"><span data-stu-id="2ec6a-122">Browse sites and the Azure portal, create new sites (Linux on Node.js only) and deploy to slots</span></span> |
| [<span data-ttu-id="2ec6a-123">Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="2ec6a-123">Cosmos DB </span></span>](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)  <br> <span data-ttu-id="2ec6a-124">[![Cosmos DB 도구](media/node-azure-tools/icon-cosmos-db.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)</span><span class="sxs-lookup"><span data-stu-id="2ec6a-124">[![Cosmos DB Tools](media/node-azure-tools/icon-cosmos-db.png)](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)</span></span>| <span data-ttu-id="2ec6a-125">Azure에서 전역적으로 분산된 다중 model 데이터베이스 만들기, 찾아보기 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="2ec6a-125">Create, browse, and update globally distributed, multi-model databases in Azure</span></span> |
| [<span data-ttu-id="2ec6a-126">Docker</span><span class="sxs-lookup"><span data-stu-id="2ec6a-126">Docker</span></span>](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)   <br> <span data-ttu-id="2ec6a-127">[![Cosmos DB 도구](media/node-azure-tools/icon-docker.png)](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)</span><span class="sxs-lookup"><span data-stu-id="2ec6a-127">[![Cosmos DB Tools](media/node-azure-tools/icon-docker.png)](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-explorer)</span></span>| <span data-ttu-id="2ec6a-128">Docker 컨테이너 및 이미지, Docker 허브 및 Azure Container Registry 관리</span><span class="sxs-lookup"><span data-stu-id="2ec6a-128">Manage Docker containers and images, Docker Hub, and Azure container registry</span></span> |

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ec6a-129">Visual Studio Code 마켓플레이스에서 Azure 확장 기능 가져오기</span><span class="sxs-lookup"><span data-stu-id="2ec6a-129">Get more Azure extensions in the Visual Studio Code marketplace</span></span>](https://marketplace.visualstudio.com/search?term=azure&target=VSCode&category=All%20categories&sortBy=Relevance)