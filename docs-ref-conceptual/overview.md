---
title: JavaScript용 Azure 모듈
description: JavaScript용 Azure 관리 및 서비스 모듈에 대한 개요입니다.
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 1d97df65f12c465cf6c790d1e3c016a9ff4aa5ba
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50310970"
---
# <a name="azure-modules-for-javascript"></a><span data-ttu-id="18cf0-103">JavaScript용 Azure 모듈</span><span class="sxs-lookup"><span data-stu-id="18cf0-103">Azure modules for JavaScript</span></span>

<span data-ttu-id="18cf0-104">JavaScript용 Azure 모듈을 사용하여 JavaScript 응용 프로그램에서 Azure 리소스를 관리하고 서비스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-104">Manage Azure resources and connect to services from your JavaScript applications with the Azure modules for JavaScript.</span></span> <span data-ttu-id="18cf0-105">코드는 프로젝트에서 사용할 [npm 모듈](node-sdk-azure-install.md)로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-105">The code is available as [npm modules](node-sdk-azure-install.md) for use in your projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="18cf0-106">Azure 리소스 관리</span><span class="sxs-lookup"><span data-stu-id="18cf0-106">Manage Azure resources</span></span>

<span data-ttu-id="18cf0-107">관리 모듈을 사용하여 앱에서 리소스를 만들고 쿼리하거나 사용자 고유의 Azure 자동화 도구를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-107">Use management modules to create and query resources from your apps or to build your own Azure automation tools.</span></span> 

<span data-ttu-id="18cf0-108">예를 들어 기존 네트워크 인터페이스를 사용하여 Linux VM을 만들려면 다음 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-108">For example, to create a Linux VM using an existing network interface, you would write the following code:</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');

// read in service principal values from env variables
const clientId = process.env['CLIENT_ID'];
const domain = process.env['DOMAIN'];
const secret = process.env['APPLICATION_SECRET'];
const subscriptionId = process.env['AZURE_SUBSCRIPTION_ID'];

msRestAzure.loginWithServicePrincipalSecret(clientId, secret, domain, function (err, credentials, subscriptions) {
    if (err) return console.log(err);
    const computeClient = new ComputeManagementClient(credentials, subscriptionId);
    // customize the VM 
    const vmParameters = {
        location: "eastus",
        osProfile: {
            computerName: "newLinuxVM",
            adminUsername: adminUsername,
            adminPassword: adminPassword
        },
        linuxConfiguration: {
            ssh: {
                publicKeys: [mySshKey]
            }
        },
        hardwareProfile: {
            vmSize: 'Basic_A1'
        },
        networkProfile: {
            networkInterfaces: [
                {
                    id: myNetworkInterfaceId,
                    primary: true
                }
            ]
        },
        storageProfile: {
            imageReference: {
                publisher: 'Canonical',
                offer: 'UbuntuServer',
                sku: '16.04-LTS',
                version: 'latest'
            },
        }
    };
 
    // create the VM
    computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, function (err, data) {
        if (err) return console.log(err);
    });

});
```

<span data-ttu-id="18cf0-109">모듈의 전체 목록에 대한 [설치 지침](node-sdk-azure-install.md)과 인증 설정 및 샘플 코드 실행에 대한 [시작 문서](node-sdk-azure-get-started.md)를 검토하여 자신의 Azure 구독에 대한 리소스를 만들고 업데이트합니다 .</span><span class="sxs-lookup"><span data-stu-id="18cf0-109">Review the [install instructions](node-sdk-azure-install.md) for a full list of the modules and the [get started article](node-sdk-azure-get-started.md) to set up authentication and run sample code to create and update resources against your own Azure subscription.</span></span> 

## <a name="connect-to-azure-services"></a><span data-ttu-id="18cf0-110">Azure 서비스에 연결</span><span class="sxs-lookup"><span data-stu-id="18cf0-110">Connect to Azure services</span></span>

<span data-ttu-id="18cf0-111">Azure 모듈을 사용하여 Azure 내에서 리소스를 만들고 관리하는 것 외에도 패키지를 사용하여 앱에서 Azure 클라우드 서비스를 연결하고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-111">In addition to using the Azure modules to create and manage resources within Azure, you can also use packages to connect and use Azure cloud services in your apps.</span></span> <span data-ttu-id="18cf0-112">예를 들어 SQL Database 테이블을 업데이트하거나 Azure Storage에 파일을 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-112">For example, you might update a table SQL Database or upload files to Azure Storage.</span></span> <span data-ttu-id="18cf0-113">[전체 목록](node-sdk-azure-install.md)에서 특정 서비스에 필요한 패키지를 선택하고, 자습서 및 샘플 코드에 대한 [JavaScript 개발자 센터](https://azure.microsoft.com/develop/nodejs/)를 방문하여 앱에서 모듈을 사용하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-113">Select the package you need for a particular service from the [complete list](node-sdk-azure-install.md) and visit the [JavaScript developer center](https://azure.microsoft.com/develop/nodejs/) for tutorials and sample code to learn how to use the modules in your apps.</span></span>

<span data-ttu-id="18cf0-114">예를 들어 Azure 저장소 컨테이너에 있는 모든 Blob의 내용을 출력하려면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-114">For example, to print out the contents of every blob in an Azure storage container:</span></span>

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a><span data-ttu-id="18cf0-115">샘플 코드 및 참조</span><span class="sxs-lookup"><span data-stu-id="18cf0-115">Sample code and reference</span></span>

<span data-ttu-id="18cf0-116">다음 샘플에서는 Azure 관리 모듈을 사용하여 일반적인 작업을 처리하며, 사용자 고유의 앱에서 사용할 준비가 된 코드를 갖추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-116">The following samples cover common tasks with the Azure management modules and have code ready to use in your own apps:</span></span>

- [<span data-ttu-id="18cf0-117">가상 머신</span><span class="sxs-lookup"><span data-stu-id="18cf0-117">Virtual machines</span></span>](node-samples-services-compute.md)
- [<span data-ttu-id="18cf0-118">웹앱</span><span class="sxs-lookup"><span data-stu-id="18cf0-118">Web apps</span></span>](node-samples-services-web-and-mobile.md)
- [<span data-ttu-id="18cf0-119">SQL Database</span><span class="sxs-lookup"><span data-stu-id="18cf0-119">SQL Database</span></span>](node-samples-services-database.md)
   
<span data-ttu-id="18cf0-120">[참조](https://docs.microsoft.com/javascript/api)는 서비스 및 관리 모듈의 모든 모듈에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-120">A [reference](https://docs.microsoft.com/javascript/api) is available for all modules in both the service and management modules.</span></span> <span data-ttu-id="18cf0-121">새 기능, 주요 변경 내용 및 이전 버전에서의 마이그레이션 지침은 [릴리스 정보](https://github.com/Azure/azure-sdk-for-node/releases)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18cf0-121">New features, breaking changes, and migration instructions from previous versions are available in the [release notes](https://github.com/Azure/azure-sdk-for-node/releases).</span></span>