---
title: "Node.js를 사용하여 Azure 서비스 사용자 만들기"
description: "Node.js를 통해 서비스 사용자 인증을 사용하는 방법을 알아봅니다."
keywords: "Azure, Node, SDK, API, 인증, Active Directory, 서비스 사용자"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: faa97e7a9ab6a8b6e04eeee590c7b642d26ba620
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="5e5f0-104">Node.js를 사용하여 Azure 서비스 사용자 만들기</span><span class="sxs-lookup"><span data-stu-id="5e5f0-104">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="5e5f0-105">앱에서 리소스에 액세스해야 하는 경우 앱에 대한 ID를 설정하고 자체의 자격 증명으로 해당 앱을 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-105">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="5e5f0-106">이 ID를 *서비스 사용자*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-106">This identity is known as a *service principal*.</span></span> <span data-ttu-id="5e5f0-107">기본적으로 Azure Active Directory 계정에 대한 키를 만들어 사용자 개입이나 사용자 이름/암호를 요구하는 대신 SDK를 제공하여 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-107">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="5e5f0-108">서비스 사용자 방법을 통해 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-108">The service principal approach enables you to:</span></span>
- <span data-ttu-id="5e5f0-109">자체 사용 권한과 다른 앱 ID에 대한 사용 권한을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-109">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="5e5f0-110">일반적으로 이러한 권한은 정확히 앱 실행에 필요한 것으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-110">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="5e5f0-111">무인 스크립트를 실행할 때 인증용 인증서를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-111">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="5e5f0-112">이 항목에서는 서비스 사용자를 만드는 세 가지 기술을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-112">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="5e5f0-113">Azure portal</span><span class="sxs-lookup"><span data-stu-id="5e5f0-113">Azure portal</span></span>
- <span data-ttu-id="5e5f0-114">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="5e5f0-114">Azure CLI 2.0</span></span>
- <span data-ttu-id="5e5f0-115">Node.js용 Azure SDK</span><span class="sxs-lookup"><span data-stu-id="5e5f0-115">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="5e5f0-116">Azure Portal을 사용하여 서비스 사용자 만들기</span><span class="sxs-lookup"><span data-stu-id="5e5f0-116">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="5e5f0-117">[포털을 사용하여 리소스에 액세스할 수 있는 Azure Active Directory 응용 프로그램 및 서비스 사용자 만들기](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) 항목에서 설명하는 단계에 따라 서비스 사용자를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-117">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="5e5f0-118">Azure CLI 2.0을 사용하여 서비스 사용자 만들기</span><span class="sxs-lookup"><span data-stu-id="5e5f0-118">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="5e5f0-119">[Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)을 사용하여 서비스 사용자를 만드는 작업은 다음 단계를 통해 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-119">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="5e5f0-120">[Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-120">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="5e5f0-121">터미널 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-121">Open a terminal window.</span></span>

3. <span data-ttu-id="5e5f0-122">다음 명령을 입력하여 로그인 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-122">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="5e5f0-123">`az login`을 호출하면 URL과 코드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-123">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="5e5f0-124">지정된 URL로 이동하고, 코드를 입력하고, Azure ID로 로그인합니다(이미 로그인한 경우 자동으로 발생할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="5e5f0-124">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="5e5f0-125">그러면 CLI를 통해 계정에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-125">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="5e5f0-126">Azure 구독 및 테넌트 ID를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-126">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="5e5f0-127">다음은 출력 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-127">The following shows an example of the output:</span></span>

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    <span data-ttu-id="5e5f0-128">**구독 ID는 7단계에서 사용되므로 기록해 두세요.**</span><span class="sxs-lookup"><span data-stu-id="5e5f0-128">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="5e5f0-129">서비스 사용자를 만들어 Azure로 인증하는 데 필요한 다른 정보를 포함하는 JSON 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-129">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="5e5f0-130">다음은 출력 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-130">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="5e5f0-131">**tenant, name 및 password 값은 7단계에서 사용되므로 기록해 두세요.**</span><span class="sxs-lookup"><span data-stu-id="5e5f0-131">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="5e5f0-132">환경 변수 설정 - &lt;subscriptionId>, &lt;tenant>, &lt;name> 및 &lt;password> 자리 표시자를 4단계 및 5단계에서 얻은 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-132">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="5e5f0-133">**bash 사용**</span><span class="sxs-lookup"><span data-stu-id="5e5f0-133">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="5e5f0-134">**PowerShell 사용**</span><span class="sxs-lookup"><span data-stu-id="5e5f0-134">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="5e5f0-135">Node.js용 Azure SDK를 사용하여 서비스 사용자 만들기</span><span class="sxs-lookup"><span data-stu-id="5e5f0-135">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="5e5f0-136">JavaScript를 사용하여 프로그래밍 방식으로 서비스 사용자를 만들려면 [ServicePrincipal 스크립트(영문)](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-136">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="5e5f0-137">서비스 사용자 사용</span><span class="sxs-lookup"><span data-stu-id="5e5f0-137">Using the service principal</span></span>

<span data-ttu-id="5e5f0-138">서비스 사용자가 있는 경우 다음 JavaScript 코드 조각에서는 Node.js용 Azure SDK를 사용하여 서비스 사용자 키를 통해 인증하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-138">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="5e5f0-139">&lt;clientId 또는 appId>, &lt;secret 또는 password>, &lt;domain 또는 tenant> 자리 표시자를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f0-139">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
