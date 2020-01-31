---
title: ICorProfilerCallback2::GarbageCollectionFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
ms.openlocfilehash: 30f2e675532848c2dbb1f055a0f1489cf3b2baa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865793"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="e50de-102">ICorProfilerCallback2::GarbageCollectionFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="e50de-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="e50de-103">ガベージコレクションが完了し、すべてのガベージコレクションコールバックが発行されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e50de-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e50de-104">構文</span><span class="sxs-lookup"><span data-stu-id="e50de-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e50de-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="e50de-105">Remarks</span></span>  
 <span data-ttu-id="e50de-106">`GarbageCollectionFinished` メソッドが呼び出されたときに、プロファイラーが最終的な場所のオブジェクトを検査するのは安全です。</span><span class="sxs-lookup"><span data-stu-id="e50de-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e50de-107">要件</span><span class="sxs-lookup"><span data-stu-id="e50de-107">Requirements</span></span>  
 <span data-ttu-id="e50de-108">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e50de-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e50de-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e50de-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e50de-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e50de-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e50de-111">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e50de-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e50de-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e50de-112">See also</span></span>

- [<span data-ttu-id="e50de-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e50de-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e50de-114">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e50de-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
