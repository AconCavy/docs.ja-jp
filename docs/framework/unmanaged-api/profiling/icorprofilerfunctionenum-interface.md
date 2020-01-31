---
title: ICorProfilerFunctionEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: add30952588ace0cbc80191617c37d7222cffee7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864493"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="9f58d-102">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f58d-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="9f58d-103">共通言語ランタイムの関数のコレクションを順番に反復処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9f58d-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f58d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9f58d-104">Methods</span></span>  
  
|<span data-ttu-id="9f58d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9f58d-105">Method</span></span>|<span data-ttu-id="9f58d-106">説明</span><span class="sxs-lookup"><span data-stu-id="9f58d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f58d-107">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="9f58d-107">Clone Method</span></span>](icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="9f58d-108">この `ICorProfilerFunctionEnum` インターフェイスのコピーへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9f58d-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="9f58d-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="9f58d-109">GetCount Method</span></span>](icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="9f58d-110">アプリケーションによって読み込まれたか、またはプロファイラーによって強制的に読み込まれた関数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="9f58d-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="9f58d-111">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="9f58d-111">Next Method</span></span>](icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="9f58d-112">関数のシーケンシャル コレクションから、列挙子の現在の位置以降にある、指定した数の隣接する関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="9f58d-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="9f58d-113">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="9f58d-113">Reset Method</span></span>](icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="9f58d-114">列挙子のカーソルをシーケンスの開始位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="9f58d-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="9f58d-115">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="9f58d-115">Skip Method</span></span>](icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="9f58d-116">指定した数の要素がスキップされるように、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="9f58d-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f58d-117">コメント</span><span class="sxs-lookup"><span data-stu-id="9f58d-117">Remarks</span></span>  
 <span data-ttu-id="9f58d-118">`ICorProfilerFunctionEnum` インターフェイスは列挙子です。</span><span class="sxs-lookup"><span data-stu-id="9f58d-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="9f58d-119">このインターフェイスにより、配列の受信側は、受信側に適した速度で送信側から要素をプルできます。</span><span class="sxs-lookup"><span data-stu-id="9f58d-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="9f58d-120">つまり、受信側は配列要素のフローを明示的に制御できるため、大きな配列をメソッド パラメーターとして渡す場合に関連する問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="9f58d-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="9f58d-121">`ICorProfilerFunctionEnum` は、既に JIT コンパイルされた関数を列挙しますが、この中に Ngen.exe で生成されたネイティブ イメージから読み込まれた関数は含まれません。</span><span class="sxs-lookup"><span data-stu-id="9f58d-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f58d-122">要件</span><span class="sxs-lookup"><span data-stu-id="9f58d-122">Requirements</span></span>  
 <span data-ttu-id="9f58d-123">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f58d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f58d-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9f58d-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9f58d-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f58d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f58d-126">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f58d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f58d-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f58d-127">See also</span></span>

- [<span data-ttu-id="9f58d-128">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f58d-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="9f58d-129">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f58d-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9f58d-130">EnumJITedFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="9f58d-130">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
