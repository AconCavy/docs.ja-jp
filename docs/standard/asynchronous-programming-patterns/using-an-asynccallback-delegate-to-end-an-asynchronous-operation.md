---
title: AsyncCallback デリゲートの使用による非同期操作の終了
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: c3cac2db57a24bf6a0f5640e4ad8101686e6c3e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130920"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="642b3-102">AsyncCallback デリゲートの使用による非同期操作の終了</span><span class="sxs-lookup"><span data-stu-id="642b3-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="642b3-103">非同期操作の結果の待機中に、他の作業を実行できるアプリケーションは、操作が完了するまで待機をブロックする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="642b3-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="642b3-104">次のオプションのいずれかを使用して、非同期操作が完了するまでの待機中に、手順の実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="642b3-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="642b3-105"><xref:System.AsyncCallback> デリゲートを使用し、個別のスレッドで非同期操作の結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="642b3-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="642b3-106">このトピックでは、この方法のデモが実行されます。</span><span class="sxs-lookup"><span data-stu-id="642b3-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="642b3-107">非同期操作の **Begin**_OperationName_ メソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.IsCompleted%2A> プロパティを使用して、その操作が完了したかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="642b3-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="642b3-108">この方法のデモを実行する例については、「[非同期操作のステータスのポーリング](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="642b3-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="642b3-109">例</span><span class="sxs-lookup"><span data-stu-id="642b3-109">Example</span></span>  
 <span data-ttu-id="642b3-110">次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム (DNS) 情報を取得するために、<xref:System.Net.Dns> クラスの非同期メソッドを使用してデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="642b3-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="642b3-111">この例では、`ProcessDnsInformation` メソッドを参照する <xref:System.AsyncCallback> デリゲートを作成します。</span><span class="sxs-lookup"><span data-stu-id="642b3-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="642b3-112">このメソッドは、DNS 情報に対する非同期要求ごとに 1 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="642b3-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="642b3-113">ユーザー指定のホストは、<xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> パラメーターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="642b3-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="642b3-114">複雑な状態オブジェクトの定義と使用に関するデモを実行する例については、「[AsyncCallback デリゲートおよび状態オブジェクトの使用](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="642b3-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="642b3-115">参照</span><span class="sxs-lookup"><span data-stu-id="642b3-115">See also</span></span>

- [<span data-ttu-id="642b3-116">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="642b3-116">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="642b3-117">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="642b3-117">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="642b3-118">IAsyncResult を使用した非同期メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="642b3-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="642b3-119">AsyncCallback デリゲートおよび状態オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="642b3-119">Using an AsyncCallback Delegate and State Object</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
