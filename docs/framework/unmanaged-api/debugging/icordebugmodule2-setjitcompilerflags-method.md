---
title: ICorDebugModule2::SetJITCompilerFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: f73919634ba15dfd16694676d1389875fc2d79bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210190"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="624ee-102">ICorDebugModule2::SetJITCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="624ee-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="624ee-103">この ICorDebugModule2 の just-in-time (JIT) コンパイルを制御するフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="624ee-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="624ee-104">構文</span><span class="sxs-lookup"><span data-stu-id="624ee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="624ee-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="624ee-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="624ee-106">から[CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md)列挙値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="624ee-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="624ee-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="624ee-107">Remarks</span></span>  
 <span data-ttu-id="624ee-108">`dwFlags`値が無効な場合、 `SetJITCompilerFlags` メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="624ee-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="624ee-109">`SetJITCompilerFlags`メソッドを呼び出すことができるのは、このモジュールの " [LoadModule](icordebugmanagedcallback-loadmodule-method.md) " コールバックの中からだけです。</span><span class="sxs-lookup"><span data-stu-id="624ee-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="624ee-110">コールバックが配信された後に呼び出しを試みると `ICorDebugManagedCallback::LoadModule` 失敗します。</span><span class="sxs-lookup"><span data-stu-id="624ee-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="624ee-111">64ビットまたは Win9x プラットフォームでは、エディットコンティニュはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="624ee-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="624ee-112">したがって、 `SetJITCompilerFlags` で CORDEBUG_JIT_ENABLE_ENC フラグを設定して、これらの2つのプラットフォームのいずれかでメソッドを呼び出すと、 `dwFlags` `SetJITCompilerFlags` メソッドと、 [ICorDebugModule2:: Applychanges](icordebugmodule2-applychanges-method.md)などのエディットコンティニュに固有のすべてのメソッドが失敗します。</span><span class="sxs-lookup"><span data-stu-id="624ee-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="624ee-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="624ee-113">Requirements</span></span>  
 <span data-ttu-id="624ee-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="624ee-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="624ee-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="624ee-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="624ee-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="624ee-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="624ee-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="624ee-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
