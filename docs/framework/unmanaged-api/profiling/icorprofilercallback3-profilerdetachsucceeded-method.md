---
title: ICorProfilerCallback3::ProfilerDetachSucceeded メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
ms.openlocfilehash: b96a8930c24275546b0aac9fa650cf5447ef4ef2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865416"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="96f80-102">ICorProfilerCallback3::ProfilerDetachSucceeded メソッド</span><span class="sxs-lookup"><span data-stu-id="96f80-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="96f80-103">共通言語ランタイム (CLR: Common Language Runtime) がプロファイラー DLL をアンロードしようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="96f80-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96f80-104">構文</span><span class="sxs-lookup"><span data-stu-id="96f80-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="96f80-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="96f80-105">Return Value</span></span>  
 <span data-ttu-id="96f80-106">このコールバックからの戻り値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="96f80-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96f80-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="96f80-107">Remarks</span></span>  
 <span data-ttu-id="96f80-108">`ProfilerDetachSucceeded` コールバックは、すべてのスレッドでプロファイラーのコードが終了した後に発行されます。</span><span class="sxs-lookup"><span data-stu-id="96f80-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="96f80-109">このメソッドが呼び出された場合、プロファイラーは、そのデストラクターに適さない最後の段階のタスク (その UI またはログ コンポーネントの通知など) を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96f80-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="96f80-110">ただし、プロファイラーは、このコールバック中に CLR によって提供されるインターフェイス ( [ICorProfilerInfo](icorprofilerinfo-interface.md)インターフェイスや `IMetaData*` インターフェイスなど) で関数を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="96f80-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="96f80-111">CLR は Windows アプリケーション イベント ログに、デタッチ操作が成功したことを示すエントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="96f80-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="96f80-112">プロファイラーがこのコールバックから戻ると、CLR はプロファイラー オブジェクトを解放し、プロファイラー DLL をアンロードします。</span><span class="sxs-lookup"><span data-stu-id="96f80-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="96f80-113">したがって、プロファイラーは、コールバックから戻った後にプロファイラー DLL 内での実行を発生させるアクションを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="96f80-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="96f80-114">たとえば、プロファイラーは、スレッドを作成することも、タイマー コールバックを登録することもできません。</span><span class="sxs-lookup"><span data-stu-id="96f80-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96f80-115">要件</span><span class="sxs-lookup"><span data-stu-id="96f80-115">Requirements</span></span>  
 <span data-ttu-id="96f80-116">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96f80-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96f80-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="96f80-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96f80-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96f80-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96f80-119">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96f80-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f80-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="96f80-120">See also</span></span>

- [<span data-ttu-id="96f80-121">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96f80-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="96f80-122">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96f80-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="96f80-123">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="96f80-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="96f80-124">プロファイル</span><span class="sxs-lookup"><span data-stu-id="96f80-124">Profiling</span></span>](index.md)
