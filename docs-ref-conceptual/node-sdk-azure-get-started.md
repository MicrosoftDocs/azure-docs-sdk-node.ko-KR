---
title: "Node.js용 Azure 모듈 시작"
description: "Node.js용 Azure 모듈을 사용하여 인증 및 리소스 관리 시작"
author: craigshoemaker
manager: routlaw
ms.author: cshoe
ms.date: 06/17/2017
ms.topic: get-started-article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 4c001fce93ef4b83f9e790b4b9374690c3ac04ef
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2018
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="413e4-103">Node.js용 Azure 모듈 시작</span><span class="sxs-lookup"><span data-stu-id="413e4-103">Get started with the Azure modules for Node.js</span></span>

<span data-ttu-id="413e4-104">이 가이드에서는 Azure Node.js 모듈을 설치하고, 서비스 사용자로 Azure에 인증하고, Azure 구독에 리소스를 만들어 Azure 클라우드 서비스에 연결하는 샘플 코드를 실행하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-104">This guide walks you through installing Azure Node.js modules, authenticating to Azure with a service principal, and running sample code that creates resources in your Azure subscription and connects to Azure cloud services.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="413e4-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="413e4-105">Prerequisites</span></span>

- <span data-ttu-id="413e4-106">Azure 계정.</span><span class="sxs-lookup"><span data-stu-id="413e4-106">An Azure account.</span></span> <span data-ttu-id="413e4-107">계정이 없으면 [체험 계정을 얻습니다](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="413e4-107">If you don't have one , [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="413e4-108">Node.js</span><span class="sxs-lookup"><span data-stu-id="413e4-108">Node.js</span></span>](https://nodejs.org)
- <span data-ttu-id="413e4-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) 또는 [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)</span><span class="sxs-lookup"><span data-stu-id="413e4-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) or [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="413e4-110">환경 준비</span><span class="sxs-lookup"><span data-stu-id="413e4-110">Prepare your environment</span></span>

<span data-ttu-id="413e4-111">빈 디렉터리에 새 프로젝트를 만들고 다음 npm 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-111">Create a new project in an empty directory and install the following npm modules:</span></span>

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a><span data-ttu-id="413e4-112">인증 설정</span><span class="sxs-lookup"><span data-stu-id="413e4-112">Set up authentication</span></span>

<span data-ttu-id="413e4-113">이 가이드에서 샘플 코드를 실행하려면 Azure 구독에 대한 읽기 및 만들기 권한이 Node.js 응용 프로그램에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-113">Your Node.js applications need read and create permissions in your Azure subscription to run the sample code in this guide.</span></span> <span data-ttu-id="413e4-114">서비스 사용자를 만들고 해당 자격 증명을 사용하여 실행되도록 응용 프로그램을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-114">Create a service principal and configure your application to run with its credentials.</span></span> <span data-ttu-id="413e4-115">서비스 사용자는 앱에서 실행하는 데 필요한 권한만 부여하는 ID와 연결되는 비대화형 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-115">Service principals are a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="413e4-116">[Azure CLI 2.0을 사용하여 서비스 사용자를 만들고](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) 출력을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-116">[Create a service principal using the Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) and capture the output.</span></span> <span data-ttu-id="413e4-117">암호 인수에 `MY_SECURE_PASSWORD` 대신 [보안 암호](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy)를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-117">You'll need to provide a [secure password](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) in the password argument instead of `MY_SECURE_PASSWORD`.</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name AzureNodeTest --password MY_SECURE_PASSWORD
```

```json
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "AzureNodeTest",
  "name": "http://AzureNodeTest",
  "password": password,
  "tenant": ""
}
```

<span data-ttu-id="413e4-118">*appId*, *password* 및 *tenant* 값을 환경 변수로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-118">Export the values for *appId*, *password* and *tenant* as environment variables:</span></span>

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="413e4-119">[az account show](https://docs.microsoft.com/cli/azure/account#show)를 사용하여 구독 ID를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-119">Get the ID for your subscription with [az account show](https://docs.microsoft.com/cli/azure/account#show)</span></span>

```azurecli-interactive
az account show
```

```json
{
   "environmentName": "AzureCloud",
   "id": "306943934-0323-4ae4d-a42b-f6613d1664ac",
   "isDefault": true
}
```

<span data-ttu-id="413e4-120">구독 ID를 환경 변수로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-120">Export the subscription ID as an environment variable</span></span>

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="413e4-121">Linux 가상 머신 만들기</span><span class="sxs-lookup"><span data-stu-id="413e4-121">Create a Linux virtual machine</span></span>

<span data-ttu-id="413e4-122">다음 코드를 사용하여 현재 디렉터리에 *createVM.js* 파일을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-122">Create a new file *createVM.js* in the current directory with the following code.</span></span> <span data-ttu-id="413e4-123">`adminPass`의 값을 유효한 암호로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-123">Update the value of `adminPass` with a good password.</span></span>

```javascript
'use strict';

