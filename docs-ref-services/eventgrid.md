---
title: Node.js용 Azure Event Grid 라이브러리
description: Node.js용 Azure Event Grid 라이브러리에 대한 참조
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: ''
ms.technology: ''
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: bddf4efc1eda186aee92d30af24125823c7a8f7b
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47347142"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a><span data-ttu-id="fd4e4-103">Node.js용 Azure Event Grid 라이브러리</span><span class="sxs-lookup"><span data-stu-id="fd4e4-103">Azure Event Grid libraries for Node.js</span></span>

<span data-ttu-id="fd4e4-104">Azure Event Grid에서 간단한 HTTP 기반 이벤트 처리를 사용하여 Azure 서비스 및 사용자 지정 원본의 이벤트에 대해 수신 대기하고 대응하는 이벤트 기반 응용 프로그램을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="fd4e4-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="fd4e4-105">Azure Event Grid에 대해 [자세히 알아보고](/azure/event-grid/overview), [Azure Blob 저장소 이벤트 자습서](/azure/storage/blobs/storage-blob-event-quickstart)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fd4e4-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="fd4e4-106">SDK 게시</span><span class="sxs-lookup"><span data-stu-id="fd4e4-106">Publish SDK</span></span>

<span data-ttu-id="fd4e4-107">Azure Event Grid 게시 SDK를 사용하여 이벤트를 만들고, 인증하고, 토픽에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="fd4e4-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="fd4e4-108">설치</span><span class="sxs-lookup"><span data-stu-id="fd4e4-108">Installation</span></span>

<span data-ttu-id="fd4e4-109">npm을 사용하여 모듈을 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fd4e4-109">Add the module to your project with npm:</span></span>

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="fd4e4-110">예제 코드</span><span class="sxs-lookup"><span data-stu-id="fd4e4-110">Example code</span></span>

<span data-ttu-id="fd4e4-111">다음 코드 세그먼트는 모의 이벤트를 Event Grid 항목에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="fd4e4-111">The following code segment publishes a mock event to a Event Grid topic.</span></span> <span data-ttu-id="fd4e4-112">Azure Portal에서 또는 Azure CLI를 통해 엔드포인트 및 토픽 액세스 키를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd4e4-112">You can retrieve the endpoint and topic access keys from the Azure Portal or through the Azure CLI:</span></span>

```azurecli-interactive
endpoint=$(az eventgrid topic show --name <topic_name> -g gridResourceGroup --query "endpoint" --output tsv)
key=$(az eventgrid topic key list --name <topic_name> -g gridResourceGroup --query "key1" --output tsv)
```

```javascript
var EventGridClient = require("azure-eventgrid");
var msRestAzure = require('ms-rest-azure');
var uuid = require('uuid').v4;

let topicCreds = new msRestAzure.TopicCredentials('your-topic-key');
let EGClient = new EventGridClient(topicCreds, 'your-subscription-id');
let topicHostName = 'your-topic-endpoint';
let events = [
   {
   id: uuid(),
   subject: 'TestSubject',
   dataVersion: '1.0',
   eventType: 'Microsoft.MockPublisher.TestEvent',
   data: {
        field1: 'value1',
        filed2: 'value2'
        }
    }
];
return EGClient.publishEvents(topicHostName, events).then((result) => {
   return Promise.resolve(console.log('Published events successfully.'));
 }).catch((err) => {
  console.log('An error ocurred');
  console.dir(err, {depth: null, colors: true});
});
```

<span data-ttu-id="fd4e4-113">이 샘플은 Azure Storage에서 이벤트를 처리하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="fd4e4-113">This sample shows how to handle an event from Azure Storage:</span></span>

```javascript
var http = require('http');

module.exports = function (context, req) {
    context.log('JavaScript HTTP trigger function begun');
    var validationEventType = "Microsoft.EventGrid.SubscriptionValidationEvent";
    var storageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

    for (var events in req.body) {
        var body = req.body[events];
        // Deserialize the event data into the appropriate type based on event type  
        if (body.data && body.eventType == validationEventType) {
            context.log("Got SubscriptionValidation event data, validation code: " + body.data.validationCode + " topic: " + body.topic);

            // Do any additional validation (as required) and then return back the below response
            var code = body.data.validationCode;
            context.res = { status: 200, body: { "ValidationResponse": code } };
        }

        else if (body.data && body.eventType == storageBlobCreatedEvent) {
            var blobCreatedEventData = body.data;
            context.log("Relaying received blob created event payload:" + JSON.stringify(blobCreatedEventData));
        }
    }
    context.done();
};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd4e4-114">클라이언트 API 탐색</span><span class="sxs-lookup"><span data-stu-id="fd4e4-114">Explore the client APIs</span></span>](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="fd4e4-115">관리 SDK</span><span class="sxs-lookup"><span data-stu-id="fd4e4-115">Management SDK</span></span>

<span data-ttu-id="fd4e4-116">관리 SDK를 사용하여 Event Grid 인스턴스, 토픽 및 구독을 만들거나 업데이트하거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="fd4e4-116">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="fd4e4-117">설치</span><span class="sxs-lookup"><span data-stu-id="fd4e4-117">Installation</span></span>

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="fd4e4-118">예제 코드</span><span class="sxs-lookup"><span data-stu-id="fd4e4-118">Example code</span></span>

<span data-ttu-id="fd4e4-119">다음 코드는 Event Grid 토픽 `topic1`을 만들고 새로 만든 토픽과 연결된 액세스 키를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fd4e4-119">The following code creates an Event Grid topic `topic1` and returns the access keys associated with the newly created topic.</span></span>

```javascript
var msRestAzure = require('ms-rest-azure');
var EventGridManagementClient = require("azure-arm-eventgrid");

msRestAzure.interactiveLogin(function(err, credentials) {
    // Created the management client
    let EGMClient = new EventGridManagementClient(credentials, 'your-subscription-id');
    let topicResponse;
    // created an enventgrid topic
    return EGMClient.topics.createOrUpdate('resourceGroup', 'topic1', { location: 'westus' }).then((topicResponse) => {
        return Promise.resolve(console.log('Created topic ', topicResponse));
    }).then(() => {
        // listed the access keys
        return EGMClient.topics.listSharedAccessKeys('resourceGroup', 'topic1')}
)};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd4e4-120">관리 API 탐색</span><span class="sxs-lookup"><span data-stu-id="fd4e4-120">Explore the management APIs</span></span>](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="fd4e4-121">자세한 정보</span><span class="sxs-lookup"><span data-stu-id="fd4e4-121">Learn more</span></span>

- [<span data-ttu-id="fd4e4-122">Event Grid SDK를 사용하여 이벤트 수신</span><span class="sxs-lookup"><span data-stu-id="fd4e4-122">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)
