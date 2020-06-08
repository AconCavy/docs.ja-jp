---
title: 'ICorProfilerInfo7:: Getinmemoryシンボルの長さメソッド'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 43d6bdeae5f522bd73b0bdf3a5c403ec69ee384c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495439"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="ae75e-102">ICorProfilerInfo7:: Getinmemoryシンボルの長さメソッド</span><span class="sxs-lookup"><span data-stu-id="ae75e-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="ae75e-103">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="ae75e-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="ae75e-104">メモリ内シンボルストリームの長さを返します。</span><span class="sxs-lookup"><span data-stu-id="ae75e-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae75e-105">構文</span><span class="sxs-lookup"><span data-stu-id="ae75e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae75e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae75e-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ae75e-107">からメモリ内ストリームを格納しているモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="ae75e-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="ae75e-108">Pcountシンボルバイト数</span><span class="sxs-lookup"><span data-stu-id="ae75e-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="ae75e-109">入出力`DWORD`メソッドから制御が戻るときに、ストリーム長がバイト単位で格納されている値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ae75e-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae75e-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="ae75e-110">Return Value</span></span>  
 <span data-ttu-id="ae75e-111">`S_OK`メモリストリームの長さがゼロ (0) であっても、このメソッドはを返します。</span><span class="sxs-lookup"><span data-stu-id="ae75e-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="ae75e-112">メソッドが `CORPROF_E_MODULE_IS_DYNAMIC` を使用して作成された場合、メソッドはを返し <xref:System.Reflection.Emit?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="ae75e-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae75e-113">解説</span><span class="sxs-lookup"><span data-stu-id="ae75e-113">Remarks</span></span>  
 <span data-ttu-id="ae75e-114">モジュールにメモリ内シンボルがある場合は、ストリームの長さがに配置され `pCountSymbolBytes` ます。</span><span class="sxs-lookup"><span data-stu-id="ae75e-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="ae75e-115">モジュールにメモリ内シンボルがない場合は `*pCountSymbolBytes = 0` 。</span><span class="sxs-lookup"><span data-stu-id="ae75e-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae75e-116">現在の実装では、リフレクションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ae75e-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="ae75e-117">モジュールがリフレクションを使用して作成された場合、メソッドは `CORPROF_E_MODULE_IS_DYNAMIC` を返します。</span><span class="sxs-lookup"><span data-stu-id="ae75e-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae75e-118">要件</span><span class="sxs-lookup"><span data-stu-id="ae75e-118">Requirements</span></span>  
 <span data-ttu-id="ae75e-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae75e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae75e-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae75e-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae75e-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae75e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae75e-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae75e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae75e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae75e-123">See also</span></span>

- [<span data-ttu-id="ae75e-124">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae75e-124">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
