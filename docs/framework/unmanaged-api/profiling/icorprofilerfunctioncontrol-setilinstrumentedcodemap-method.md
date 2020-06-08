---
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: 738c98a0a37983faa71ea6e5eeaabb20639f604a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503141"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="220e5-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="220e5-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="220e5-103">指定した共通中間言語 (CIL) マップ エントリを使用して、指定される関数のコード マップを設定します。</span><span class="sxs-lookup"><span data-stu-id="220e5-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="220e5-104">構文</span><span class="sxs-lookup"><span data-stu-id="220e5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="220e5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="220e5-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="220e5-106">[in] マップ内のエントリの数。</span><span class="sxs-lookup"><span data-stu-id="220e5-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="220e5-107">[in] COR_IL_MAP エントリの呼び出し元が割り当てたアレイ。</span><span class="sxs-lookup"><span data-stu-id="220e5-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="220e5-108">これらのエントリの解釈は、 [ICorProfilerInfo:: SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md)メソッドの場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="220e5-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="220e5-109">解説</span><span class="sxs-lookup"><span data-stu-id="220e5-109">Remarks</span></span>  
 <span data-ttu-id="220e5-110">このメソッドを呼び出すことによってマッピングを設定すると、デバッガーは[ICorDebugILCode2:: GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md)を呼び出すことによってマッピングを取得できます。</span><span class="sxs-lookup"><span data-stu-id="220e5-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="220e5-111">またデバッガーは、スタック トレースおよび可変的な有効期間に対する IL オフセットを計算するときに、マッピングを内部で使用できます。</span><span class="sxs-lookup"><span data-stu-id="220e5-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="220e5-112">要件</span><span class="sxs-lookup"><span data-stu-id="220e5-112">Requirements</span></span>  
 <span data-ttu-id="220e5-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="220e5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="220e5-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="220e5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="220e5-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="220e5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="220e5-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="220e5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="220e5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="220e5-117">See also</span></span>

- [<span data-ttu-id="220e5-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="220e5-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
