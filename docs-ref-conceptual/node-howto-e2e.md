---
title: Visual Studio Code 및 Azure를 사용하여 Node.js 개발
description: Azure에 Node.js 앱을 만들고, Docker화하고, 배포하는 방법을 보여 주는 완벽한 종단 간 자습서입니다.
services: multiple
author: tomarcher
manager: douge
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 06/25/2017
ms.author: joncart
ms.openlocfilehash: 1b43502394b7224c5791ee870999cdb958a0969d
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2017
ms.locfileid: "20908143"
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a><span data-ttu-id="025bf-103">Visual Studio Code 및 Azure를 사용하여 Node.js 개발</span><span class="sxs-lookup"><span data-stu-id="025bf-103">Node.js development with Visual Studio Code and Azure</span></span>

<span data-ttu-id="025bf-104">이 자습서에서는 기존 Node.js 앱을 가져와서 "컨테이너화"한(Docker 사용) 다음 Visual Studio Code를 사용하여 Azure에 앱을 배포하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-104">This tutorial illustrates taking an existing Node.js app, "containerizing" it (with Docker), and then deploying the app to Azure using Visual Studio Code.</span></span>

<span data-ttu-id="025bf-105">이 자습서에서는 [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular)를 통해 만들고 게시하는 간단한 할 일 앱을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-105">The tutorial makes use of a simple todo app created by and published by [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span></span> <span data-ttu-id="025bf-106">단일 페이지 MEAN 앱이므로 MongoDB를 데이터베이스로 사용하고, REST API/웹 서버의 경우 Node/Express를 사용하고, 프런트 엔드 UI의 경우 Angular.js 1.x를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-106">It is a single-page MEAN app, and therefore, uses MongoDB as its database, Node/Express for the REST API/web server, and Angular.js 1.x for the front-end UI.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="025bf-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="025bf-107">Prerequisites</span></span>

<span data-ttu-id="025bf-108">데모와 함께 수행하려면 다음 소프트웨어가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-108">In order to follow along with the demo, you'll need to have the following software installed:</span></span>

