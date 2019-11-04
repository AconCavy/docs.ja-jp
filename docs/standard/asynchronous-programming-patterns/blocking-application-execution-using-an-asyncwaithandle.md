---
title: AsyncWaitHandle の使用によるアプリケーション実行のブロック
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
ms.openlocfilehash: 16b5a297c13cd9096548ed489e4994b72a48da67
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121434"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="617c6-102">AsyncWaitHandle の使用によるアプリケーション実行のブロック</span><span class="sxs-lookup"><span data-stu-id="617c6-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="617c6-103">非同期操作の結果の待機中に、他の作業を継続できないアプリケーションは、操作が完了するまでブロックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="617c6-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="617c6-104">次のオプションのいずれかを使用して、非同期操作が完了するまでの待機中に、アプリケーションのメイン スレッドをブロックします。</span><span class="sxs-lookup"><span data-stu-id="617c6-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="617c6-105">非同期操作の **Begin**_OperationName_ メソッドによって返される <xref:System.IAsyncResult> の <xref:System.IAsyncResult.AsyncWaitHandle%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="617c6-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="617c6-106">このトピックでは、この方法のデモが実行されます。</span><span class="sxs-lookup"><span data-stu-id="617c6-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="617c6-107">非同期操作の **End**_OperationName_ メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="617c6-107">Call the asynchronous operation's **End**_OperationName_ method.</span></span> <span data-ttu-id="617c6-108">この方法をデモの例については、「[非同期操作の終了によるアプリケーション実行のブロック](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="617c6-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="617c6-109">非同期操作が完了するまでブロックする 1 つ以上の <xref:System.Threading.WaitHandle> オブジェクトを使用するアプリケーションは、通常は **Begin**_OperationName_ メソッドを呼び出し、操作の結果なしで実行できるすべての作業を実行し、非同期操作が完了するまでブロックします。</span><span class="sxs-lookup"><span data-stu-id="617c6-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="617c6-110">アプリケーションは、<xref:System.IAsyncResult.AsyncWaitHandle%2A> を使用して <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドのいずれかを呼び出し、単一の操作上でブロックできます。</span><span class="sxs-lookup"><span data-stu-id="617c6-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="617c6-111">非同期操作のセットが完了するまで待機しながらブロックするには、関連する <xref:System.IAsyncResult.AsyncWaitHandle%2A> オブジェクトを配列に格納し、<xref:System.Threading.WaitHandle.WaitAll%2A> メソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="617c6-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="617c6-112">非同期操作のいずれかのセットが完了するまで待機しながらブロックするには、関連する <xref:System.IAsyncResult.AsyncWaitHandle%2A> オブジェクトを配列に格納し、<xref:System.Threading.WaitHandle.WaitAny%2A> メソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="617c6-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="617c6-113">例</span><span class="sxs-lookup"><span data-stu-id="617c6-113">Example</span></span>  
 <span data-ttu-id="617c6-114">次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム情報を取得するために、DNS クラスの非同期メソッドを使用してデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="617c6-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="617c6-115">例では、非同期操作に関連付けられた <xref:System.Threading.WaitHandle> を使用して、ブロックのデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="617c6-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="617c6-116">この方法を使用する場合は必要ないため、`null` (Visual Basic の場合は `Nothing`) は、<xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` と `stateObject` パラメーターに渡されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="617c6-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="617c6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="617c6-117">See also</span></span>

- [<span data-ttu-id="617c6-118">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="617c6-118">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="617c6-119">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="617c6-119">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
