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
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="160f4-104">Node.js용 Azure HDInsight 모듈</span><span class="sxs-lookup"><span data-stu-id="160f4-104">Azure HDInsight Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="160f4-105">개요</span><span class="sxs-lookup"><span data-stu-id="160f4-105">Overview</span></span>

<span data-ttu-id="160f4-106">Azure HDInsight는 HDP(Hortonworks Data Platform)의 Hadoop 구성 요소를 클라우드에 배포한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="160f4-106">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="160f4-107">Apache Hadoop은 컴퓨터의 클러스터에서 빅 데이터 집합을 분산 처리하고 분석하기 위한 원래의 오픈 소스 프레임워크였습니다.</span><span class="sxs-lookup"><span data-stu-id="160f4-107">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="160f4-108">HDInsight는 다음과 같이 Hadoop 기술을 더 쉽게 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="160f4-108">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="160f4-109">간단한 설정 및 구성 -</span><span class="sxs-lookup"><span data-stu-id="160f4-109">Less setup and configuration.</span></span> <span data-ttu-id="160f4-110">'HDInsight에서 Hadoop 클러스터 프로비전' 참조</span><span class="sxs-lookup"><span data-stu-id="160f4-110">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="160f4-111">고가용성 및 안정성 -.</span><span class="sxs-lookup"><span data-stu-id="160f4-111">High availability and reliability.</span></span> <span data-ttu-id="160f4-112">'HDInsight 가용성 및 안정성' 참조</span><span class="sxs-lookup"><span data-stu-id="160f4-112">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="160f4-113">Active Directory와의 통합을 통한 보안 및 관리 -</span><span class="sxs-lookup"><span data-stu-id="160f4-113">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="160f4-114">'도메인 가입 클러스터' 참조</span><span class="sxs-lookup"><span data-stu-id="160f4-114">See Domain-joined clusters.</span></span>
- <span data-ttu-id="160f4-115">작업 중단 없이 동적 확장</span><span class="sxs-lookup"><span data-stu-id="160f4-115">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="160f4-116">구성 요소 업데이트 및 최신 버전 -</span><span class="sxs-lookup"><span data-stu-id="160f4-116">Component updates and current versions.</span></span> <span data-ttu-id="160f4-117">'HDInsight의 Hadoop 구성 요소 및 버전' 참조</span><span class="sxs-lookup"><span data-stu-id="160f4-117">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="160f4-118">다른 Azure 서비스(Web Apps 및 SQL Database 포함)와의 통합</span><span class="sxs-lookup"><span data-stu-id="160f4-118">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="160f4-119">Hadoop 기술 스택에는 Apache Hive, HBase, Spark, Kafka 및 기타 등등 관련 소프트웨어 및 유틸리티가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="160f4-119">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="160f4-120">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="160f4-120">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="160f4-121">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="160f4-121">Install the npm modules</span></span>

<span data-ttu-id="160f4-122">npm을 사용하여 Node.js용 Azure HDInsight 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="160f4-122">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="160f4-123">예제</span><span class="sxs-lookup"><span data-stu-id="160f4-123">Example</span></span> 

<span data-ttu-id="160f4-124">이 예제에서는 HDInsight 클라이언트를 만든 다음 사용 가능한 모든 클러스터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="160f4-124">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

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

## <a name="samples"></a><span data-ttu-id="160f4-125">샘플</span><span class="sxs-lookup"><span data-stu-id="160f4-125">Samples</span></span>

<span data-ttu-id="160f4-126">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="160f4-126">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
