---
title: ICorProfilerCallback4::MovedReferences2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
ms.openlocfilehash: 37d5f5e8294bb87a8796d6dcae046864904b096b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439377"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="911df-102">ICorProfilerCallback4::MovedReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="911df-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="911df-103">圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトの新しいレイアウトを報告するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="911df-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="911df-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="911df-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="911df-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span><span class="sxs-lookup"><span data-stu-id="911df-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="911df-106">構文</span><span class="sxs-lookup"><span data-stu-id="911df-106">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="911df-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="911df-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="911df-108">[in] 圧縮ガベージ コレクションを実行した後に移動される、隣接したオブジェクトのブロック数。</span><span class="sxs-lookup"><span data-stu-id="911df-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="911df-109">つまり、`cMovedObjectIDRanges` の値は `oldObjectIDRangeStart`、`newObjectIDRangeStart`、および `cObjectIDRangeLength` 配列の合計サイズです。</span><span class="sxs-lookup"><span data-stu-id="911df-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="911df-110">`MovedReferences2` の次の 3 つの引数は並列配列です。</span><span class="sxs-lookup"><span data-stu-id="911df-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="911df-111">つまり、`oldObjectIDRangeStart[i]`、`newObjectIDRangeStart[i]`、`cObjectIDRangeLength[i]` はすべて、隣接するオブジェクトの同じブロックを対象としています。</span><span class="sxs-lookup"><span data-stu-id="911df-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="911df-112">[in] それぞれがメモリ内の有効な隣接オブジェクト ブロックの古い (ガベージ コレクション実行前の) 開始アドレスを表す、`ObjectID` 値の配列。</span><span class="sxs-lookup"><span data-stu-id="911df-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="911df-113">[in] それぞれがメモリ内の有効な隣接オブジェクト ブロックの新しい (ガベージ コレクション実行後の) 開始アドレスを表す、`ObjectID` 値の配列。</span><span class="sxs-lookup"><span data-stu-id="911df-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="911df-114">[in] それぞれがメモリ内の隣接オブジェクト ブロックのサイズを表す、整数の配列。</span><span class="sxs-lookup"><span data-stu-id="911df-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="911df-115">サイズは、`oldObjectIDRangeStart` および `newObjectIDRangeStart` 配列内の参照される各ブロックに対して指定します。</span><span class="sxs-lookup"><span data-stu-id="911df-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="911df-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="911df-116">Remarks</span></span>  
 <span data-ttu-id="911df-117">圧縮ガベージ コレクターは、無効なオブジェクトによって占有されているメモリを解放し、解放された領域を圧縮します。</span><span class="sxs-lookup"><span data-stu-id="911df-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="911df-118">その結果、ヒープ内で有効なオブジェクトが移動され、以前の通知で配布された `ObjectID` の値が変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="911df-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="911df-119">既存の `ObjectID` の値 (`oldObjectID`) が次の範囲内にあるとします。</span><span class="sxs-lookup"><span data-stu-id="911df-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="911df-120">この場合、範囲の開始からオブジェクトの開始までのオフセットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="911df-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="911df-121">`i` の値が次の範囲内にあるとします。</span><span class="sxs-lookup"><span data-stu-id="911df-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="911df-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="911df-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="911df-123">この場合、新しい `ObjectID` は次のように計算できます。</span><span class="sxs-lookup"><span data-stu-id="911df-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="911df-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="911df-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="911df-125">ガーベッジ コレクションでオブジェクトが古い場所から新しい場所へ移動中の可能性があるため、コールバックの間は `MovedReferences2` によって渡される `ObjectID` 値はすべて無効です。</span><span class="sxs-lookup"><span data-stu-id="911df-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="911df-126">このため、`MovedReferences2` 呼び出しの間、プロファイラーはオブジェクトを検査するべきではありません。</span><span class="sxs-lookup"><span data-stu-id="911df-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="911df-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span><span class="sxs-lookup"><span data-stu-id="911df-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="911df-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span><span class="sxs-lookup"><span data-stu-id="911df-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="911df-129">プロファイラーは HRESULT を返すことがあり、これは `MovedReferences2` メソッドの失敗を示し、2 番目のメソッドが呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="911df-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="911df-130">［要件］</span><span class="sxs-lookup"><span data-stu-id="911df-130">Requirements</span></span>  
 <span data-ttu-id="911df-131">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="911df-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="911df-132">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="911df-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="911df-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="911df-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="911df-134">**.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="911df-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911df-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="911df-135">See also</span></span>

- [<span data-ttu-id="911df-136">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="911df-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="911df-137">MovedReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="911df-137">MovedReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="911df-138">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="911df-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="911df-139">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="911df-139">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="911df-140">プロファイル</span><span class="sxs-lookup"><span data-stu-id="911df-140">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
