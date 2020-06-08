---
title: ICorProfilerCallback2::GarbageCollectionStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
ms.openlocfilehash: f025f4c0bc0ec8e11decddcdf64be50f68955266
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499806"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="fc5e0-102">ICorProfilerCallback2::GarbageCollectionStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="fc5e0-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="fc5e0-103">ガベージコレクションが開始されたことをコードプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc5e0-104">構文</span><span class="sxs-lookup"><span data-stu-id="fc5e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc5e0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc5e0-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="fc5e0-106">から配列内のエントリの合計数 `generationCollected` 。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="fc5e0-107">からブール値の配列 `true` 。配列インデックスに対応するジェネレーションがこのガベージコレクションによって収集されている場合は、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="fc5e0-108">配列は、生成を示す[COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md)列挙体の値によってインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="fc5e0-109">からガベージコレクションが発生した理由を示す[COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md)列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-109">[in] A value of the [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc5e0-110">解説</span><span class="sxs-lookup"><span data-stu-id="fc5e0-110">Remarks</span></span>  
 <span data-ttu-id="fc5e0-111">このガベージコレクションに関連するすべてのコールバックは、 `GarbageCollectionStarted` コールバックとそれに対応する[ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)コールバックの間で発生します。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="fc5e0-112">これらのコールバックは、同じスレッドでは実行されません。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="fc5e0-113">プロファイラーは、コールバック中に元の場所のオブジェクトを検査するのが安全です `GarbageCollectionStarted` 。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="fc5e0-114">ガベージコレクターは、から戻った後にオブジェクトの移動を開始し `GarbageCollectionStarted` ます。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="fc5e0-115">プロファイラーは、このコールバックから戻った後、コールバックを受信するまで、すべてのオブジェクト Id が無効であると見なす必要があり `ICorProfilerCallback2::GarbageCollectionFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc5e0-116">要件</span><span class="sxs-lookup"><span data-stu-id="fc5e0-116">Requirements</span></span>  
 <span data-ttu-id="fc5e0-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc5e0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc5e0-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc5e0-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc5e0-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc5e0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc5e0-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc5e0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc5e0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc5e0-121">See also</span></span>

- [<span data-ttu-id="fc5e0-122">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc5e0-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="fc5e0-123">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc5e0-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
