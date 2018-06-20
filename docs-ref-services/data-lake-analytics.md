---
title: Node.js용 Azure Data Lake Analytics 모듈
description: Node.js용 Azure Data Lake Analytics 모듈에 대한 참조
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 28dae604ae9977eb33470757e207ac12a592c676
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
ms.locfileid: "28116968"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a>Node.js용 Azure Data Lake Analytics 모듈

Azure Data Lake Analytics는 빅 데이터 분석을 간소화하는 주문형 분석 작업 서비스입니다. 분산된 인프라 작업보다는 작업 작성, 실행 및 관리에 초점을 맞출 수 있습니다. 하드웨어를 배포, 구성 및 조정하는 대신, 데이터를 변형하고 귀중한 통찰력을 얻기 위한 쿼리를 작성합니다. 이 분석 서비스는 필요한 전력 크기만큼 다이얼을 설정하여 어떤 크기의 작업도 즉시 처리할 수 있습니다. 실행할 때 작업 기준으로 비용이 부과되므로 비용 효과적일 수 있습니다. 이 분석 서비스는 온-프레미스 ID 시스템과 통합되어 액세스 및 역할을 관리할 수 있도록 하는 Azure Active Directory를 지원합니다. 또한 이 서비스에는 SQL의 장점을 사용자 코드의 표현 능력과 결합한 U-SQL 언어가 포함되어 있습니다. U-SQL의 확장 가능한 분산 런타임을 통해 저장소와 Azure, Azure SQL Database 및 Azure SQL Data Warehouse의 SQL Server 간에 데이터를 효과적으로 분석할 수 있습니다.

### <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-module"></a>npm 모듈 설치

npm을 사용하여 Node.js용 Azure Data Lake Analytics 모듈을 설치합니다.

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a>예

이 예제에서는 지정된 구독에 대한 모든 분석 계정을 나열합니다.

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
