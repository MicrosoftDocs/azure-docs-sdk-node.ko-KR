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
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50339921"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a>Node.js용 Azure Event Grid 라이브러리

Azure Event Grid에서 간단한 HTTP 기반 이벤트 처리를 사용하여 Azure 서비스 및 사용자 지정 원본의 이벤트에 대해 수신 대기하고 대응하는 이벤트 기반 응용 프로그램을 작성합니다.

Azure Event Grid에 대해 [자세히 알아보고](/azure/event-grid/overview), [Azure Blob 저장소 이벤트 자습서](/azure/storage/blobs/storage-blob-event-quickstart)를 시작합니다. 

## <a name="publish-sdk"></a>SDK 게시

Azure Event Grid 게시 SDK를 사용하여 이벤트를 만들고, 인증하고, 토픽에 게시합니다.

### <a name="installation"></a>설치

npm을 사용하여 모듈을 프로젝트에 추가합니다.

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a>예제 코드

다음 코드 세그먼트는 모의 이벤트를 Event Grid 항목에 게시합니다. Azure Portal에서 또는 Azure CLI를 통해 엔드포인트 및 토픽 액세스 키를 검색할 수 있습니다.

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

이 샘플은 Azure Storage에서 이벤트를 처리하는 방법을 보여줍니다.

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
> [클라이언트 API 탐색](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a>관리 SDK

관리 SDK를 사용하여 Event Grid 인스턴스, 토픽 및 구독을 만들거나 업데이트하거나 삭제합니다.

### <a name="installation"></a>설치

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a>예제 코드

다음 코드는 Event Grid 토픽 `topic1`을 만들고 새로 만든 토픽과 연결된 액세스 키를 반환합니다.

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
> [관리 API 탐색](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a>자세한 정보

- [Event Grid SDK를 사용하여 이벤트 수신](/azure/event-grid/receive-events)
