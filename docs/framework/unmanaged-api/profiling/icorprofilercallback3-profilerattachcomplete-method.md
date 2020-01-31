---
title: ICorProfilerCallback3::ProfilerAttachComplete メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: 8168f6f1079ec34b9fb53a485da0f32175446719
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865429"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="ffc85-102">ICorProfilerCallback3::ProfilerAttachComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="ffc85-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="ffc85-103">プロファイラーが[ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md)および[ICorProfilerInfo3:: enummodules](icorprofilerinfo3-enummodules-method.md)のキャッチアップメソッドを呼び出せるようになったことを示すために、共通言語ランタイム (CLR) によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ffc85-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffc85-104">構文</span><span class="sxs-lookup"><span data-stu-id="ffc85-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ffc85-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="ffc85-105">Remarks</span></span>  
 <span data-ttu-id="ffc85-106">`ProfilerAttachComplete` コールバックは、 [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md)メソッドが呼び出された後に発行されます。</span><span class="sxs-lookup"><span data-stu-id="ffc85-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="ffc85-107">これは、次のことを示します。</span><span class="sxs-lookup"><span data-stu-id="ffc85-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="ffc85-108">`InitializeForAttach` でプロファイラーによって要求されたコールバックがアクティブ化されました。</span><span class="sxs-lookup"><span data-stu-id="ffc85-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="ffc85-109">プロファイラーは、通知されないことを心配せずに、関連付けられた ID でキャッチアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ffc85-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="ffc85-110">CLR はこのコールバックからの戻り値を無視します。</span><span class="sxs-lookup"><span data-stu-id="ffc85-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffc85-111">要件</span><span class="sxs-lookup"><span data-stu-id="ffc85-111">Requirements</span></span>  
 <span data-ttu-id="ffc85-112">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffc85-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffc85-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ffc85-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ffc85-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffc85-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffc85-115">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffc85-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc85-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffc85-116">See also</span></span>

- [<span data-ttu-id="ffc85-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffc85-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ffc85-118">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffc85-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ffc85-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffc85-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ffc85-120">プロファイル</span><span class="sxs-lookup"><span data-stu-id="ffc85-120">Profiling</span></span>](index.md)
