---
title: "Node.js용 Azure HDInsight 모듈"
description: "Node.js용 Azure HDInsight 모듈에 대한 참조"
keywords: Azure, SDK, API, HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a>Node.js용 Azure HDInsight 모듈

## <a name="overview"></a>개요

Azure HDInsight는 HDP(Hortonworks Data Platform)의 Hadoop 구성 요소를 클라우드에 배포한 것입니다. Apache Hadoop은 컴퓨터의 클러스터에서 빅 데이터 집합을 분산 처리하고 분석하기 위한 원래의 오픈 소스 프레임워크였습니다.

HDInsight는 다음과 같이 Hadoop 기술을 더 쉽게 사용할 수 있게 합니다.
- 간단한 설정 및 구성 - 'HDInsight에서 Hadoop 클러스터 프로비전' 참조
- 고가용성 및 안정성 -. 'HDInsight 가용성 및 안정성' 참조
- Active Directory와의 통합을 통한 보안 및 관리 - '도메인 가입 클러스터' 참조
- 작업 중단 없이 동적 확장
- 구성 요소 업데이트 및 최신 버전 - 'HDInsight의 Hadoop 구성 요소 및 버전' 참조
- 다른 Azure 서비스(Web Apps 및 SQL Database 포함)와의 통합

Hadoop 기술 스택에는 Apache Hive, HBase, Spark, Kafka 및 기타 등등 관련 소프트웨어 및 유틸리티가 포함되어 있습니다. 

## <a name="management-package"></a>관리 패키지

### <a name="install-the-npm-modules"></a>npm 모듈 설치

npm을 사용하여 Node.js용 Azure HDInsight 모듈을 설치합니다.

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a>예제 

이 예제에서는 HDInsight 클라이언트를 만든 다음 사용 가능한 모든 클러스터를 나열합니다. 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a>샘플

앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.
