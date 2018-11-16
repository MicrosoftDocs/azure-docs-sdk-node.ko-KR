---
title: Node.js용 Azure 권한 부여 모듈
description: Node.js용 Azure 권한 부여 모듈에 대한 참조
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 0b0ecd088d8b7728e56f352597e2db038678945f
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51480847"
---
# <a name="azure-authorization-modules-for-nodejs"></a>Node.js용 Azure 권한 부여 모듈

## <a name="overview"></a>개요

Azure App Service 인증/권한 부여는 앱 백 엔드에서 코드를 변경할 필요가 없도록 사용자가 응용 프로그램에 로그인하는 방법을 제공하는 기능입니다. 권한 부여는 응용 프로그램을 보호하고 사용자별 데이터로 작업하는 쉬운 방법을 제공합니다.

## <a name="management-package"></a>관리 패키지

npm을 사용하여 Node.js용 Azure 권한 부여 모듈을 설치합니다.

### <a name="install-the-npm-module"></a>npm 모듈 설치

Azure 권한 부여 npm 모듈을 설치합니다.

```bash
npm install azure-arm-authorization
```

### <a name="example"></a>예

이 예제에서는 요청된 리소스 그룹에 대한 모든 역할 할당을 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
