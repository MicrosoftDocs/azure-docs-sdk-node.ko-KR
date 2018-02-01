---
title: "Node.js용 Azure 관리 모듈을 사용하여 인증"
description: "서비스 사용자를 통해 Node.js용 Azure 관리 모듈에 인증합니다."
author: craigshoemaker
manager: routlaw
ms.author: cshoe
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: c93e5205c43c78d1c9e94d59a362cda336cd8310
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="a44ad-103">Node.js용 Azure 모듈을 사용하여 인증</span><span class="sxs-lookup"><span data-stu-id="a44ad-103">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="a44ad-104">모든 서비스 API에는 인스턴스화될 때 `credentials` 개체를 통한 인증이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ad-104">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="a44ad-105">Node.js용 Azure SDK를 통해 필요한 자격 증명을 인증하고 만드는 세 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ad-105">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="a44ad-106">기본 인증</span><span class="sxs-lookup"><span data-stu-id="a44ad-106">Basic authentication</span></span>
- <span data-ttu-id="a44ad-107">대화형 로그인</span><span class="sxs-lookup"><span data-stu-id="a44ad-107">Interactive login</span></span>
- <span data-ttu-id="a44ad-108">서비스 주체 인증</span><span class="sxs-lookup"><span data-stu-id="a44ad-108">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="a44ad-109">기본 인증</span><span class="sxs-lookup"><span data-stu-id="a44ad-109">Basic authentication</span></span>

<span data-ttu-id="a44ad-110">Azure 계정 자격 증명을 사용하여 프로그래밍 방식으로 인증하려면 `loginWithUsernamePassword` 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ad-110">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="a44ad-111">다음 JavaScript 코드 조각에서는 환경 변수로 저장된 자격 증명을 통해 기본 인증을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a44ad-111">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a><span data-ttu-id="a44ad-112">대화형 로그인</span><span class="sxs-lookup"><span data-stu-id="a44ad-112">Interactive login</span></span>

<span data-ttu-id="a44ad-113">대화형 로그인은 사용자가 브라우저에서 인증할 수 있게 하는 링크와 코드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ad-113">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="a44ad-114">동일한 스크립트에서 여러 계정을 사용하거나 사용자가 개입하는 것이 좋을 때 이 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a44ad-114">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="a44ad-115">서비스 주체 인증</span><span class="sxs-lookup"><span data-stu-id="a44ad-115">Service principal authentication</span></span>

<span data-ttu-id="a44ad-116">[대화형 로그인](#interactive-login)은 가장 쉬운 인증 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="a44ad-116">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="a44ad-117">그러나 Node.js SDK를 사용하는 경우 계정 자격 증명을 제공하는 대신 서비스 사용자 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ad-117">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="a44ad-118">[Node.js를 사용하여 Azure 서비스 사용자 만들기](./node-sdk-azure-authenticate-principal.md) 항목에서는 서비스 사용자를 만들고 사용하기 위한 다양한 기술을 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44ad-118">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 