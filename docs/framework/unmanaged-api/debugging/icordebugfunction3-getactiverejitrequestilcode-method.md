---
title: ICorDebugFunction3::GetActiveReJitRequestILCode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: db9ce146da1d6fee8db32a0be43903eaa61e52de
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501756"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="4e720-102">ICorDebugFunction3::GetActiveReJitRequestILCode メソッド</span><span class="sxs-lookup"><span data-stu-id="4e720-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="4e720-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="4e720-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4e720-104">アクティブな ReJIT 要求から IL を含む、[コード](icordebugilcode-interface.md)へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4e720-104">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e720-105">構文</span><span class="sxs-lookup"><span data-stu-id="4e720-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e720-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4e720-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="4e720-107">アクティブな ReJIT 要求からの、IL へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4e720-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e720-108">解説</span><span class="sxs-lookup"><span data-stu-id="4e720-108">Remarks</span></span>  
 <span data-ttu-id="4e720-109">この `ICorDebugFunction3` オブジェクトによって表示されるメソッドがアクティブな ReJIT 要求を持っている場合、`ppReJitedILCode` は IL へのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="4e720-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="4e720-110">一般的なケースであるアクティブな要求がない場合、 `ppReJitedILCode` は**null**になります。</span><span class="sxs-lookup"><span data-stu-id="4e720-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="4e720-111">ReJIT 要求は、 [ICorProfilerCallback4:: GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md)メソッドの呼び出しから実行が戻った直後にアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="4e720-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="4e720-112">これは、まだ JIT コンパイルされていない可能性があり、スレッドはコードの元のバージョンで実行中の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4e720-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="4e720-113">ReJIT 要求は、 [ICorProfilerInfo4:: RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md)メソッドへのプロファイラーの呼び出し中に非アクティブになります。</span><span class="sxs-lookup"><span data-stu-id="4e720-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="4e720-114">LI が戻された後であっても、スレッドは JIT 再コンパイル (ReJIT) されたコードで実行中の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4e720-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e720-115">要件</span><span class="sxs-lookup"><span data-stu-id="4e720-115">Requirements</span></span>  
 <span data-ttu-id="4e720-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e720-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e720-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e720-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e720-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e720-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e720-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e720-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e720-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e720-120">See also</span></span>

- [<span data-ttu-id="4e720-121">ICorDebugFunction3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4e720-121">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="4e720-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4e720-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4e720-123">ReJIT: ハウツーガイド</span><span class="sxs-lookup"><span data-stu-id="4e720-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
