---
title: Node.js를 통한 Azure 메시지 및 IoT 샘플 코드
description: Node.js를 통해 Azure 메시지 및 IoT를 사용하는 방법을 보여주는 샘플 코드
author: rloutlaw
manager: routlaw
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: routlaw
ms.openlocfilehash: 3169c3ef0d204e902db47d81ba02b638a5eb02f5
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220685"
---
# <a name="sample-code-for-using-azure-messaging-and-iot-with-nodejs"></a><span data-ttu-id="76314-103">Node.js를 통해 Azure 메시지 및 IoT를 사용하는 샘플 코드</span><span class="sxs-lookup"><span data-stu-id="76314-103">Sample code for using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="76314-104">다음 샘플 코드에서는Node.js를 통해 Azure 메시지 및 IoT를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="76314-104">The following sample code illustrates using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="76314-105">다른 작업에 대한 코드가 필요하면 [Azure Node.js 샘플 ](https://azure.microsoft.com/resources/samples/?term=nodejs)의 전체 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76314-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="76314-106">**Azure IoT Hub**</span><span class="sxs-lookup"><span data-stu-id="76314-106">**Azure IoT Hub**</span></span> ||
| [<span data-ttu-id="76314-107">Azure IoT Hub ping(영문)</span><span class="sxs-lookup"><span data-stu-id="76314-107">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping) | <span data-ttu-id="76314-108">Azure IoT Hub에 대한 장치 연결을 확인하는 데 도움이 되는 간단한 ping 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="76314-108">Simple ping solution to help validate a device connectivity to Azure IoT Hub.</span></span> |
| [<span data-ttu-id="76314-109">Node.js를 실행하는 Intel Edison의 데이터에서 Azure IoT 서비스로 검색된 진동 이상 트윗(영문)</span><span class="sxs-lookup"><span data-stu-id="76314-109">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) | <span data-ttu-id="76314-110">Azure IoT Hub를 사용하고, 원격 분석 데이터를 보내기 위해 노드를 실행하는 장치를 표시하고, Azure IoT 서비스에서 분석하는 IoT 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="76314-110">IoT project using Azure IoT Hub and showing a device running node to send telemetry data and that is analyzed by Azure IoT services.</span></span> |
| <span data-ttu-id="76314-111">**Intel Edison IoT**</span><span class="sxs-lookup"><span data-stu-id="76314-111">**Intel Edison IoT**</span></span> ||
| [<span data-ttu-id="76314-112">Intel Edison Azure IoT 시작 키트 시작(영문)</span><span class="sxs-lookup"><span data-stu-id="76314-112">Get started with Intel Edison Azure IoT Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit) | <span data-ttu-id="76314-113">Azure IoT 시작 키트(Intel Edison)를 사용하여 Azure IoT를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="76314-113">Demonstrates Azure IoT using the Azure IoT Starter Kit - Intel Edison.</span></span> |
| <span data-ttu-id="76314-114">**MQTT**</span><span class="sxs-lookup"><span data-stu-id="76314-114">**MQTT**</span></span> ||
| [<span data-ttu-id="76314-115">MQTT 및 HTTP 게이트웨이 샘플 모듈(영문)</span><span class="sxs-lookup"><span data-stu-id="76314-115">Sample MQTT and HTTP Gateway modules</span></span>](https://github.com/Azure-Samples/iot-gateway-mqtt-http) | <span data-ttu-id="76314-116">원격 분석 업로드를 위한 IoT Hub 방식의 MQTT 및 HTTPS 끝점을 공개하는 두 개의 게이트웨이 모듈을 제공하며, MQTT 모듈의 경우 C2D 메시지도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="76314-116">Provides two Gateway modules that expose IoTHub-style MQTT and HTTPS endpoints for telemetry upload, and in the case of MQTT module also C2D messaging.</span></span> |
| <span data-ttu-id="76314-117">**Raspberry Pi**</span><span class="sxs-lookup"><span data-stu-id="76314-117">**Raspberry Pi**</span></span> ||
| [<span data-ttu-id="76314-118">Microsoft Azure IoT Raspberry Pi 시작 키트 시작(영문)</span><span class="sxs-lookup"><span data-stu-id="76314-118">Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started) | <span data-ttu-id="76314-119">Azure IoT Raspberry Pi 시작 키트를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="76314-119">Illustrates using the Azure IoT Raspberry Pi Starter Kit.</span></span> |
| [<span data-ttu-id="76314-120">Microsoft Azure IoT Raspberry Pi 3 시작 키트를 원격 모니터링 솔루션에 연결(영문)</span><span class="sxs-lookup"><span data-stu-id="76314-120">Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) | <span data-ttu-id="76314-121">Azure IoT Suite 원격 모니터링 솔루션에 Raspberry Pi 3 장치를 연결하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="76314-121">Learn how to connect a Raspberry Pi 3 device to the Azure IoT Suite remote monitoring solution.</span></span> |
