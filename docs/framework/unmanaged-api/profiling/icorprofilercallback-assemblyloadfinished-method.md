---
title: ICorProfilerCallback::AssemblyLoadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: 33b72c8d089e5b335069fe465987086dfa1243bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445174"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="29295-102">ICorProfilerCallback::AssemblyLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="29295-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="29295-103">Notifies the profiler that an assembly has finished loading.</span><span class="sxs-lookup"><span data-stu-id="29295-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29295-104">構文</span><span class="sxs-lookup"><span data-stu-id="29295-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29295-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29295-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="29295-106">[in] Identifies the assembly that was loaded.</span><span class="sxs-lookup"><span data-stu-id="29295-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="29295-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span><span class="sxs-lookup"><span data-stu-id="29295-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29295-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="29295-108">Remarks</span></span>  
 <span data-ttu-id="29295-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span><span class="sxs-lookup"><span data-stu-id="29295-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="29295-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="29295-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="29295-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="29295-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="29295-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span><span class="sxs-lookup"><span data-stu-id="29295-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29295-113">［要件］</span><span class="sxs-lookup"><span data-stu-id="29295-113">Requirements</span></span>  
 <span data-ttu-id="29295-114">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29295-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29295-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29295-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29295-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29295-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29295-117">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29295-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29295-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="29295-118">See also</span></span>

- [<span data-ttu-id="29295-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29295-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
