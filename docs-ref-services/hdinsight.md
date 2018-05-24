---
title: Node.js용 Azure HDInsight 모듈
description: Node.js용 Azure HDInsight 모듈에 대한 참조
author: mumian
ms.author: jgao
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 311933f619ceab5d679c8b0a767d3b52960c5ce1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="3e950-103">Node.js용 Azure HDInsight 모듈</span><span class="sxs-lookup"><span data-stu-id="3e950-103">Azure HDInsight Modules for Node.js</span></span>

<span data-ttu-id="3e950-104">Azure HDInsight는 HDP(Hortonworks Data Platform)의 Hadoop 구성 요소를 클라우드에 배포한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3e950-104">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="3e950-105">Apache Hadoop은 컴퓨터의 클러스터에서 빅 데이터 집합을 분산 처리하고 분석하기 위한 원래의 오픈 소스 프레임워크였습니다.</span><span class="sxs-lookup"><span data-stu-id="3e950-105">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="3e950-106">HDInsight는 다음과 같이 Hadoop 기술을 더 쉽게 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e950-106">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="3e950-107">간단한 설정 및 구성 -</span><span class="sxs-lookup"><span data-stu-id="3e950-107">Less setup and configuration.</span></span> <span data-ttu-id="3e950-108">'HDInsight에서 Hadoop 클러스터 프로비전' 참조</span><span class="sxs-lookup"><span data-stu-id="3e950-108">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="3e950-109">고가용성 및 안정성 -.</span><span class="sxs-lookup"><span data-stu-id="3e950-109">High availability and reliability.</span></span> <span data-ttu-id="3e950-110">'HDInsight 가용성 및 안정성' 참조</span><span class="sxs-lookup"><span data-stu-id="3e950-110">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="3e950-111">Active Directory와의 통합을 통한 보안 및 관리 -</span><span class="sxs-lookup"><span data-stu-id="3e950-111">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="3e950-112">'도메인 가입 클러스터' 참조</span><span class="sxs-lookup"><span data-stu-id="3e950-112">See Domain-joined clusters.</span></span>
- <span data-ttu-id="3e950-113">작업 중단 없이 동적 확장</span><span class="sxs-lookup"><span data-stu-id="3e950-113">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="3e950-114">구성 요소 업데이트 및 최신 버전 -</span><span class="sxs-lookup"><span data-stu-id="3e950-114">Component updates and current versions.</span></span> <span data-ttu-id="3e950-115">'HDInsight의 Hadoop 구성 요소 및 버전' 참조</span><span class="sxs-lookup"><span data-stu-id="3e950-115">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="3e950-116">다른 Azure 서비스(Web Apps 및 SQL Database 포함)와의 통합</span><span class="sxs-lookup"><span data-stu-id="3e950-116">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="3e950-117">Hadoop 기술 스택에는 Apache Hive, HBase, Spark, Kafka 및 기타 등등 관련 소프트웨어 및 유틸리티가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e950-117">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="3e950-118">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="3e950-118">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="3e950-119">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="3e950-119">Install the npm modules</span></span>

<span data-ttu-id="3e950-120">npm을 사용하여 Node.js용 Azure HDInsight 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3e950-120">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="3e950-121">예</span><span class="sxs-lookup"><span data-stu-id="3e950-121">Example</span></span> 

<span data-ttu-id="3e950-122">이 예제에서는 HDInsight 클라이언트를 만든 다음 사용 가능한 모든 클러스터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="3e950-122">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

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

## <a name="samples"></a><span data-ttu-id="3e950-123">샘플</span><span class="sxs-lookup"><span data-stu-id="3e950-123">Samples</span></span>

<span data-ttu-id="3e950-124">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="3e950-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
