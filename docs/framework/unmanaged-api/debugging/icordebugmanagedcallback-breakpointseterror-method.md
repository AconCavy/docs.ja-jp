---
title: ICorDebugManagedCallback::BreakpointSetError メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
ms.openlocfilehash: 67d4972ee38a54d43b4a096847cc61fa3402b042
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788437"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="d0333-102">ICorDebugManagedCallback::BreakpointSetError メソッド</span><span class="sxs-lookup"><span data-stu-id="d0333-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="d0333-103">関数が just-in-time (JIT) コンパイルされる前に設定されたブレークポイントを共通言語ランタイムが正しくバインドできなかったことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="d0333-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0333-104">構文</span><span class="sxs-lookup"><span data-stu-id="d0333-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0333-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0333-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d0333-106">からバインドされていないブレークポイントを含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d0333-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d0333-107">からバインドされていないブレークポイントを含むスレッドを表す、表示スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d0333-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="d0333-108">からバインドされていないブレークポイントを表す ICorDebugBreakpoint オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d0333-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="d0333-109">からエラーを示す整数。</span><span class="sxs-lookup"><span data-stu-id="d0333-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0333-110">コメント</span><span class="sxs-lookup"><span data-stu-id="d0333-110">Remarks</span></span>  
 <span data-ttu-id="d0333-111">指定されたブレークポイントはヒットしません。</span><span class="sxs-lookup"><span data-stu-id="d0333-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="d0333-112">デバッガーは、非アクティブ化して再バインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0333-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0333-113">要件</span><span class="sxs-lookup"><span data-stu-id="d0333-113">Requirements</span></span>  
 <span data-ttu-id="d0333-114">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0333-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0333-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0333-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0333-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0333-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0333-117">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0333-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0333-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0333-118">See also</span></span>

- [<span data-ttu-id="d0333-119">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0333-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
