---
title: disconnectedContext MDA
description: .NET で disconnectedContext マネージデバッグアシスタントを確認します。これは、CLR が切断されたアパートメントまたはコンテキストに移行しようとしたときに呼び出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
ms.openlocfilehash: 0b24aadefab7a7cb2a5294f25e674d188beec814
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416084"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="333c5-103">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="333c5-103">disconnectedContext MDA</span></span>
<span data-ttu-id="333c5-104">CLR が COM オブジェクトに関する要求を処理中に、切断しているアパートメントまたはコンテキストに遷移しようとすると、`disconnectedContext` マネージド デバッグ アシスタント (MDA) がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="333c5-104">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="333c5-105">現象</span><span class="sxs-lookup"><span data-stu-id="333c5-105">Symptoms</span></span>  
 <span data-ttu-id="333c5-106">[ランタイム呼び出し可能ラッパー](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) に対する呼び出しは、その呼び出しが存在する COM コンポーネントではなく、現在のアパートメントまたはコンテキスト内の基になる COM コンポーネントへ送られます。</span><span class="sxs-lookup"><span data-stu-id="333c5-106">Calls made on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="333c5-107">シングル スレッド アパートメント (STA) コンポーネントのように、COM コンポーネントがマルチスレッド化されていない場合、これが原因で破損やデータ損失が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="333c5-107">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="333c5-108">あるいは RCW 自体がプロキシである場合、呼び出しの結果として <xref:System.Runtime.InteropServices.COMException> がスローされ、HRESULT が RPC_E_WRONG_THREAD になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="333c5-108">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="333c5-109">原因</span><span class="sxs-lookup"><span data-stu-id="333c5-109">Cause</span></span>  
 <span data-ttu-id="333c5-110">OLE アパートメントまたはコンテキストは、CLR が遷移を試行しようとしたときに、既にシャットダウンしています。</span><span class="sxs-lookup"><span data-stu-id="333c5-110">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="333c5-111">ほとんどの場合これは、STA アパートメントが所有するすべての COM コンポーネントが完全に解放される前に、それらの STA アパートメントがシャットダウンしたことが原因で発生します。また、RCW でユーザー コードからの明示的な呼び出しが実行された結果として発生することや、CLR 自体が COM コンポーネントを操作している場合 (たとえば関連する RCW がガーベージ コレクションされているのに CRL が COM コンポーネントを解放する場合など) にも発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="333c5-111">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="333c5-112">解決策</span><span class="sxs-lookup"><span data-stu-id="333c5-112">Resolution</span></span>  
 <span data-ttu-id="333c5-113">この問題を回避するには、アプリケーションがアパートメントに存在するすべてのオブジェクトの処理を完了する前に、STA を所有するスレッドが強制終了しないようにします。</span><span class="sxs-lookup"><span data-stu-id="333c5-113">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="333c5-114">コンテキストの場合も同様に、アプリケーションがコンテキスト内部に存在するすべての COM コンポーネントの処理を完了するまでは、コンテキストがシャットダウンしないようにします。</span><span class="sxs-lookup"><span data-stu-id="333c5-114">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="333c5-115">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="333c5-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="333c5-116">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="333c5-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="333c5-117">接続していないコンテキストに関するデータを報告するだけです。</span><span class="sxs-lookup"><span data-stu-id="333c5-117">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="333c5-118">出力</span><span class="sxs-lookup"><span data-stu-id="333c5-118">Output</span></span>  
 <span data-ttu-id="333c5-119">非接続アパートメントまたはコンテキストのコンテキスト Cookie を報告します。</span><span class="sxs-lookup"><span data-stu-id="333c5-119">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="333c5-120">構成</span><span class="sxs-lookup"><span data-stu-id="333c5-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="333c5-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="333c5-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="333c5-122">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="333c5-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="333c5-123">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="333c5-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