- [<span data-ttu-id="025bf-109">Contact.java</span><span class="sxs-lookup"><span data-stu-id="025bf-109">Visual Studio Code</span></span>](https://code.visualstudio.com/)
- [<span data-ttu-id="025bf-110">Docker</span><span class="sxs-lookup"><span data-stu-id="025bf-110">Docker</span></span>](https://www.docker.com/products/docker)
- [<span data-ttu-id="025bf-111">Docker Hub 계정</span><span class="sxs-lookup"><span data-stu-id="025bf-111">DockerHub account</span></span>](https://hub.docker.com/)
- [<span data-ttu-id="025bf-112">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="025bf-112">Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [<span data-ttu-id="025bf-113">Azure 계정</span><span class="sxs-lookup"><span data-stu-id="025bf-113">Azure account</span></span>](https://azure.microsoft.com/free/)
- [<span data-ttu-id="025bf-114">Yarn</span><span class="sxs-lookup"><span data-stu-id="025bf-114">Yarn</span></span>](https://yarnpkg.com/en/docs/install)
- <span data-ttu-id="025bf-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - 데모 앱의 프런트 엔드 디버깅에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Used for debugging the demo app's front-end.</span></span>
- <span data-ttu-id="025bf-116">MongoDB - 데모 앱에서 MongoDB를 사용하므로 표준 `27017` 포트에서 수신 대기 중인 MongoDB 인스턴스가 로컬로 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-116">MongoDB - Since the demo app uses MongoDB, you need to have a locally running MongoDB instance that is listening on the standard `27017` port.</span></span> <span data-ttu-id="025bf-117">이 작업을 수행하는 가장 간단한 방법은 Docker를 설치한 후에 `docker pull mongo` 명령에 이어 `docker run -it -p 27017:27017 mongo` 명령을 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-117">The simplest way to achieve this is by running the following two commands after Docker is installed: `docker pull mongo` followed by `docker run -it -p 27017:27017 mongo`.</span></span>

## <a name="project-setup"></a><span data-ttu-id="025bf-118">프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="025bf-118">Project setup</span></span>

<span data-ttu-id="025bf-119">시작하려면 다음 단계를 사용하여 샘플 프로젝트를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-119">To get started, download the sample project using the following steps:</span></span>

1. <span data-ttu-id="025bf-120">Visual Studio Code를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-120">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="025bf-121">**&lt;F1>** 키를 눌러 명령 팔레트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-121">Press **&lt;F1>** to display the command palette.</span></span>

1. <span data-ttu-id="025bf-122">명령 팔레트 프롬프트에서 `gitcl`을 입력하고, **Git: Clone**(Git: 복제) 명령을 선택하고, **&lt;Enter>** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-122">At the command palette prompt, enter `gitcl`, select the **Git: Clone** command, and press **&lt;Enter>**.</span></span>

    ![Visual Studio Code 명령 팔레트 프롬프트의 gitcl 명령](./media/node-howto-e2e/git-clone.png)

1. <span data-ttu-id="025bf-124">**리포지토리 URL**에 대한 프롬프트가 표시되면 `https://github.com/scotch-io/node-todo`를 입력하고 **&lt;Enter>** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-124">When prompted for the **Repository URL**, enter `https://github.com/scotch-io/node-todo`, then press **&lt;Enter>**.</span></span>

1. <span data-ttu-id="025bf-125">프로젝트를 복제할 로컬 디렉터리를 선택하거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-125">Select (or create) the local directory into which you want to clone the project.</span></span>

    ![Visual Studio Code 탐색기](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a><span data-ttu-id="025bf-127">통합 터미널</span><span class="sxs-lookup"><span data-stu-id="025bf-127">Integrated terminal</span></span>

<span data-ttu-id="025bf-128">Node.js 프로젝트이므로 가장 먼저 해야 할 작업은 프로젝트의 모든 종속성이 npm에서 설치되었는지 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-128">Since this is a Node.js project, the first thing you need to do is ensure that all of the project's dependencies are installed from npm.</span></span>  

1. <span data-ttu-id="025bf-129">**&lt;Ctrl>** 키를 눌러 Visual Studio Code 통합 터미널을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-129">Press **&lt;Ctrl>\`** to display the Visual Studio Code integrated terminal.</span></span> 

1. <span data-ttu-id="025bf-130">`yarn`을 입력하고 **&lt;Enter>** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-130">Enter `yarn`, and press **&lt;Enter>**.</span></span>  

    ![Visual Studio Code 내에서 yarn 명령 실행](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a><span data-ttu-id="025bf-132">통합된 Git 버전 제어</span><span class="sxs-lookup"><span data-stu-id="025bf-132">Integrated Git version control</span></span>

<span data-ttu-id="025bf-133">Yarn을 통해 앱의 종속성을 설치한 후 나중에 조금도 놀라지 않고 CI(연속 통합) 빌드, 프로덕션 배포 또는 다른 개발자 컴퓨터 중 하나에서 똑같은 종속성을 다시 가져오는 예측 가능한 방법을 제공하는 `yarn.lock` 파일이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-133">After installing the app's dependencies via Yarn, a `yarn.lock` file is created that provides a predictable way to reacquire the exact same dependencies in the future, without any surprises in either CI (continuous integration) builds, production deployments, or other developer machines.</span></span>

<span data-ttu-id="025bf-134">다음 단계에서는 `yarn.lock` 파일을 소스 제어에 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-134">The following steps illustrate how to check the `yarn.lock` file into source control:</span></span>

1. <span data-ttu-id="025bf-135">Visual Studio Code 내에서 통합된 Git 탭(Git 로고가 있는 탭)으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-135">Within Visual Studio Code, switch to the integrated Git tab (the tab with the Git logo).</span></span>

1. <span data-ttu-id="025bf-136">**메시지** 상자에서 커밋 메시지를 입력하고 **&lt;Ctrl>&lt;Enter>** 를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-136">In the **Message** box, enter a commit message, and press **&lt;Ctrl>&lt;Enter>**.</span></span> 

    ![Git에 yarn.lock 파일 추가](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a><span data-ttu-id="025bf-138">프로젝트 및 코드 탐색</span><span class="sxs-lookup"><span data-stu-id="025bf-138">Project and code navigation</span></span>

<span data-ttu-id="025bf-139">코드베이스 내에서 방향을 직접 설정하기 위해 Visual Studio Code에서 제공하는 몇 가지 탐색 기능의 예제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-139">In order to orient ourselves within the codebase, let's play around with some examples of some of the navigation capabilities that Visual Studio Code provides.</span></span>

1. <span data-ttu-id="025bf-140">**&lt;Ctrl>P**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-140">Press **&lt;Ctrl>P**.</span></span>

1. <span data-ttu-id="025bf-141">`.js`를 입력하여 프로젝트의 모든 JavaScript/JSON 파일을 각 파일의 부모 디렉터리와 함께 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-141">Enter `.js` to display all the JavaScript/JSON files in the project along with each file's parent directory</span></span> 

    ![모든 .js\* 파일 표시](./media/node-howto-e2e/git-output.png)

1. <span data-ttu-id="025bf-143">앱에 대한 시작 스크립트인 `server.js`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-143">Select `server.js`, which is the startup script for the app.</span></span> 

1. <span data-ttu-id="025bf-144">마우스로 **database**(6번 줄에서 가져옴) 변수 위를 가리켜서 해당 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-144">Hover your mouse over the **database** variable (imported on line 6) to see its type.</span></span> <span data-ttu-id="025bf-145">파일 내의 변수/모듈/형식을 빠르게 검사하는 이 기능은 프로젝트를 개발하는 동안 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-145">This ability to quickly inspect variables/modules/types within a file is very useful during the development of your projects.</span></span> 

    ![검색 유형](./media/node-howto-e2e/hover-help.png)

1. <span data-ttu-id="025bf-147">**database**와 같은 변수 범위 내에서 마우스를 클릭하면 동일한 파일 내에서 해당 변수에 대한 모든 참조를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-147">Clicking your mouse within the span of a variable - such as **database** - allows you to see all references to that variable within the same file.</span></span> <span data-ttu-id="025bf-148">프로젝트 내에서 변수에 대한 모든 참조를 보려면 마우스 오른쪽 단추로 해당 변수를 클릭하고 컨텍스트 메뉴에서 **모든 참조 찾기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-148">To view all references to a variable within the project, right-click the variable, and from the context menu, and select **Find All References**.</span></span>

    ![변수에 대한 참조 찾기](./media/node-howto-e2e/word-hilight.png)

1. <span data-ttu-id="025bf-150">마우스로 변수 위를 가리켜서 형식을 검색하는 것 외에도 다른 파일에 있는 변수의 정의를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-150">In addition to being to hover your mouse over a variable to discover its type, you can also inspect the definition of a variable, even if it's in another file.</span></span> <span data-ttu-id="025bf-151">이 기능이 활성 중인지 확인하려면 마우스 오른쪽 단추로 **database.localUrl**(12번 줄)을 클릭하고 컨텍스트 메뉴에서 **정의 피킹**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-151">To see this in action, right-click **database.localUrl** (line 12), and, from the context menu, select **Peek Definition**.</span></span> 

    ![변수 정의 피킹](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a><span data-ttu-id="025bf-153">코드 수정 및 자동 완성 사용</span><span class="sxs-lookup"><span data-stu-id="025bf-153">Modifying the code and using autocompletion</span></span>

<span data-ttu-id="025bf-154">MongoDB 연결 문자열은 **database.localUrl** 선언에 하드 코드됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-154">The MongoDB connection string is hard-coded in declaration of the **database.localUrl**.</span></span> <span data-ttu-id="025bf-155">이 섹션에서는 코드를 수정하여 환경 변수에서 연결 문자열을 검색하고 Visual Studio Code의 자동 완성 기능에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-155">In this section, you'll modify the code to retrieve the connection string from an environment variable, and learn about Visual Studio Code's autocompetion feature.</span></span>  

1. <span data-ttu-id="025bf-156">`server.js` 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-156">Open the `server.js` file</span></span>

1. <span data-ttu-id="025bf-157">다음 코드를</span><span class="sxs-lookup"><span data-stu-id="025bf-157">Replace the following code:</span></span> 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    <span data-ttu-id="025bf-158">이 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-158">with this code:</span></span>

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

<span data-ttu-id="025bf-159">복사 및 붙여넣기 대신 수동으로 코드를 입력할 때 `process` 뒤에 마침표를 입력하면 Visual Studio Code에서 **process** 전역 Node.js API의 사용 가능한 멤버가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-159">Note that if you type the code in manually (instead of copy and paste), when you type the period after `process`, Visual Studio Code displays the available members of the Node.js **process** global API.</span></span>

![API 멤버를 자동으로 표시하는 자동 완성](./media/node-howto-e2e/process-env.png)

<span data-ttu-id="025bf-161">Visual Studio Code가 백그라운드에서(심지어 JavaScript의 경우에도) TypeScript를 사용하여 입력함에 따라 완성 목록에 알리는 데 사용할 수 있는 형식 정보를 제공하기 때문에 자동 완성이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-161">Autocompetion works because Visual Studio Code uses TypeScript behind the scenes - even for JavaScript - to provide type information that can then be used to inform the completion list as you type.</span></span> <span data-ttu-id="025bf-162">Visual Studio Code에서는 이 작업이 Node.js 프로젝트임을 감지할 수 있으며, 이에 따라 [NPM에서 Node.js](https://www.npmjs.com/package/@types/node)에 대한 TypeScript 입력 항목 파일을 자동으로 다운로드했습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-162">Visual Studio Code is able to detect that this is a Node.js project, and as a result, automatically downloaded the TypeScript typings file for [Node.js from NPM](https://www.npmjs.com/package/@types/node).</span></span> <span data-ttu-id="025bf-163">입력 항목 파일을 사용하면 **fs** 및 **http**와 같은 모든 기본 제공 모듈뿐만 아니라 **Buffer** 및 **setTimeout**와 같은 다른 Node.js 전역 모듈에 대한 자동 완성도 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-163">The typings file allows you to get autocompletion for other Node.js globals - such as **Buffer** and **setTimeout** - as well as all of the built-in modules such as **fs** and **http**.</span></span>

<span data-ttu-id="025bf-164">기본 제공 Node.js API 외에도 입력 항목의 자동 취득은 2,000개 이상의 타사 모듈(예: React, Underscore 및 Express)에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-164">In addition to the built-in Node.js APIs, this auto-acquisition of typings also works for over 2,000 3rd party modules, such as React, Underscore and Express.</span></span> <span data-ttu-id="025bf-165">예를 들어 Mongoose에서 구성된 MongoDB 데이터베이스 인스턴스에 연결할 수 없는 경우 Mongoose에서 정지된 샘플 앱을 해제하려면 13번 줄에 다음 코드 줄을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-165">For example, in order to disable Mongoose from crashing the sample app if it can't connect to the configured MongoDB database instance, insert the following line of code at  line 13:</span></span>

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

<span data-ttu-id="025bf-166">이전 코드와 마찬가지로 사용자가 작업하지 않아도 자동 완성을 가져오는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-166">As with the previous code, you'll notice that you get autocompletion without any work on your part.</span></span>

![API 멤버를 자동으로 표시하는 자동 완성](./media/node-howto-e2e/mongoose.png)

<span data-ttu-id="025bf-168">모든 TypeScript 형식 정의의 커뮤니티 기반 소스인 [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) 프로젝트를 탐색하여 이 자동 완성 기능을 지원하는 모듈을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-168">You can see which modules support this auto-complete capability by browsing the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) project, which is the community-driven source of all TypeScript type definitions.</span></span>

## <a name="running-the-app"></a><span data-ttu-id="025bf-169">앱 실행</span><span class="sxs-lookup"><span data-stu-id="025bf-169">Running the app</span></span>

<span data-ttu-id="025bf-170">코드에 대해 약간 알아보았으면 앱을 실행할 차례입니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-170">Once you've explored the code a bit, it's time to run the app.</span></span> <span data-ttu-id="025bf-171">Visual Studio Code에서 앱을 실행하려면 **&lt;F5>** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-171">To run the app from Visual Studio Code, press **&lt;F5>**.</span></span> <span data-ttu-id="025bf-172">**&lt;F5>**(디버그 모드) 키를 통해 코드를 실행하면 Visual Studio Code에서 앱을 실행하고, 앱의 stdout(표준 출력)을 보여 주는 **디버그 콘솔** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-172">When running the code via **&lt;F5>** (debug mode), Visual Studio Code launches the app and displays the **Debug Console** window that displays stdout for the app.</span></span>

![디버그 콘솔을 통한 앱의 stdout 모니터링](./media/node-howto-e2e/console.png)

<span data-ttu-id="025bf-174">또한 새로 실행 중인 앱에 **디버그 콘솔**이 연결되어 있으므로 JavaScript 식을 입력할 수 있습니다. 이 식은 앱에서 평가되며 자동 완성 기능도 포함하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-174">Additionally, the **Debug Console** is attached to the newly running app so you can type JavaScript expressions, which will be evaluated in the app, and also includes auto-completion.</span></span> <span data-ttu-id="025bf-175">이 기능이 활성 중인지 확인하려면 콘솔에서 `process.env`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-175">To see this in action, type `process.env` in the console:</span></span>

![디버그 콘솔에 입력 항목 코드 추가](./media/node-howto-e2e/console-code.png)

<span data-ttu-id="025bf-177">현재 열려 있는 파일이 JavaScript 파일(`server.js`)이므로 **&lt;F5>** 키를 눌러 앱을 실행할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-177">You were able to press **&lt;F5>** to run the app because the currently open file is a JavaScript file (`server.js`).</span></span> <span data-ttu-id="025bf-178">결과적으로 Visual Studio Code에서는 프로젝트가 Node.js 앱이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-178">As a result, Visual Studio Code assumes that the project is a Node.js app.</span></span> <span data-ttu-id="025bf-179">Visual Studio Code의 모든 JavaScript 파일을 닫은 다음 **&lt;F5>** 키를 누르면 Visual Studio Code에서 사용자를 환경으로 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-179">If you close all JavaScript files in Visual Studio Code, and then press **&lt;F5>**, Visual Studio Code will query you as the environment:</span></span>

![런타임 환경 지정](./media/node-howto-e2e/select-env.png)

<span data-ttu-id="025bf-181">브라우저를 열고 `http://localhost:8080`으로 이동하여 실행 중인 앱을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-181">Open a browser, and navigate to `http://localhost:8080` to see the running app.</span></span> <span data-ttu-id="025bf-182">텍스트 상자에 메시지를 입력하고 몇 가지 할 일을 추가/제거하여 앱이 작동하는 방식에 대해 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-182">Type a message into the textbox and add/remove a few todos to get a feel for how the app works.</span></span>

![할 일 앱 실행](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a><span data-ttu-id="025bf-184">디버그</span><span class="sxs-lookup"><span data-stu-id="025bf-184">Debugging</span></span>

<span data-ttu-id="025bf-185">Visual Studio Code는 통합된 콘솔을 통해 앱을 실행하고 상호 작용할 수 있을 뿐만 아니라 코드 내에서 중단점을 직접 설정할 수 있는 기능도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-185">In addition to being able to run the app and interact with it via the integrated console, Visual Studio Code provides the ability to set breakpoints directly within your code.</span></span> <span data-ttu-id="025bf-186">예를 들어 **&lt;Ctrl>P**를 눌러 파일 선택기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-186">For example, press **&lt;Ctrl>P** to display the file picker.</span></span> <span data-ttu-id="025bf-187">파일 선택기가 표시되면 `route`를 입력하고 `route.js` 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-187">Once the file picker displays, type `route`, and select the `route.js` file.</span></span>

<span data-ttu-id="025bf-188">앱에서 할 일 항목을 추가하려고 할 때 호출되는 Express 경로를 나타내는 중단점을 28번 줄에 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-188">Set a breakpoint on line 28, which represents the Express route that is called when the app tries to add a todo entry.</span></span> <span data-ttu-id="025bf-189">중단점을 설정하려면 다음 그림과 같이 편집기 내에서 줄 번호의 왼쪽 영역을 클릭하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-189">To set a breakpoint, simply click the area to the left of the line number within the editor as shown in the following figure.</span></span>

![Visual Studio Code 내 중단점 설정](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> <span data-ttu-id="025bf-191">Visual Studio Code는 표준 중단점 외에도 앱에서 실행을 일시 중단해야 하는 시점을 사용자 지정할 수 있는 조건부 중단점을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-191">In addition to standard breakpoints, Visual Studio Code supports conditional breakpoints that allow you to customize when the app should suspend execution.</span></span> <span data-ttu-id="025bf-192">조건부 중단점을 설정하려면 마우스 오른쪽 단추로 실행을 일시 중지하려는 줄의 왼쪽 영역을 클릭하고, **조건부 중단점 추가...** 를 선택한 다음, JavaScript 식(예: `foo = "bar"` ) 또는 실행을 일시 중지하려는 조건을 정의하는 실행 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-192">To set a conditional breakpoint, right-click the area to the left of the line on which you wish to pause execution, select **Add Conditional Breakpoint...**, and specify either a JavaScript expression (e.g. `foo = "bar"`) or execution count that defines the condition under which you want to pause execution.</span></span>
> 
> 

<span data-ttu-id="025bf-193">중단점이 설정되면 실행 중인 앱으로 돌아가서 할 일 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-193">Once the breakpoint has been set, return to the running app and add a todo entry.</span></span> <span data-ttu-id="025bf-194">할 일 항목을 추가하는 즉시 중단점을 설정한 28번 줄에서 앱의 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-194">Adding a todo entry immediately causes the app to suspend execution on line 28 where you set the breakpoint:</span></span>

![중단점에서 실행이 일시 중지된 Visual Studio Code](./media/node-howto-e2e/debugger.png)

<span data-ttu-id="025bf-196">응용 프로그램이 일시 중지되면 마우스로 코드 식 위를 가리켜서 현재 값을 볼 수 있고, 지역/조사 식 및 호출 스택을 검사하고, 디버그 도구 모음을 사용하여 코드 실행을 단계별로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-196">Once the application has been paused, you can hover your mouse over the code's expressions to view their current value, inspect the locals/watches and call stack, and use the debug toolbar to step through the code execution.</span></span> <span data-ttu-id="025bf-197">**&lt;F5>** 키를 눌러 앱 실행을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-197">Press **&lt;F5>** to resume execution of the app.</span></span>

## <a name="full-stack-debugging"></a><span data-ttu-id="025bf-198">전체 스택 디버깅</span><span class="sxs-lookup"><span data-stu-id="025bf-198">Full-stack debugging</span></span>

<span data-ttu-id="025bf-199">이 항목의 앞부분에서 설명했듯이 할 일 앱은 MEAN 앱입니다. 즉 프런트 엔드와 백 엔드 코드가 모두 JavaScript를 사용하여 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-199">As mentioned earlier in the topic, the TODO app is a MEAN app - meaning that its front-end and back-end are both written using JavaScript.</span></span> <span data-ttu-id="025bf-200">따라서 현재 백 엔드(Node/Express) 코드를 디버그하고 있지만 어느 시점에서 프런트 엔드(Angular) 코드를 디버그해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-200">So, while you're currently debugging the back-end (Node/Express) code, at some point, you may need to debug the front-end (Angular) code.</span></span> <span data-ttu-id="025bf-201">이러한 목적을 위해 Visual Studio Code는 통합된 Chrome 디버깅을 포함하여 광범위한 확장 에코시스템을 갖추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-201">For that purpose, Visual Studio Code has a huge ecosystem of extensions, including integrated Chrome debugging.</span></span>

<span data-ttu-id="025bf-202">**확장** 탭으로 전환하고 검색 상자에 `chrome`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-202">Switch to the **Extensions** tab, and type `chrome` into the search box:</span></span>

![Visual Studio Code용 Chrome 디버깅 확장](./media/node-howto-e2e/chrome.png)

<span data-ttu-id="025bf-204">**Chrome용 디버거**를 선택하고 **설치**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-204">Select the extension named **Debugger for Chrome**, and select **Install**.</span></span> <span data-ttu-id="025bf-205">Chrome 디버깅 확장을 설치한 후 **다시 로드**를 선택하여 확장을 활성화하기 위해 Visual Studio Code를 닫고 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-205">After installing the Chrome debugging extension, select **Reload** to close and reopen Visual Studio Code in order to activate the extension.</span></span> 

![Chrome 디버깅 확장을 설치한 후 Visual Studio Code 다시 로드](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

<span data-ttu-id="025bf-207">Visual Stdio 코드 관련 구성 없이 Node.js 코드를 실행하고 디버그할 수 있었지만, 프런트 엔드 웹앱을 디버그하려면 앱을 실행하는 방법을 Visual Studio Code에 지시하는 `launch.json` 파일을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-207">While you were able to run and debug the Node.js code without any Visual Stdio Code-specific configuration, in order to debug a front-end web app, you need to generate a `launch.json` file that instructs Visual Studio Code how to run the app.</span></span> 

<span data-ttu-id="025bf-208">`launch.json` 파일을 생성하려면 **디버그** 탭으로 전환하고, 톱니 바퀴 아이콘(위쪽에 빨간색 점이 없어야 함)을 클릭한 다음, **node.js** 환경을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-208">To generate the `launch.json` file, switch to the **Debug** tab, click the gear icon (which should have a little red dot on top of it), and select the **node.js** environment.</span></span>

![launch.json 파일을 구성하는 Visual Studio Code 옵션](./media/node-howto-e2e/debug-gear.png)

<span data-ttu-id="025bf-210">일단 만들어지면 `launch.json` 파일은 다음과 비슷하며, 디버그하기 위해 앱을 시작 및/또는 연결하는 방법을 Visual Studio Code에 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-210">Once created, the `launch.json` file looks similar to the following, and tells Visual Studio Code how to launch and/or attach to the app in order to debug it.</span></span> 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceRoot}/server.js"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "Attach to Port",
            "address": "localhost",
            "port": 5858
        }
    ]
}
```

<span data-ttu-id="025bf-211">Visual Studio Code에서 앱의 시작 스크립트가 `server.js`임을 감지할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-211">Note that Visual Studio Code was able to detect that the app's startup script is `server.js`.</span></span> 

<span data-ttu-id="025bf-212">열려 있는 `launch.json` 파일을 통해 **구성 추가**(오른쪽 아래)를 선택하고 **Chrome: Launch with userDataDir**(Chrome: userDataDir로 시작)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-212">With the `launch.json` file open, select **Add Configuration** (bottom right), and select **Chrome: Launch with userDataDir**.</span></span>

![Visual Studio Code에 Chrome 구성 추가](./media/node-howto-e2e/add-chrome-config.png)

<span data-ttu-id="025bf-214">Chrome에 새 실행 구성을 추가하면 프런트 엔드 JavaScript 코드를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-214">Adding a new run configuration for Chrome allows you to debug the front-end JavaScript code.</span></span> 

<span data-ttu-id="025bf-215">마우스로 지정된 설정 위를 가리키면 설정에서 수행하는 작업에 대한 설명서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-215">You can hover your mouse over any of the settings that are specified to view documentation about what the setting does.</span></span> <span data-ttu-id="025bf-216">또한 Visual Studio Code는 앱의 URL을 자동으로 감지합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-216">Additionally, notice that Visual Studio Code automatically detects the URL of the app.</span></span> <span data-ttu-id="025bf-217">**webRoot** 속성을 `${workspaceRoot}/public`으로 업데이트하여 Chrome 디버거에서 앱의 프런트 엔드 자산을 찾을 위치를 인식할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-217">Update the **webRoot** property to `${workspaceRoot}/public` so that the Chrome debugger will know where to find the app's front-end assets:</span></span>

```json
{
   "type": "chrome",
   "request": "launch",
   "name": "Launch Chrome",
   "url": "http://localhost:8080",
   "webRoot": "${workspaceRoot}/public",
   "userDataDir": "${workspaceRoot}/.vscode/chrome"
}
```

<span data-ttu-id="025bf-218">프런트 엔드와 백 엔드 모두를 동시에 시작/디버그하려면 동시에 실행할 구성 집합을 Visual Studio Code에 알려주는 *복합* 실행 구성을 만들어야 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-218">In order to launch/debug both the front and back-end at the same time, you need to create a *compound* run configuration that tells Visual Studio Code which set of configurations to run in parallel.</span></span> 

<span data-ttu-id="025bf-219">다음 코드 조각을 `launch.json` 파일 내의 최상위 수준 속성(기존 **configurations** 속성의 형제)으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-219">Add the following snippet as a top-level property within the `launch.json` file (as a sibling of the existing **configurations** property).</span></span>

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

<span data-ttu-id="025bf-220">**compounds.configurations** 배열에 지정된 문자열 값은 **configurations** 목록에 있는 개별 항목의 **name**을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-220">The string values specified in the **compounds.configurations** array refer to the **name** of individual entries in the list of **configurations**.</span></span> <span data-ttu-id="025bf-221">이러한 이름을 수정한 경우 배열에서 적절히 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-221">If you've modfied those names, you'll need to make the appropriate changes in the array.</span></span> <span data-ttu-id="025bf-222">이 기능이 활성 중인지 확인하려면 디버그 탭으로 전환하고, 선택한 구성을 **Full-Stack**(복합 구성의 이름)으로 변경한 다음, **&lt;F5>** 키를 눌러 해당 구성을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-222">To see this in action, switch to the debug tab, and change the selected configuration to **Full-Stack** (the name of the compound configuration), and press **&lt;F5>** to run it.</span></span>

![Visual Studio Code에서 구성 실행](./media/node-howto-e2e/full-stack-profile.png)

<span data-ttu-id="025bf-224">구성을 실행하면 Node.js 앱(디버그 콘솔 출력에서 볼 수 있는 것과 동일함)과 Chrome(`http://localhost:8080`에서 Node.js 앱으로 이동하도록 구성됨)이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-224">Running the configuration launches the Node.js app (as can be seen in the debug console output) and Chrome (configured to navigate to the Node.js app at `http://localhost:8080`).</span></span>

<span data-ttu-id="025bf-225">**&lt;Ctrl>P**를 누르고 앱의 프런트 엔드에 대한 주 Angular 컨트롤러인 `todos.js`를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-225">Press **&lt;Ctrl>P**, and enter (or select) `todos.js`, which is the main Angular controller for the app's front-end.</span></span> 

<span data-ttu-id="025bf-226">11번 줄에 중단점을 설정합니다. 이 중단점은 만들려는 새 할 일 항목에 대한 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-226">Set a breakpoint on line 11, which is the entry-point for a new todo entry being created.</span></span>

<span data-ttu-id="025bf-227">실행 중인 앱으로 돌아가서 새 할 일 항목을 추가하고, 이제 Angular 코드 내에서 일시 중단된 실행이 Visual Studio Code에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-227">Return to the running app, add a new todo entry, and notice that Visual Studio Code has now suspended execution within the Angular code.</span></span>

![Visual Studio Code에서 프런트 엔드 코드 디버깅](./media/node-howto-e2e/chrome-pause.png)

<span data-ttu-id="025bf-229">Node.js 디버깅과 마찬가지로 마우스로 식 위를 가리키고, 지역/조사 식을 보고, 콘솔에서 식을 평가하는 등의 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-229">Like Node.js debugging, you can hover your mouse over expressions, view locals/watches, evaluate expressions in the console, and so on.</span></span> 

<span data-ttu-id="025bf-230">유의해야 할 두 가지 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-230">There are two cools things to note:</span></span>

1. <span data-ttu-id="025bf-231">**호출 스택** 창에는 서로 다른 두 가지 스택, **Node** 및 **Chrome**이 표시되며, 현재 일시 중지된 스택을 나타내고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-231">The **Call Stack** pane displays two different stacks: **Node** and **Chrome**, and indicates which one is currently paused.</span></span>

1. <span data-ttu-id="025bf-232">프런트 엔드와 백 엔드 코드 간에 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-232">You can step between front and back-end code.</span></span> <span data-ttu-id="025bf-233">이 작업을 테스트하려면 Express 경로에서 이전에 설정한 중단점을 실행하고 적중하는 **&lt;F5>** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-233">To test this, press **&lt;F5>**, which will run and hit the breakpoint previously set in the Express route.</span></span>

<span data-ttu-id="025bf-234">이 설정을 사용하면 이제 Visual Studio Code 내에서 프런트 엔드, 백 엔드 또는 전체 스택 JavaScript 코드를 효율적으로 직접 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-234">With this setup, you can now efficiently debug front, back, or full-stack JavaScript code directly within Visual Studio Code.</span></span> 

<span data-ttu-id="025bf-235">또한 복합 디버거 개념은 두 가지 대상 프로세스만으로 제한되지 않고 JavaScript만으로도 제한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-235">In addition, the compound debugger concept is not limited to just two target processes, and also isn't just limited to JavaScript.</span></span> <span data-ttu-id="025bf-236">따라서 마이크로 서비스 앱(잠재적으로 다국어 사용)에서 작동하는 경우 언어/프레임워크에 적절한 확장을 설치하면 똑같은 워크플로를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-236">Therefore, if work on a microservice app (that is potentially polyglot), you can use the exact same workflow (once you've installed the appropriate extensions for the language/framework).</span></span>

## <a name="dockerizing-the-app"></a><span data-ttu-id="025bf-237">앱 Docker화</span><span class="sxs-lookup"><span data-stu-id="025bf-237">Dockerizing the app</span></span>

<span data-ttu-id="025bf-238">이 섹션에서는 Visual Studio Coded에서 [Docker](https://www.docker.com/)를 사용하여 개발할 때 제공하는 환경에 중점을 둡니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-238">This section focuses on the experience that Visual Studio Code provides for developing with [Docker](https://www.docker.com/).</span></span> <span data-ttu-id="025bf-239">Node.js 개발자는 Docker를 사용하여 개발, 즉 CI(연속 통합) 및 프로덕션 환경 모두에 이식 가능한 앱 배포를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-239">Node.js developers use Docker to provide portable app deployments for both development, CI (continuous integration), and production environments.</span></span> <span data-ttu-id="025bf-240">Docker는 급격한 학습 곡선과 같이 빠르게 습득할 수 있으므로 앱에서 Docker를 사용하여 일부를 간소화하는 데 도움이 되는 확장이 Visual Studio Code에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-240">As Docker presents a steep-learning curve to some, Visual Studio Code provides an extension that tries to help simplify some using Docker in your apps.</span></span>

<span data-ttu-id="025bf-241">**확장** 탭으로 다시 전환하고, `docker`를 검색한 다음, **Docker** 확장을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-241">Switch back to the **Extensions** tab, search for `docker`, and select the **Docker** extension.</span></span> 

<span data-ttu-id="025bf-242">Docker 확장을 설치하고 Visual Studio Code를 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-242">Install the Docker extension, and then reload Visual Studio Code.</span></span>

![Visual Studio Code용 Docker 확장 설치](./media/node-howto-e2e/docker-search.png)

<span data-ttu-id="025bf-244">Visual Studio Code의 Docker 확장에는 기존 프로젝트를 위한 *Dockerfile* 및 `docker-compose.yml` 파일을 생성하는 명령이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-244">The Docker extension for Visual Studio Code includes a command for generating a *Dockerfile* and the `docker-compose.yml` file for an existing project.</span></span> 

<span data-ttu-id="025bf-245">사용 가능한 Docker 명령을 보려면 **&lt;F1>** 키를 통해 명령 팔레트를 표시하고 `docker`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-245">To see the available Docker commands, display the command palette - via **&lt;F1>** - and type `docker`.</span></span>

![<span data-ttu-id="025bf-246">Visual Studio용 Docker 확장에서 지원되는 명령</span><span class="sxs-lookup"><span data-stu-id="025bf-246">Commands supported by the Docker extension for Visual Studio</span></span> ](./media/node-howto-e2e/docker-commands.png)

<span data-ttu-id="025bf-247">**Docker: Add docker files to workspace**(Docker: 작업 영역에 Docker 파일 추가)를 선택하고, **Node.js**를 앱 플랫폼으로 선택한 다음, 앱에서 `8080` 포트를 공개하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-247">Select **Docker: Add docker files to workspace**, select **Node.js** as the app platform, and specify that the app exposes port `8080`.</span></span> 

<span data-ttu-id="025bf-248">Docker 명령은 즉시 사용할 수 있는 완전한 `Dockerfile` 및 Docker 작성 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-248">The Docker command generates a complete `Dockerfile` and Docker-compose files that you can begin using immediately.</span></span>

![생성된 Dockerfile](./media/node-howto-e2e/docker-file.png)

<span data-ttu-id="025bf-250">또한 Docker 확장은 `Dockerfiles` 및 `docker-compose.yml` 파일에 대한 자동 완성 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-250">The Docker extension also provides auto-completion for your `Dockerfiles` and `docker-compose.yml` files.</span></span> 

<span data-ttu-id="025bf-251">이 기능이 활성 중인지 확인하려면 `Dockerfile`을 열고 다음의 2번 줄을</span><span class="sxs-lookup"><span data-stu-id="025bf-251">To see this in action, open the `Dockerfile` and change line 2 from:</span></span>

```docker
FROM node:latest
```

<span data-ttu-id="025bf-252">아래와 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-252">To:</span></span>

```docker
FROM mhart
```

<span data-ttu-id="025bf-253">`mhart`의 `t` 뒤에 커서를 배치한 다음 **&lt;Ctrl>&lt;스페이스>** 를 눌러 `mhart`에서 DockerHub에 게시한 모든 이미지 리포지토리를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-253">With your cursor positioned after the `t` in `mhart`, press **&lt;Ctrl>&lt;Space>** to view all the image repositories that `mhart` has published on DockerHub.</span></span>

![Docker 확장의 자동 완성](./media/node-howto-e2e/docker-completion.png)

<span data-ttu-id="025bf-255">이 앱에 필요한 모든 항목을 제공하는 `mhart/alpine-node`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-255">Select `mhart/alpine-node`, which provides everything that this app needs.</span></span> 

<span data-ttu-id="025bf-256">앱 빌드 및 배포가 가능한 빨리 수행되기를 원하므로 일반적으로 이미지가 작을수록 더 효율적이며, 이에 따라 배포와 크기 조정이 더 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-256">Smaller images are typically better since you want your app builds and deployments to be as fast as possible, which makes distribution and scaling quicker.</span></span>

<span data-ttu-id="025bf-257">이제 `Dockerfile`을 생성했으므로 실제 Docker 이미지를 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-257">Now, that you have generated the `Dockerfile`, you need to build the actual Docker image.</span></span> <span data-ttu-id="025bf-258">다시금 말하지만 Visual Studio Code에 설치한 Docker 확장 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-258">Once again, you can use a command that the Docker extension installed in Visual Studio Code.</span></span> <span data-ttu-id="025bf-259">**&lt;F1>** 키를 누르고, 명령 팔레트에서 `dockerb`를 입력한 다음, **Docker: Build Image**(Docker: 이미지 빌드) 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-259">Press **&lt;F1>**, enter `dockerb` at the command palette, and select the **Docker: Build Image** command.</span></span> <span data-ttu-id="025bf-260">방금 생성하여 수정한 `/Dockerfile`을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-260">Choose the `/Dockerfile` that you just generated and modified.</span></span> <span data-ttu-id="025bf-261">DockerHub 사용자 이름(예: `lostintangent/node`)이 포함된 태그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-261">Specify a tag that includes your DockerHub username (e.g. `lostintangent/node`).</span></span> <span data-ttu-id="025bf-262">**&lt;ENTER>** 키를 눌러 빌드되는 Docker 이미지의 출력을 표시하는 통합 터미널 창을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-262">Press **&lt;ENTER>** to launch the integrated terminal window that displays the output of your Docker image being built.</span></span>

![Docker 이미지 빌드 상태](./media/node-howto-e2e/docker-build.png)

<span data-ttu-id="025bf-264">이 명령은 `docker build`를 실행하는 프로세스를 자동화했습니다. 이는 사용하도록 선택할 수 있거나 Docker CLI를 직접 사용할 수 있는 생산성 강화 도구의 또 다른 예입니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-264">Notice that the command automated the process of running `docker build` for you, which is another example of a productivity enhancer that you can either choose to use, or you can just use the Docker CLI directly.</span></span> 

<span data-ttu-id="025bf-265">이 시점에서 이 이미지를 쉽게 배포할 수 있게 하려면 해당 이미지를 DockerHub로 푸시하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-265">At this point, to make this image easily acquirable for deployments, you need only push the image to DockerHub.</span></span> <span data-ttu-id="025bf-266">이렇게 하려면 CLI에서 `docker login`을 실행하고 자신의 계정 자격 증명을 입력하여 DockerHub를 통해 이미 인증되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-266">To do this, make sure you have already autheticated with DockerHub by running `docker login` from the CLI and entering your account credentials.</span></span> <span data-ttu-id="025bf-267">그런 다음 Visual Studio Code에서 명령 팔레트를 표시하고, `dockerpush`를 입력한 다음, `Docker: Push` 명령을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-267">Then, in Visual Studio Code, you can bring up the command palette, enter `dockerpush`, and select the `Docker: Push` command.</span></span> <span data-ttu-id="025bf-268">방금 빌드한 이미지 태그(예: `lostintangent/node`)를 선택하고 **&lt;Enter>** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-268">Select the image tag that you just built (e.g. `lostintangent/node`) and press **&lt;Enter>**.</span></span> <span data-ttu-id="025bf-269">이 명령은 `docker push`의 호출을 자동화하고 통합 터미널에 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-269">The command automates the calling of `docker push` and displays the output in the integrated terminal.</span></span>

## <a name="deploying-the-app"></a><span data-ttu-id="025bf-270">앱 배포</span><span class="sxs-lookup"><span data-stu-id="025bf-270">Deploying the app</span></span>

<span data-ttu-id="025bf-271">이제 앱이 Docker화되고 DockerHub에 푸시되었으므로 전 세계에서 볼 수 있도록 클라우드에 해당 앱을 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-271">Now that you the app Dockerized and pushed to DockerHub, you need to deploy it to the cloud so the world can see it.</span></span> <span data-ttu-id="025bf-272">이를 위해 Azure의 PaaS 제품인 Azure App Service를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-272">For this, you can use Azure App Service, which is Azure's PaaS offering.</span></span> <span data-ttu-id="025bf-273">App Service에는 Node.js 개발자와 관련된 두 가지 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-273">App Service has two capabilities that are relevant to Node.js developers:</span></span>

- <span data-ttu-id="025bf-274">Linux 기반 VM 지원 - 네이티브 Node 모듈을 사용하여 빌드된 앱 또는 Windows를 지원하지 않거나 다르게 작동할 수 있는 다른 도구에 대한 비호환성 문제가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-274">Support for Linux-based VMs, which reduces incompatibilities for apps which are built using native Node modules, or other tools which might not support Windows and/or may behave differently.</span></span>
- <span data-ttu-id="025bf-275">Docker 기반 배포 지원 - Docker 이미지의 이름을 지정하고, App Service에서 이미지를 자동으로 가져오고, 배포하고, 크기 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-275">Support for Docker-based deployments, which allows you to specify the name of your Docker image, and allow App Service to pull, deploy, and scale the image automatically.</span></span>

<span data-ttu-id="025bf-276">시작하려면 Visual Studio 터미널을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-276">To get started, open up the Visual Studio terminal.</span></span> <span data-ttu-id="025bf-277">새 Azure CLI 2.0을 사용하여 Azure 계정을 관리하고 할 일 앱을 실행하는 데 필요한 인프라를 프로비전합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-277">You'll use the new Azure CLI 2.0 to manage your Azure account and provision the necessary infrastructure to run the todo app.</span></span> <span data-ttu-id="025bf-278">필수 구성 요소에서 설명한 대로 CLI에서 `az login` 명령을 사용하여 계정에 로그인한 후 다음 단계에 따라 App Service 인스턴스를 프로비전하고 할 일 앱 컨테이너를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-278">Once you've logged into your account from the CLI using the `az login` command (as mentioned in the pre-reqs), perform the following steps to provision the App Service instance and deploy the todo app container:</span></span>

1. <span data-ttu-id="025bf-279">Azure 리소스를 구성하는 데 도움이 되는 *네임스페이스* 또는 *디렉터리*로 간주할 수 있는 리소스 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-279">Create a resource group, which you can think of as a *namespace* or *directory* for helping to organize Azure resources.</span></span> <span data-ttu-id="025bf-280">`-n` 옵션은 그룹의 이름을 지정하는 데 사용되며, 원하는 대로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-280">The `-n` option is used to specify the name of the group and can be anything you want.</span></span>

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > <span data-ttu-id="025bf-281">`-l` 옵션은 리소스 그룹의 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-281">The `-l` option indicates the location of the resource group.</span></span> <span data-ttu-id="025bf-282">미리 보기로 있는 동안 Linux에 대한 App Service 지원은 일부 지역에서만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-282">While in preview, the App Service on Linux support is available only in select regions.</span></span> <span data-ttu-id="025bf-283">따라서 미국 서부에 있지 않고 다른 지역에서 사용할 수 있는지 확인하려면 CLI에서 `az appservice list-locations --linux-workers-enabled`를 실행하여 데이터 센터 옵션을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="025bf-283">Therefore, if you aren't located in the Western US, and you want to check which other regions are available, run `az appservice list-locations --linux-workers-enabled` from the CLI to view your datacenter options.</span></span>

2. <span data-ttu-id="025bf-284">각 CLI 호출에서 리소스 그룹을 명시적으로 지정하지 않고도 CLI를 계속 사용할 수 있도록 새로 만든 리소스 그룹을 기본 리소스 그룹으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-284">Set the newly created resource group as the default resource group so that you can continue to use the CLI without needing to explicitly specify the resource group with each CLI call:</span></span>

   ```shell
   az configure -d group=nina-demo
   ```
   
3. <span data-ttu-id="025bf-285">앱이 배포된 기본 가상 컴퓨터의 생성 및 크기 조정을 관리하는 App Service *계획*을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-285">Create the App Service *plan*, which manages the creation and scaling of the underlying virtual machines to which your app is deployed.</span></span> <span data-ttu-id="025bf-286">다시 한 번 `n` 옵션에 대해 원하는 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-286">Once again, specify any value that you'd like for the `n` option.</span></span>

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > <span data-ttu-id="025bf-287">--is-linux 옵션은 Linux 기반 가상 컴퓨터가 필요하다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-287">The --is-linux option is indicates that you want Linux-based virtual machines.</span></span> <span data-ttu-id="025bf-288">이 옵션이 없으면 CLI에서 기본적으로 Windows 기반 가상 컴퓨터를 프로비전하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-288">Without it, the CLI defaults to provisioning Windows-based virtual machines.</span></span>

4. <span data-ttu-id="025bf-289">방금 생성된 계획 및 리소스 그룹 내에서 실행될 실제 할 일 앱을 나타내는 App Service 웹앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-289">Create the App Service web app, which represents the actual todo app that will be running within the plan and resource group just created.</span></span> <span data-ttu-id="025bf-290">웹앱은 프로세스 또는 컨테이너와 동의어로, 계획은 실행 중인 가상 컴퓨터/컨테이너 호스트로 간주할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-290">You can think of a web app as being synonymous with a process or container, and the plan as being the virtual machine/container host that they're running on.</span></span> <span data-ttu-id="025bf-291">또한 웹앱을 만드는 작업의 일부로 DockerHub에 게시한 Docker 이미지를 사용하도록 해당 웹앱을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-291">Additionally, as part of creating the web app, you'll need to configure it to use the Docker image you published to DockerHub:</span></span>

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > <span data-ttu-id="025bf-292">사용자 지정 컨테이너를 사용하는 대신 Git를 배포하려면 [Azure에 Node.js 웹앱 만들기](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="025bf-292">If instead of using a custom container, you'd prefer a Git deployment, refer to the article, [Create a Node.js web app in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span></span>

5. <span data-ttu-id="025bf-293">웹앱을 기본 웹 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-293">Set the web app as the default web instance:</span></span>

    ```shell
    az configure -d web=nina-demo-app
    ```

6. <span data-ttu-id="025bf-294">앱을 실행하여 `*.azurewebsites.net` URL에서 사용할 수 있는 배포된 컨테이너를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-294">Launch the app to view the deployed container, which will be available at an `*.azurewebsites.net` URL:</span></span>

    ```shell
    az webapp browse
    ```

    ![브라우저에서 실행 중인 할 일 앱](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > <span data-ttu-id="025bf-296">App Service에서 DockerHub의 Docker 이미지를 끌어온 다음 시작해야 하므로 앱을 처음 로드하는 데 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-296">It may take few minutes to load app the first time as App Service has to pull the Docker image from DockerHub and then start it.</span></span>

<span data-ttu-id="025bf-297">이 시점에서 할 일 앱을 배포하고 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-297">At this point, you've just deployed and run the todo app.</span></span> 

<span data-ttu-id="025bf-298">이제 할 일 앱을 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-298">You have now deployed the todo app.</span></span> <span data-ttu-id="025bf-299">그러나 회전하는 아이콘은 앱이 데이터베이스에 연결할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-299">However, the spinning icon indicates that the app can't connect to the database.</span></span> <span data-ttu-id="025bf-300">이는 분명히 Azure 데이터 센터 내에서 연결할 수 없는 개발 중인 MongoDB의 로컬 인스턴스를 사용했기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-300">This is due to the fact that you were using a local instance of MongoDB during development, which obviously isn't reachable from within the Azure datacenters.</span></span> <span data-ttu-id="025bf-301">환경 변수를 통해 연결 문자열을 수락하도록 앱을 수정했으므로 MongoDB 서버를 시작하고 이 환경 변수를 참조하도록 App Service 인스턴스를 다시 구성하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-301">Since you modified the app to accept the connection string via an environment variable, you need only to start a MongoDB server and re-configure the App Service instance to reference the environment variable.</span></span> <span data-ttu-id="025bf-302">이 내용은 다음 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-302">This is illustrated in the next section.</span></span>

## <a name="provisioning-a-mongodb-server"></a><span data-ttu-id="025bf-303">MongoDB 서버 프로비전</span><span class="sxs-lookup"><span data-stu-id="025bf-303">Provisioning a MongoDB server</span></span>

<span data-ttu-id="025bf-304">직접 MongoDB 서버 또는 복제본 세트를 구성하고 해당 인프라를 관리할 수 있지만 Azure에서는 [Cosmos DB](https://azure.microsoft.com/services/documentdb/)라는 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-304">While you could configure a MongoDB server, or replica set, and manage that infrastructure yourself, Azure provides a solution called [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span></span> <span data-ttu-id="025bf-305">Cosmos DB는 완벽하게 관리되고 지리적으로 복제 가능한 고성능 NoSQL 데이터베이스로서 MongoDB 호환성 계층을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-305">Cosmos DB is a fully-managed, geo-replicable, high-performance, NoSQL database that provides a MongoDB-compatibility layer.</span></span> <span data-ttu-id="025bf-306">즉, 연결 문자열만 변경하여 Cosmos DB(또는 [Studio 3T](https://studio3t.com/)와 같은 MongoDB 클라이언트/도구)에서 기존 MEAN 앱을 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-306">This means that you can point an existing MEAN app at it (or any MongoDB client/tool such as [Studio 3T](https://studio3t.com/)) without needing to change anything but the connection string.</span></span> <span data-ttu-id="025bf-307">다음 단계에서는 이 작업이 수행되는 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-307">The following steps illustrate how this is done:</span></span>

1. <span data-ttu-id="025bf-308">Visual Studio Code 터미널에서 다음 명령을 실행하여 Cosmos DB 서비스의 MongoDB 호환 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-308">From the Visual Studio Code terminal, run the following command to create a MongoDB-compatible instance of the Cosmos DB service.</span></span> <span data-ttu-id="025bf-309">**<NAME>** 자리 표시자를 전역 고유 값으로 바꿉니다(Cosmos DB에서는 이 이름을 사용하여 데이터베이스의 서버 URL을 생성함).</span><span class="sxs-lookup"><span data-stu-id="025bf-309">Replace the **<NAME>** placeholder with a globally unique value (Cosmos DB uses this name to generate the database's server URL):</span></span>

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. <span data-ttu-id="025bf-310">이 인스턴스에 대한 MongoDB 연결 문자열을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-310">Retrieve the MongoDB connection string for this instance:</span></span>

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. <span data-ttu-id="025bf-311">로컬로 실행 중인 MongoDB 서버(존재하지 않음)에 연결하는 대신 새로 프로비전된 Cosmos DB 인스턴스에 연결하도록 웹앱의 **MONGODB_URL** 환경 변수를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-311">Update your web app's **MONGODB_URL** environment variable so that it connects to the newly provisioned Cosmos DB instance instead of attempting to connect to a locally running MongoDB server (that doesn't exist!):</span></span>

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. <span data-ttu-id="025bf-312">브라우저로 돌아가서 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-312">Return to your browser and refresh it.</span></span> <span data-ttu-id="025bf-313">할 일 항목을 추가하거나 제거하여 아무 것도 변경하지 않고도 앱이 작동함을 증명합니다!</span><span class="sxs-lookup"><span data-stu-id="025bf-313">Try adding and removing a todo item to prove that the app now works without needing to change anything!</span></span> <span data-ttu-id="025bf-314">환경 변수를 만든 Cosmos DB 인스턴스로 설정합니다.이 인스턴스는 MongoDB 데이터베이스를 완벽하게 에뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-314">Set the environment variable to the created Cosmos DB instance, which is fully emulating a MongoDB database.</span></span>

    ![데이터베이스에 연결된 이후의 데모 앱](./media/node-howto-e2e/finished-demo.png)

<span data-ttu-id="025bf-316">필요에 따라 Cosmos DB 인스턴스로 다시 전환하고 MongoDB 인스턴스에 필요한 예약된 처리량을 강화(또는 축소)할 수 있으며, 수동으로 인프라를 관리할 필요 없이 추가된 트래픽의 이점을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-316">When needed, you can switch back to the Cosmos DB instance and scale up (or down) the reserved throughput that the MongoDB instance needs, and benefit from the added traffic without needing to manage any infrastructure manually.</span></span>

<span data-ttu-id="025bf-317">또한 Cosmos DB는 자동으로 모든 단일 문서와 속성을 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-317">Additionally, Cosmos DB automatically indexes every single document and property for you.</span></span> <span data-ttu-id="025bf-318">이렇게 하면 느린 쿼리를 프로파일링하거나 수동으로 인덱스를 미세 조정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-318">That way, you don't need to profile slow queries or manually fine-tune your indexes.</span></span> <span data-ttu-id="025bf-319">필요에 따라 프로비전 및 크기 조정하고, Cosmos DB에서 나머지 작업을 처리하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-319">Just provision and scale as needed, and let Cosmos DB handle the rest.</span></span>

## <a name="hosting-a-private-docker-registry"></a><span data-ttu-id="025bf-320">개인 Docker 레지스트리 호스팅</span><span class="sxs-lookup"><span data-stu-id="025bf-320">Hosting a private Docker registry</span></span>

<span data-ttu-id="025bf-321">DockerHub는 보안/거버넌스 또는 성능 이점과 같이 컨테이너 이미지를 배포하는 데 유용한 환경을 제공하지만 고유의 개인 Docker 레지스트리를 호스팅하려는 시나리오가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-321">DockerHub provides an amazing experience for distributing your container images, but there may be scenarios where you'd prefer to host your own private Docker registry - such as for security/governance or performance benefits.</span></span> <span data-ttu-id="025bf-322">이를 위해 Azure에서는 지원하는 저장소가 웹앱(더 빨리 끌어올 수 있음)과 동일한 데이터 센터에 있는 Docker 레지스트리를 만들 수 있는 [ACR(Azure Container Registry)](https://azure.microsoft.com/services/container-registry/)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-322">For this purpose, Azure provides the [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) that allows you to spin up your own Docker registry whose backing storage is located in the same data center as your web app (which makes pulls quicker).</span></span> <span data-ttu-id="025bf-323">또한 ACR은 이미지를 푸시하거나 끌어올 수 있는 사람과 같이 콘텐츠 및 액세스 제어에 대한 완벽한 제어 권한도 사용자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-323">The ACR also provides you with full control over the contents and access controls - such as who can push or pull images.</span></span> 

<span data-ttu-id="025bf-324">다음 명령을 실행하여 사용자 지정 레지스트리 프로비전을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-324">Provisioning a custom registry can be accomplished by running the following command.</span></span> <span data-ttu-id="025bf-325">ACR에서 레지스트리의 로그인 서버 URL을 생성하는 데 지정된 값을 사용하므로 **<NAME>** 자리 표시자를 고유한 전역 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-325">(Replace the **<NAME>** placeholder with a globally unique value as ACR uses specified value to generate the registry's login server URL.</span></span>

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="025bf-326">이 항목의 예제에서는 **관리자 계정**을 사용하여 작업을 단순하게 유지하지만 프로덕션 레지스트리에는 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-326">While this topic's example uses the **admin account** to keep things simple, it is not recommended for production registries.</span></span> 

<span data-ttu-id="025bf-327">`az acr create` 명령은 Docker CLI(예: `ninademo.azurecr.io`)를 사용하여 로그인하는 데 사용하는 로그인 서버 URL(`LOGIN SERVER` 열을 통해)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-327">The `az acr create` commands displays the login server URL (via the `LOGIN SERVER` column) that you use to log in using the Docker CLI (e.g. `ninademo.azurecr.io`).</span></span> <span data-ttu-id="025bf-328">또한 이 명령은 인증에 사용할 수 있는 관리자 자격 증명을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-328">Additionally, the command generates admin credentials that you can use in order to authenticate against it.</span></span> <span data-ttu-id="025bf-329">이러한 자격 증명을 검색하려면 다음 명령을 실행하고 표시된 사용자 이름과 암호를 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-329">To retrieve those credentials, run the following command and note the displayed username and password:</span></span>

```shell
az acr credential show -n $ACR_NAME
```

<span data-ttu-id="025bf-330">이전 단계의 자격 증명과 개별 로그인 서버를 사용하면 표준 Docker CLI 워크플로를 통해 레지스트리에 로그인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-330">Using the credentials from the previous step, and your individual login server, you can log in to the registry using the standard Docker CLI workflow.</span></span>

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

<span data-ttu-id="025bf-331">이제 `lostintangent/node`를 컨테이너 이미지에 지정한 이름으로 바꾸는 다음 명령을 사용하여 개인 레지스트리와 연결되어 있음을 나타내도록 Docker 컨테이너에 태그를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-331">You can now tag your Docker container to indicate that it's associated with your private registry using the following command (replacing `lostintangent/node` with the name you gave the container image.</span></span>

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="025bf-332">마지막으로 태그가 지정된 이미지를 개인 Docker 레지스트리로 푸시합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-332">Finally, push the tagged image to your private Docker registry.</span></span>

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="025bf-333">이제 컨테이너가 사용자 고유의 개인 레지스트리에 저장되고, Docker CLI는 DockerHub를 사용할 때와 동일한 방식으로 계속 작업할 수 있게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-333">Your container is now stored in your own private registry, and the Docker CLI was happy to allow you to continue working in the same way as you did when using DockerHub.</span></span> <span data-ttu-id="025bf-334">App Service 웹앱에서 개인 레지스트리에서 가져오도록 지시하려면 다음 명령만 실행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-334">In order to instruct the App Service web app to pull from your private registry, you need only run the following command:</span></span>

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> <span data-ttu-id="025bf-335">`-r` 옵션의 시작 부분에 `https://` 접두사를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-335">Make sure to add the `https://` prefix to the beginning of the `-r` option.</span></span> <span data-ttu-id="025bf-336">그러나 이 접두사를 컨테이너 이미지 이름에는 추가하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="025bf-336">However, don't add the prefix to the container image name.</span></span>

<span data-ttu-id="025bf-337">브라우저에서 앱을 새로 고치면 모든 것이 동일하게 표시되고 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-337">If you refresh the app in your browser, everything should look and work the same.</span></span> <span data-ttu-id="025bf-338">그러나 이제는 개인 Docker 레지스트리를 통해 앱을 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-338">However, it's now running your app via your private Docker registry.</span></span> <span data-ttu-id="025bf-339">앱을 업데이트한 후 위에서 수행한 대로 태그를 지정하고, 변경 내용을 적용한 다음, App Service 컨테이너 구성에서 태그를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-339">Once you update your app, tag and push the changes as done above, and update the tag in your App Service container configuration.</span></span>

## <a name="configuring-a-custom-domain-name"></a><span data-ttu-id="025bf-340">사용자 지정 도메인 이름 구성</span><span class="sxs-lookup"><span data-stu-id="025bf-340">Configuring a custom domain name</span></span>

<span data-ttu-id="025bf-341">`*.azurewebsites.net` URL은 테스트에 적합하지만, 어느 시점에서 사용자 지정 도메인 이름을 웹앱에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-341">While the `*.azurewebsites.net` URL is great for testing, at some point you may want to add a custom domain name to your web app.</span></span> <span data-ttu-id="025bf-342">등록자의 도메인 이름이 있으면 웹앱의 외부 IP(실제로 부하 분산 장치)를 가리키는 `A` 레코드만 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-342">Once you have a domain name from a registrar, you need only add an `A` record to it  that points at your web app's external IP (which is actually a load balancer).</span></span> <span data-ttu-id="025bf-343">다음 명령을 실행하여 이 IP를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-343">You can retrieve this IP by running the following command:</span></span>

```shell
az webapp config hostname get-external-ip
```

<span data-ttu-id="025bf-344">`A` 레코드를 추가하는 것 외에도, 지금까지 사용 중인 `*.azurewebsites.net` 도메인을 가리키는 `TXT` 레코드를 도메인에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-344">In addition to add an `A` record, you also need to add a `TXT` record to your domain that points at the `*.azurewebsites.net` domain you've been using thus far.</span></span> <span data-ttu-id="025bf-345">`A`과 `TXT` 레코드의 조합을 사용하면 Azure에서 사용자가 해당 도메인을 소유하고 있음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-345">The combination of the `A` and `TXT` records allows Azure to verify that you own the domain.</span></span>

<span data-ttu-id="025bf-346">일단 레코드가 만들어지고 DNS 변경 내용이 전파되면 들어오는 트래픽을 올바르게 예상하는지 파악할 수 있도록 Azure에 사용자 지정 도메인을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-346">Once those records are created - and the DNS changes have propagated - register the custom domain with Azure so that it knows to expect the incoming traffic correctly.</span></span> 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> <span data-ttu-id="025bf-347">이 명령이 작동하려면 먼저 DNS 변경 내용이 전파되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-347">The command will not work until the DNS changes have propagated.</span></span>

<span data-ttu-id="025bf-348">브라우저를 열고 사용자 지정 도메인으로 이동하여 이제 Azure에서 배포된 앱으로 확인하는지 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-348">Open a browser and navigate to your custom domain to see that it now resolves to your deployed app on Azure.</span></span>

## <a name="scaling-up-and-out"></a><span data-ttu-id="025bf-349">강화 및 확장</span><span class="sxs-lookup"><span data-stu-id="025bf-349">Scaling up and out</span></span>

<span data-ttu-id="025bf-350">어느 시점에서는 증가된 트래픽 및 운영 요구 사항을 처리하기에는 할당된 리소스(CPU 및 RAM)가 충분하지 않을 만큼 웹앱이 충분히 인기가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-350">At some point, your web app may become popular enough that its allocated resources (CPU and RAM) aren't sufficient for handling the increase in traffic and operational demands.</span></span> <span data-ttu-id="025bf-351">이전에 만든 App Service 계획(**B1**)에는 하나의 CPU 코어와 1.75GB RAM이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-351">The App Service Plan that you created earlier (**B1**) comes with 1 CPU core and 1.75 GB of RAM, which can get maxed out fairly quickly.</span></span> <span data-ttu-id="025bf-352">**B2** 계획은 이러한 CPU와 RAM의 두 배가 됩니다. 따라서 둘 중 어느 하나가 부족하게 되면 앱에서 다음 명령을 실행하여 기본 가상 컴퓨터를 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-352">The **B2** plan come swith twice as much RAM and CPU, so if you notice that your app is beginning to run out of either, you can scale up the underlying virtual machine by running the following command:</span></span>

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> <span data-ttu-id="025bf-353">Azure App Service 계획에 대한 가격 책정 세부 정보 및 사양은 [App Service 가격](https://azure.microsoft.com/pricing/details/app-service/) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="025bf-353">For Azure App Plan pricing details and specs, see the article, [App Service Pricing](https://azure.microsoft.com/pricing/details/app-service/)</span></span>

<span data-ttu-id="025bf-354">잠시 후 요청된 하드웨어로 웹앱이 마이그레이션되어 관련 리소스를 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-354">After just a few moments, your web app will be migrated to the requested hardware, and can begin taking advantage of the associated resources.</span></span> <span data-ttu-id="025bf-355">강화 외에도 더 낮은 가격으로 더 적은 리소스를 제공하는 `--sku` 옵션을 지정하여 위와 동일한 명령을 실행하여 규모를 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-355">In addition to scaling up, you can also scale down by running the same command as above, specifying a `--sku` option that provides less resources at a lower price.</span></span> 

<span data-ttu-id="025bf-356">가상 컴퓨터 사양을 강화하는 것 외에도, 상태 비저장 웹앱인 경우 기본 가상 컴퓨터 인스턴스를 더 많이 추가하여 *확장*하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-356">In addition to scaling up the virtual machine specs, as long as your web app is stateless, you also have the option to *scale out* by adding more underlying virtual machine instances.</span></span> <span data-ttu-id="025bf-357">이전에 만든 App Service 계획에는 단일 가상 컴퓨터(*작업자*)만 있으므로 들어오는 모든 트래픽은 최종적으로 해당 인스턴스 하나의 사용 가능한 리소스 제한을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-357">The App Service Plan you created earlier included only a single virtual machine (a *worker*), and therefore, all incoming traffic is ultimately bound by the limits of the available resources of that one instance.</span></span> <span data-ttu-id="025bf-358">두 번째 가상 컴퓨터 인스턴스를 추가하려는 경우 이전에 실행한 동일한 명령을 실행해도 되지만 SKU를 강화하는 대신 작업자 가상 컴퓨터의 수를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-358">If you want to add a second virtual machine instance, you could run the same command you ran earlier, but instead of scaling up the SKU, you scale out the number of worker virtual machines.</span></span>

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

<span data-ttu-id="025bf-359">웹앱을 이와 같이 확장하면 들어오는 트래픽이 모든 인스턴스 간에 투명하게 부하 분산되어 코드를 변경하거나 필요한 인프라에 대해 걱정하지 않고 용량을 즉시 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-359">When you scale out a web app like this, incoming traffic will be transparently load balanced between all instances, which allows you to immediately increase your capacity without any code changes or worrying about the needed infrastructure.</span></span> 

<span data-ttu-id="025bf-360">상태 비저장 웹앱은 단일 가상 컴퓨터 또는 앱 인스턴스에서 작동하는 데 필요한 상태를 포함하지 않으므로 완전히 결정적으로 크기 조정(강화, 축소 또는 확장)할 수 있는 모범 사례로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-360">Stateless web apps are considered a best practice as they make the ability to scale them (up, down, out) entirely deterministic as no single virtual machine or app instance includes state that is neccessary in order to function.</span></span> 

> [!NOTE]
> <span data-ttu-id="025bf-361">이 항목의 자습서에서는 App Service 계획의 일부로 단일 웹앱을 실행하는 방법을 보여 주지만, 하나의 계획을 프로비전하고 이에 대한 비용을 지불할 수 있도록 여러 웹앱을 만들어 동일한 계획에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-361">While this topic's tutorial illustrates running a single web app as part of an App Service Plan, you can create and deploy multiple web apps into the same plan, allowing you to provision and pay for a single plan.</span></span> 

## <a name="clean-up"></a><span data-ttu-id="025bf-362">정리</span><span class="sxs-lookup"><span data-stu-id="025bf-362">Clean-up</span></span>

<span data-ttu-id="025bf-363">사용하지 않는 Azure 리소스에 대해 요금이 청구되지 않도록 하려면 Visual Studio Code 터미널에서 다음 명령을 실행하여 이 자습서에서 프로비전된 모든 리소스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-363">To ensure that you don't get charged for any Azure resources you aren't using, run the following command from your Visual Studio Code terminal to delete all of the resources provisioned during this tutorial.</span></span>

```shell
az group delete
```

> [!NOTE]
> <span data-ttu-id="025bf-364">정리 프로세스를 완료하는 데 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-364">The clean-up process can take several minutes to complete.</span></span> 

<span data-ttu-id="025bf-365">완료되면 `az group delete` 명령은 Azure 계정을 자습서를 시작하기 전과 동일한 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-365">Once finished, the `az group delete` command leaves your Azure account in the same state it was before you started the tutorial.</span></span> <span data-ttu-id="025bf-366">Azure 리소스를 단일 단위로 구성, 배포 및 삭제하는 기능은 리소스 그룹의 주요 이점 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-366">The ability to organize, deploy, and delete Azure resources as a single unit is one of the primary benefits of resource groups.</span></span> <span data-ttu-id="025bf-367">따라서 동일한 수명을 갖춘 것으로 예상되는 리소스로 그룹화하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="025bf-367">Therefore, as a recommended practice,  you should group your resources together that you anticipate having the same lifespan.</span></span>