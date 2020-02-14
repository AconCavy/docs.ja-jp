---
title: dirtyCastAndCallOnInterface MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
ms.openlocfilehash: 6e4f0074958e8a6a8ca322968e9c29e89481c0c8
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216511"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="a2ad2-102">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="a2ad2-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="a2ad2-103">`dirtyCastAndCallOnInterface` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、vtable を使用して事前バインディングされた呼び出しが、遅延バインディング専用とマークされたクラス インターフェイスで試行されたときにアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a2ad2-104">現象</span><span class="sxs-lookup"><span data-stu-id="a2ad2-104">Symptoms</span></span>  
 <span data-ttu-id="a2ad2-105">COM 経由で CLR への事前バインディングされた呼び出しが実行されると、アプリケーションはアクセス違反をスローするか、予期しない動作に発生します。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a2ad2-106">原因</span><span class="sxs-lookup"><span data-stu-id="a2ad2-106">Cause</span></span>  
 <span data-ttu-id="a2ad2-107">コードは、遅延バインディング専用のクラス インターフェイス経由で、vtable を使用して事前バインディングされた呼び出しを試行しています。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="a2ad2-108">既定では、クラス インターフェイスは遅延バインディング専用として識別されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="a2ad2-109">また、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性に <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> 値 (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`) が設定されている場合も、遅延バインディングとして識別されます。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a2ad2-110">解決策</span><span class="sxs-lookup"><span data-stu-id="a2ad2-110">Resolution</span></span>  
 <span data-ttu-id="a2ad2-111">推奨される解決策としては、COM で使用するための明示的なインターフェイスを定義し、自動生成されるクラス インターフェイスを通してではなく、このインターフェイスを通して、COM クライアント呼び出しを実行するようにする方法があります。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="a2ad2-112">代わりに、`IDispatch` を介して、COM からの呼び出しを遅延バインディングされた呼び出しに変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="a2ad2-113">事前バインディングされた呼び出しを COM から実行できるように、クラスを <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) として識別することもできます。ただし、「<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>」に記載されているバージョン管理の制約から、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute> を使用しないことを強く推奨します。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a2ad2-114">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="a2ad2-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="a2ad2-115">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="a2ad2-116">遅延バインディングされたインターフェイス上の事前バインディングされた呼び出しに関するデータを報告するだけです。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a2ad2-117">出力</span><span class="sxs-lookup"><span data-stu-id="a2ad2-117">Output</span></span>  
 <span data-ttu-id="a2ad2-118">事前バインディングでアクセスされたメソッド名またはフィールド名です。</span><span class="sxs-lookup"><span data-stu-id="a2ad2-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a2ad2-119">構成</span><span class="sxs-lookup"><span data-stu-id="a2ad2-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2ad2-120">参照</span><span class="sxs-lookup"><span data-stu-id="a2ad2-120">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="a2ad2-121">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="a2ad2-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
