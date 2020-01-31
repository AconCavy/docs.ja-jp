---
title: ICorDebugManagedCallback2::ExceptionUnwind メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: 482afd09ce370fb1247864b9ac2032ee7e3a1dca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788278"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="98e36-102">ICorDebugManagedCallback2::ExceptionUnwind メソッド</span><span class="sxs-lookup"><span data-stu-id="98e36-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="98e36-103">例外アンワインド処理中の状態通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="98e36-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e36-104">構文</span><span class="sxs-lookup"><span data-stu-id="98e36-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98e36-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98e36-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="98e36-106">から例外がスローされたスレッドを含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="98e36-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="98e36-107">から例外がスローされたスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="98e36-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="98e36-108">からアンワインドフェーズ中にコールバックによって通知されるイベントを指定する CorDebugExceptionUnwindCallbackType 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="98e36-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="98e36-109">から例外に関する追加情報を指定する[Cordebugexceptionflags](cordebugexceptionflags-enumeration.md)列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="98e36-109">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98e36-110">コメント</span><span class="sxs-lookup"><span data-stu-id="98e36-110">Remarks</span></span>  
 <span data-ttu-id="98e36-111">`ExceptionUnwind` は、例外処理プロセスのアンワインドフェーズ中にさまざまなポイントで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="98e36-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="98e36-112">1つの例外のアンワインド中に、`ExceptionUnwind` を複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="98e36-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="98e36-113">`dwEventType` = DEBUG_EXCEPTION_INTERCEPTED の場合、命令ポインターは、例外の原因となった命令の前 (これはいくつかの命令になります) に、スレッドのリーフフレームに配置されます。</span><span class="sxs-lookup"><span data-stu-id="98e36-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e36-114">要件</span><span class="sxs-lookup"><span data-stu-id="98e36-114">Requirements</span></span>  
 <span data-ttu-id="98e36-115">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98e36-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e36-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98e36-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98e36-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98e36-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98e36-118">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e36-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e36-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="98e36-119">See also</span></span>

- [<span data-ttu-id="98e36-120">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98e36-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="98e36-121">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98e36-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