const MsRest = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');
const NetworkManagementClient = require('azure-arm-network');

MsRest.loginWithServicePrincipalSecret(
    process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {

        let adminPass = YOUR_VALUE_HERE;
        const networkClient = new NetworkManagementClient(credentials, process.env.AZURE_SUB);
        const computeClient = new ComputeManagementClient(credentials, process.env.AZURE_SUB);

        let nicParameters = {
            location: "eastus",
            ipConfigurations: [
                {
                    name: "vmnetinterface",
                    privateIPAllocationMethod: 'Dynamic',
                }
            ]
        };

        const vnetParameters = {
            location: "eastus",
            addressSpace: {
                addressPrefixes: ['10.0.0.0/16']
            },
            dhcpOptions: {
                dnsServers: ['10.1.1.1', '10.1.2.4']
            },
            subnets: [{ name: "mynodesubnet", addressPrefix: '10.0.0.0/24' }],
        };

        let vmParameters = {
            location: "eastus",
            osProfile: {
                computerName: "newLinuxVM",
                adminUsername: "testadmin",
                adminPassword: admin_password
            },
            hardwareProfile: {
                vmSize: 'Basic_A1'
            },
            networkProfile: {
                networkInterfaces: [
                    {
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

        let publicIPParameters = {
            location: "eastus",
            publicIPAllocationMethod: 'Dynamic'
        };

        networkClient.virtualNetworks.createOrUpdate("myResourceGroup", "mynodevnet", vnetParameters)
            .then(function (vnetwork) {
                networkClient.subnets.get("myResourceGroup", "mynodevnet", "mynodesubnet")
                    .then(function (subnetInfo) {
                        nicParameters.ipConfigurations[0].subnet = subnetInfo;
                        networkClient.publicIPAddresses.createOrUpdate("myResourceGroup", "myLinuxPublicIP", publicIPParameters)
                            .then(function (publicIP) {
                                nicParameters.ipConfigurations[0].publicIPAddress = publicIP;
                                networkClient.networkInterfaces.createOrUpdate("myResourceGroup", "vmnetinterface", nicParameters)
                                    .then(function (vmNetworkInterface) {
                                        vmParameters.networkProfile.networkInterfaces[0].id = vmNetworkInterface.id;
                                        computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, (err, data) => {
                                            if (err) return console.log(err);
                                            console.log("Created new Linux VM");
                                        });
                                    });
                            });
                    });
            });
    });
```

<span data-ttu-id="413e4-124">명령줄에서 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-124">Run the code from the command line:</span></span>

```bash
node createVM.js
```

<span data-ttu-id="413e4-125">코드가 완료되면 새 가상 머신의 IP를 가져오고 코드에서 `adminPass` 값을 사용하여 SSH로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-125">Once the code completes, get the IP of your new virtual machine and log in with SSH using the value for `adminPass` from your code.</span></span>

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a><span data-ttu-id="413e4-126">Azure Storage에 Blob 쓰기</span><span class="sxs-lookup"><span data-stu-id="413e4-126">Write a blob to Azure Storage</span></span>

<span data-ttu-id="413e4-127">다음 코드를 사용하여 현재 디렉터리에 *uploadFile.js* 파일을 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-127">Create a new file *uploadFile.js* in the current directory with the following code.</span></span>

```javascript
'use strict'

const MsRest = require('ms-rest-azure');
const storage = require('azure-storage');
const storageManagementClient = require('azure-arm-storage');

MsRest.loginWithServicePrincipalSecret(process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {
    const client = new storageManagementClient(credentials, process.env.AZURE_SUB);

    const createParameters = {
        location: 'eastus',
        sku: {
            name: 'Standard_LRS'
        },
        kind: 'BlobStorage',
        accessTier: 'Hot'
    };

    const blobAccountName = "nodedemo" + Math.random().toString(10).substr(4, 7);

    client.storageAccounts.create("myResourceGroup", blobAccountName, createParameters, (err, result, httpRequest, response) => {
        if (err) console.log(err);

        // get a connection string for the account
        client.storageAccounts.listKeys("myResourceGroup", blobAccountName, (err, result) => {
            if (err) console.log(err);

            // get a storage key and use it to connect to the azure-storage module
            const blobSvc = storage.createBlobService(blobAccountName, result.keys[0].value);
            blobSvc.createContainerIfNotExists('mycontainer', { publicAccessLevel: 'blob' }, function (error, result, response) {
                if (!error) {
                    blobSvc.createBlockBlobFromText('mycontainer', 'myblob', 'Hello Azure!', function (error, result, response) {
                        if (!error) {
                            console.log("File uploaded to " + "https://" + blobAccountName + ".blob.core.windows.net/mycontainer/myblob");
                        }
                    });
                }
            });

        });
    });
});
```

<span data-ttu-id="413e4-128">명령을 실행한 다음, 출력에서 URL을 복사하여 웹 브라우저에 붙여넣어 Azure Storage에서 파일을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-128">Run the command and then copy and paste the URL from the output into your web browser to view the file in Azure Storage:</span></span>

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a><span data-ttu-id="413e4-129">리소스 정리</span><span class="sxs-lookup"><span data-stu-id="413e4-129">Clean up resources</span></span>

<span data-ttu-id="413e4-130">리소스 그룹을 삭제하여 이 가이드에서 만든 리소스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-130">Delete the resource group to remove the resources created in this guide.</span></span>

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a><span data-ttu-id="413e4-131">다음 단계</span><span class="sxs-lookup"><span data-stu-id="413e4-131">Next steps</span></span>

<span data-ttu-id="413e4-132">앱에서 사용할 수 있는 [Node.js 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=nodejs)를 추가로 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-132">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>

## <a name="reference"></a><span data-ttu-id="413e4-133">참고 자료</span><span class="sxs-lookup"><span data-stu-id="413e4-133">Reference</span></span> 

<span data-ttu-id="413e4-134">[참조](/javascript/api/overview/azure/)는 모든 패키지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-134">A [reference](/javascript/api/overview/azure/) is available for all packages.</span></span>

## <a name="get-help-and-give-feedback"></a><span data-ttu-id="413e4-135">도움말 가져오기 및 피드백 제공</span><span class="sxs-lookup"><span data-stu-id="413e4-135">Get help and give feedback</span></span>

<span data-ttu-id="413e4-136">[Stack Overflow(영문)](https://stackoverflow.com/questions/tagged/azure+node.js)의 커뮤니티에 질문을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-136">Post questions to the community on [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span></span> <span data-ttu-id="413e4-137">[GitHub 프로젝트](https://github.com/Azure/azure-sdk-for-node)에서 Node.js용 Azure 모듈에 대한 버그 및 열기 문제를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="413e4-137">Report bugs and open issues against the Azure modules for Node.js on the [project GitHub](https://github.com/Azure/azure-sdk-for-node).</span></span>

