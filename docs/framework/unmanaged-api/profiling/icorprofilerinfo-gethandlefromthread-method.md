---
title: ICorProfilerInfo::GetHandleFromThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 419195d9450bf07e5ad8c7cedcac76e175137c96
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498220"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="d5876-102">ICorProfilerInfo::GetHandleFromThread メソッド</span><span class="sxs-lookup"><span data-stu-id="d5876-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="d5876-103">スレッドの ID を Win32 スレッドハンドルにマップします。</span><span class="sxs-lookup"><span data-stu-id="d5876-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5876-104">構文</span><span class="sxs-lookup"><span data-stu-id="d5876-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5876-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5876-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d5876-106">から割り当てられるスレッド ID。</span><span class="sxs-lookup"><span data-stu-id="d5876-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="d5876-107">入出力Win32 スレッドハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d5876-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5876-108">解説</span><span class="sxs-lookup"><span data-stu-id="d5876-108">Remarks</span></span>  
 <span data-ttu-id="d5876-109">プロファイラーは、 `DuplicateHandle` 使用する前にハンドルで Win32 関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5876-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5876-110">要件</span><span class="sxs-lookup"><span data-stu-id="d5876-110">Requirements</span></span>  
 <span data-ttu-id="d5876-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5876-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5876-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5876-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5876-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5876-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5876-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5876-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5876-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5876-115">See also</span></span>

- [<span data-ttu-id="d5876-116">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5876-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
