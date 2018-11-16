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
ms.openlocfilehash: 97a846d9970310931e05e681b23b5787c97260b6
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51381378"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="ba506-103">Node.js용 Azure Data Lake Analytics 모듈</span><span class="sxs-lookup"><span data-stu-id="ba506-103">Azure Data Lake Analytics modules for Node.js</span></span>

<span data-ttu-id="ba506-104">Azure Data Lake Analytics는 빅 데이터 분석을 간소화하는 주문형 분석 작업 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-104">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="ba506-105">분산된 인프라 작업보다는 작업 작성, 실행 및 관리에 초점을 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-105">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="ba506-106">하드웨어를 배포, 구성 및 조정하는 대신, 데이터를 변형하고 귀중한 통찰력을 얻기 위한 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-106">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="ba506-107">이 분석 서비스는 필요한 전력 크기만큼 다이얼을 설정하여 어떤 크기의 작업도 즉시 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-107">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="ba506-108">실행할 때 작업 기준으로 비용이 부과되므로 비용 효과적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-108">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="ba506-109">이 분석 서비스는 온-프레미스 ID 시스템과 통합되어 액세스 및 역할을 관리할 수 있도록 하는 Azure Active Directory를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-109">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="ba506-110">또한 이 서비스에는 SQL의 장점을 사용자 코드의 표현 능력과 결합한 U-SQL 언어가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-110">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="ba506-111">U-SQL의 확장 가능한 분산 런타임을 통해 저장소와 Azure, Azure SQL Database 및 Azure SQL Data Warehouse의 SQL Server 간에 데이터를 효과적으로 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-111">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="ba506-112">관리 패키지</span><span class="sxs-lookup"><span data-stu-id="ba506-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ba506-113">npm 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="ba506-113">Install the npm module</span></span>

<span data-ttu-id="ba506-114">npm을 사용하여 Node.js용 Azure Data Lake Analytics 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-114">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="ba506-115">예</span><span class="sxs-lookup"><span data-stu-id="ba506-115">Example</span></span>

<span data-ttu-id="ba506-116">이 예제에서는 지정된 구독에 대한 모든 분석 계정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-116">This example lists all of the analytics accounts for a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ba506-117">샘플</span><span class="sxs-lookup"><span data-stu-id="ba506-117">Samples</span></span>

<span data-ttu-id="ba506-118">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="ba506-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
