---
title: ICorProfilerInfo::GetCurrentThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
ms.openlocfilehash: fa0fe827300a86a906a254292434e2a56ebb4a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498402"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="a8ead-102">ICorProfilerInfo::GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="a8ead-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="a8ead-103">マネージスレッドの場合、現在のスレッドの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="a8ead-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8ead-104">構文</span><span class="sxs-lookup"><span data-stu-id="a8ead-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8ead-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a8ead-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="a8ead-106">入出力返されたマネージスレッドの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a8ead-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8ead-107">解説</span><span class="sxs-lookup"><span data-stu-id="a8ead-107">Remarks</span></span>  
 <span data-ttu-id="a8ead-108">現在のスレッドが内部ランタイムスレッドまたはその他のアンマネージスレッドである場合、は `GetCurrentThreadID` CORPROF_E_NOT_MANAGED_THREAD を HRESULT として返し、パラメーターの戻り値は null になり `pThreadId` ます。</span><span class="sxs-lookup"><span data-stu-id="a8ead-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8ead-109">要件</span><span class="sxs-lookup"><span data-stu-id="a8ead-109">Requirements</span></span>  
 <span data-ttu-id="a8ead-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8ead-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8ead-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a8ead-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8ead-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8ead-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8ead-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ead-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ead-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8ead-114">See also</span></span>

- [<span data-ttu-id="a8ead-115">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a8ead-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
