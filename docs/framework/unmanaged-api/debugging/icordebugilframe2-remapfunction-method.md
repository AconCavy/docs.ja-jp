---
title: ICorDebugILFrame2::RemapFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
ms.openlocfilehash: f4f73b99b4cb48690a2a8611dbf5a5420adab5d4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794350"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="00ea8-102">ICorDebugILFrame2::RemapFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="00ea8-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="00ea8-103">新しい Microsoft 中間言語 (MSIL) オフセットを指定して、編集された関数を再マップします。</span><span class="sxs-lookup"><span data-stu-id="00ea8-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ea8-104">構文</span><span class="sxs-lookup"><span data-stu-id="00ea8-104">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00ea8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00ea8-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="00ea8-106">から命令ポインターが配置されるスタックフレームの新しい MSIL オフセット。</span><span class="sxs-lookup"><span data-stu-id="00ea8-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="00ea8-107">この値は、シーケンスポイントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="00ea8-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="00ea8-108">この値の有効性を保証するのは、呼び出し元の責任です。</span><span class="sxs-lookup"><span data-stu-id="00ea8-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="00ea8-109">たとえば、関数の境界の外側にある場合、MSIL オフセットは無効です。</span><span class="sxs-lookup"><span data-stu-id="00ea8-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00ea8-110">コメント</span><span class="sxs-lookup"><span data-stu-id="00ea8-110">Remarks</span></span>  
 <span data-ttu-id="00ea8-111">フレームの関数が編集されている場合、デバッガーは `RemapFunction` メソッドを呼び出して、フレームの関数の最新バージョンをスワップし、実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="00ea8-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="00ea8-112">コードの実行は、指定された MSIL オフセットから開始されます。</span><span class="sxs-lookup"><span data-stu-id="00ea8-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00ea8-113">`RemapFunction`を呼び出すと、[テキストボックス:: SetIP](icordebugilframe-setip-method.md)の呼び出しと同様に、スレッドのスタックトレースの生成に関連するすべてのデバッグインターフェイスがすぐに無効になります。</span><span class="sxs-lookup"><span data-stu-id="00ea8-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="00ea8-114">これらのインターフェイス[には](icordebugchain-interface.md)、次のようなインターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="00ea8-114">These interfaces include [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="00ea8-115">`RemapFunction` メソッドは、現在のフレームのコンテキストでのみ呼び出すことができ、次のいずれかの場合にのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="00ea8-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="00ea8-116">まだ継続していない[ICorDebugManagedCallback2:: FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md)コールバックを受信した後。</span><span class="sxs-lookup"><span data-stu-id="00ea8-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="00ea8-117">このフレームに対して、コードの実行が停止している間に、このフレームに対しては、[というエラーが発生し](icordebugmanagedcallback-editandcontinueremap-method.md)ます。</span><span class="sxs-lookup"><span data-stu-id="00ea8-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00ea8-118">要件</span><span class="sxs-lookup"><span data-stu-id="00ea8-118">Requirements</span></span>  
 <span data-ttu-id="00ea8-119">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00ea8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00ea8-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00ea8-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00ea8-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00ea8-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00ea8-122">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00ea8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
