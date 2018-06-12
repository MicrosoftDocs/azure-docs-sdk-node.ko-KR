---
title: Node.js용 Azure Container Service 모듈
description: Node.js용 Azure Container Service 모듈에 대한 참조
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Service
ms.openlocfilehash: 2d0aac2f7f6cc70ab3e40f7b3ccee6f64a011b55
ms.sourcegitcommit: 702a716434eb42f55d8782feb62ae2c6d8147aa9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689833"
---
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a>Node.js용 Microsoft Azure SDK -ContainerServiceClient
이 프로젝트는 Azure에 액세스하기 위한 Node.js 패키지를 제공합니다. 현재는 다음이 지원됩니다.
- **Node.js 버전 6.x.x 이상**

## <a name="features"></a>기능


## <a name="how-to-install"></a>설치 방법

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a>사용 방법

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a>예를 들어 인증, 클라이언트 만들기 및 containerServices 리스트가 있습니다.

```javascript
const msRestAzure = require("ms-rest-azure");
const ContainerServiceClient = require("azure-arm-containerservice");
msRestAzure.interactiveLogin().then((creds) => {
    const subscriptionId = "<Subscription_Id>";
    const client = new ContainerServiceClient(creds, subscriptionId);
    return client.containerServices.list().then((result) => {
      console.log("The result is:");
      console.log(result);
    });
}).catch((err) => {
  console.log('An error ocurred:');
  console.dir(err, {depth: null, colors: true});
});
```

## <a name="related-projects"></a>관련된 프로젝트

- [Node.js용 Microsoft Azure SDK](https://github.com/Azure/azure-sdk-for-node)