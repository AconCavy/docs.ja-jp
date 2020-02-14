---
title: overlappedFreeError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 8a0c72cf26ef8434719ff6661ef15a44f51c8740
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217257"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="d7546-102">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="d7546-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="d7546-103">オーバーラップされた操作が完了する前に `overlappedFreeError` メソッドが呼び出されると、<xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> マネージド デバッグ アシスタント (MDA) がアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="d7546-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d7546-104">現象</span><span class="sxs-lookup"><span data-stu-id="d7546-104">Symptoms</span></span>  
 <span data-ttu-id="d7546-105">アクセス違反またはガベージ コレクションされたヒープの破損。</span><span class="sxs-lookup"><span data-stu-id="d7546-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d7546-106">原因</span><span class="sxs-lookup"><span data-stu-id="d7546-106">Cause</span></span>  
 <span data-ttu-id="d7546-107">操作が完了する前に、オーバーラップされた構造が解放されました。</span><span class="sxs-lookup"><span data-stu-id="d7546-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="d7546-108">オーバーラップされたポインターを使用する関数は、解放された後に構造に書き込む可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d7546-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="d7546-109">その場合、現時点で別のオブジェクトがその領域を占有していることによってヒープが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d7546-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="d7546-110">オーバーラップされた操作が正常に起動しなかった場合、この MDA はエラーを発生しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="d7546-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d7546-111">解決策</span><span class="sxs-lookup"><span data-stu-id="d7546-111">Resolution</span></span>  
 <span data-ttu-id="d7546-112"><xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> メソッドを呼び出す前に、オーバーラップされた構造を使用している I/O 操作が必ず完了するようにします。</span><span class="sxs-lookup"><span data-stu-id="d7546-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d7546-113">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="d7546-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="d7546-114">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="d7546-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d7546-115">出力</span><span class="sxs-lookup"><span data-stu-id="d7546-115">Output</span></span>  
 <span data-ttu-id="d7546-116">この MDA のサンプル出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d7546-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="d7546-117">構成</span><span class="sxs-lookup"><span data-stu-id="d7546-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7546-118">参照</span><span class="sxs-lookup"><span data-stu-id="d7546-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d7546-119">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="d7546-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d7546-120">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="d7546-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
