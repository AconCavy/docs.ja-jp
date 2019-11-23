---
title: サービス操作の実行時間の確認
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 06a4c2da7b702fa4fbc1469576c118b790803339
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291425"
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="fbd6d-102">サービス操作の実行時間の確認</span><span class="sxs-lookup"><span data-stu-id="fbd6d-102">Determining service operation duration</span></span>
<span data-ttu-id="fbd6d-103">Windows Communication Foundation (WCF) アプリケーションで分析トレースが有効になっている場合、サービス操作の実行時間は、イベントログを調べることで簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-103">If analytic tracing is enabled in a Windows Communication Foundation (WCF) application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="fbd6d-104">ここでは、サービス操作の実行にかかる時間を確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="fbd6d-105">サービス操作の実行時間の確認</span><span class="sxs-lookup"><span data-stu-id="fbd6d-105">Determining service operation execution duration</span></span>  
  
1. <span data-ttu-id="fbd6d-106">**[開始]** 、 **[実行]** の順にクリックしてイベントビューアーを開き、`eventvwr.exe`を入力します。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2. <span data-ttu-id="fbd6d-107">分析トレースを有効にしていない場合は、 **[アプリケーションとサービスログ]** 、 **[Microsoft]** 、 **[Windows]** 、 **[アプリケーションサーバー-アプリケーション]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="fbd6d-108">**[表示]** 、 **[分析およびデバッグログの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="fbd6d-109">**[分析]** を右クリックし、 **[ログを有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="fbd6d-110">サービス操作が実行された後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3. <span data-ttu-id="fbd6d-111">次に、サービスプロジェクトと、そのサービスと対話するクライアントプロジェクトを含む WCF アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-111">Next, open a WCF application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="fbd6d-112">このようなアプリケーションを作成するには、[はじめにチュートリアル](../../getting-started-tutorial.md)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-112">You can create such an application by following the [Getting Started Tutorial](../../getting-started-tutorial.md).</span></span>  <span data-ttu-id="fbd6d-113">WCF サンプルがインストールされている場合は、チュートリアルで作成した完成したプロジェクトを含む[入門サンプル](../../samples/getting-started-sample.md)を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-113">If you have the WCF samples installed, you can open the [Getting Started](../../samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4. <span data-ttu-id="fbd6d-114">**F5**キーを押して、サーバーアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="fbd6d-115">**クライアントプロジェクトを**右クリックし、 **[デバッグ]** 、 **[新しいインスタンスを開始]** の順に選択して、クライアントアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5. <span data-ttu-id="fbd6d-116">イベント ビューアーで、分析ログを更新し、イベント ID でイベントを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="fbd6d-117">イベント ID [214-OperationCompleted](214-operationcompleted.md)のイベントを探します。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-117">Look for events with Event ID [214 - OperationCompleted](214-operationcompleted.md).</span></span>  <span data-ttu-id="fbd6d-118">これらのイベントは、完了した操作、およびその操作にかかった時間を示します。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="fbd6d-119">次のイベントは、追加操作の時間を示しています。</span><span class="sxs-lookup"><span data-stu-id="fbd6d-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
