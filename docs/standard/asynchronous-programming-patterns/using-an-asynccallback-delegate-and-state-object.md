---
title: AsyncCallback デリゲートおよび状態オブジェクトの使用
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: c7bd0a7606b5f93289cf39d33794457265e7e453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094602"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="95236-102">AsyncCallback デリゲートおよび状態オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="95236-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="95236-103"><xref:System.AsyncCallback> デリゲートを使用し、別個のスレッドで非同期操作の結果を処理するとき、状態オブジェクトを使用してコールバック間で情報を渡し、最終的な結果を取得できます。</span><span class="sxs-lookup"><span data-stu-id="95236-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="95236-104">このトピックでは、「[AsyncCallback デリゲートの使用による非同期操作の終了](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)」の例をさらに展開することでそれを実践します。</span><span class="sxs-lookup"><span data-stu-id="95236-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95236-105">例</span><span class="sxs-lookup"><span data-stu-id="95236-105">Example</span></span>  
 <span data-ttu-id="95236-106">次のコード例は、ユーザー指定のコンピューターのドメイン ネーム システム (DNS) 情報を取得するために、<xref:System.Net.Dns> クラスの非同期メソッドを使用してデモを実行します。</span><span class="sxs-lookup"><span data-stu-id="95236-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="95236-107">この例では、`HostRequest` クラスを定義して使用し、状態情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="95236-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="95236-108">`HostRequest` オブジェクトは、ユーザーがコンピューター名を入力するたびに作成されます。</span><span class="sxs-lookup"><span data-stu-id="95236-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="95236-109">このオブジェクトは <xref:System.Net.Dns.BeginGetHostByName%2A> メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="95236-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="95236-110">`ProcessDnsInformation` メソッドは、要求が完了するたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="95236-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="95236-111">`HostRequest` オブジェクトは <xref:System.IAsyncResult.AsyncState%2A> プロパティを利用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="95236-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="95236-112">`ProcessDnsInformation` メソッドは `HostRequest` オブジェクトを使用し、要求により返された <xref:System.Net.IPHostEntry> か、スローされた <xref:System.Net.Sockets.SocketException> を格納します。</span><span class="sxs-lookup"><span data-stu-id="95236-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="95236-113">要求がすべて完了すると、アプリケーションは `HostRequest` オブジェクトを反復処理し、DNS 情報か <xref:System.Net.Sockets.SocketException> エラー メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="95236-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="95236-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="95236-114">See also</span></span>

- [<span data-ttu-id="95236-115">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="95236-115">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="95236-116">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="95236-116">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="95236-117">AsyncCallback デリゲートの使用による非同期操作の終了</span><span class="sxs-lookup"><span data-stu-id="95236-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
