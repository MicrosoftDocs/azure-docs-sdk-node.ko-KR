---
title: Node.js용 Azure App Service 모듈
description: Node.js용 Azure App Service 모듈에 대한 참조
author: SyntaxC4
ms.author: cfowler
manager: jhubbard
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: d9cb33e9aead2878fc9571b1ccb3a34b8990af74
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-app-service-modules-for-nodejs"></a>Node.js용 Azure App Service 모듈

## <a name="overview"></a>개요

Azure App Service는 Microsoft Azure의 PaaS(Platform-as-a-Service) 제품입니다. 플랫폼 및 장치에 웹 및 모바일 앱을 만듭니다. SaaS 솔루션과 앱을 통합하고 온-프레미스 응용 프로그램을 사용하여 연결하고 비즈니스 프로세스를 자동화합니다. Azure는 공유 VM 리소스 또는 전용 VM을 선택하여 완전히 관리되는 VM(가상 머신)에서 앱을 실행합니다.

App Service는 이전에 개별적으로 Azure Websites 및 Azure Mobile Services로 전달한 웹 및 모바일 기능을 포함합니다. 또한 비즈니스 프로세스를 자동화하고 클라우드 API를 호스팅하는 새 기능을 포함합니다. 단일 통합 서비스인 App Service를 통해 웹 사이트, 모바일 앱 백 엔드, RESTful API 및 비즈니스 프로세스 등 다양한 구성 요소를 단일 솔루션으로 작성할 수 있습니다.

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-package"></a>npm 패키지 설치

Node.js용 Azure App Service 모듈을 설치합니다.

```bash
npm install azure-arm-website
```

### <a name="example"></a>예

이 예제에서는 Node.js를 사용하여 Azure에 웹 사이트를 만듭니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a>샘플

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
