---
title: ICorProfilerInfo::GetILFunctionBodyAllocator メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
ms.openlocfilehash: 967f38add9ae5996c6ac33388203b55161a84e39
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498272"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="4d379-102">ICorProfilerInfo::GetILFunctionBodyAllocator メソッド</span><span class="sxs-lookup"><span data-stu-id="4d379-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="4d379-103">Microsoft 中間言語 (MSIL) コードでメソッドの本体を交換するために使用されるメモリを割り当てるメソッドを提供するインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d379-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d379-104">構文</span><span class="sxs-lookup"><span data-stu-id="4d379-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d379-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4d379-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="4d379-106">からメソッドが存在するモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="4d379-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="4d379-107">入出力メモリを割り当てるメソッドを提供する[Imethodmalloc](imethodmalloc-interface.md)インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4d379-107">[out] A pointer to an [IMethodMalloc](imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d379-108">解説</span><span class="sxs-lookup"><span data-stu-id="4d379-108">Remarks</span></span>  
 <span data-ttu-id="4d379-109">MSIL コードのメソッド本体は、読み込まれたモジュールに対して相対的な相対仮想アドレス (RVA) として配置されている必要があります。これは、モジュールが 4 GB 以内に続くことを意味します。</span><span class="sxs-lookup"><span data-stu-id="4d379-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="4d379-110">ツールがメソッドの本体を簡単に交換できるようにするために、メソッドは、 `GetILFunctionBodyAllocator` その範囲内でメモリが割り当てられるようにします。</span><span class="sxs-lookup"><span data-stu-id="4d379-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d379-111">要件</span><span class="sxs-lookup"><span data-stu-id="4d379-111">Requirements</span></span>  
 <span data-ttu-id="4d379-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d379-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d379-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4d379-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d379-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d379-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d379-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d379-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d379-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d379-116">See also</span></span>

- [<span data-ttu-id="4d379-117">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d379-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
