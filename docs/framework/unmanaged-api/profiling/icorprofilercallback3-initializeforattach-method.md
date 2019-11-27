---
title: ICorProfilerCallback3::InitializeForAttach メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
ms.openlocfilehash: 047516574595f9ffcd61360f51823da73a2f9733
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439521"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="503c8-102">ICorProfilerCallback3::InitializeForAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="503c8-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="503c8-103">アタッチ操作後にその状態を初期化する機会をプロファイラーに与えるために、共通言語ランタイム (CLR) により呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="503c8-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="503c8-104">構文</span><span class="sxs-lookup"><span data-stu-id="503c8-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="503c8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="503c8-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="503c8-106">[in] `ICorProfilerInfo*` インターフェイスへのインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="503c8-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="503c8-107">から`pvClientData` パラメーターで[IClrProfiling:: AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)メソッドに渡されるデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="503c8-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="503c8-108">このパラメーターが null の場合、`cbClientData` は 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="503c8-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="503c8-109">CLR は、`InitializeForAttach` から戻るとこのメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="503c8-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="503c8-110">[in] `pvClientData` がポイントするデータのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="503c8-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="503c8-111">コメント</span><span class="sxs-lookup"><span data-stu-id="503c8-111">Remarks</span></span>  
 <span data-ttu-id="503c8-112">CLR は `InitializeForAttach` を呼び出し、コールバックを要求できる機会をプロファイラーに与えます。</span><span class="sxs-lookup"><span data-stu-id="503c8-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="503c8-113">要件</span><span class="sxs-lookup"><span data-stu-id="503c8-113">Requirements</span></span>  
 <span data-ttu-id="503c8-114">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="503c8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="503c8-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="503c8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="503c8-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="503c8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="503c8-117">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="503c8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503c8-118">参照</span><span class="sxs-lookup"><span data-stu-id="503c8-118">See also</span></span>

- [<span data-ttu-id="503c8-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="503c8-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="503c8-120">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="503c8-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="503c8-121">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="503c8-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="503c8-122">プロファイル</span><span class="sxs-lookup"><span data-stu-id="503c8-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
