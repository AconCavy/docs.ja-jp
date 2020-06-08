---
title: ICorProfilerInfo::SetILFunctionBody メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: 462fc7222243f8cad4e1d03d1717eedace549836
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502939"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="73363-102">ICorProfilerInfo::SetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="73363-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="73363-103">指定したモジュール内の指定した関数の本体を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="73363-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73363-104">構文</span><span class="sxs-lookup"><span data-stu-id="73363-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73363-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="73363-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="73363-106">から関数が存在するモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="73363-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="73363-107">から本文の置換対象となる関数のトークン。</span><span class="sxs-lookup"><span data-stu-id="73363-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="73363-108">から関数の新しいヘッダー。</span><span class="sxs-lookup"><span data-stu-id="73363-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73363-109">解説</span><span class="sxs-lookup"><span data-stu-id="73363-109">Remarks</span></span>  
 <span data-ttu-id="73363-110">メソッドは、 `SetILFunctionBody` メタデータ内の関数の相対仮想アドレスを置き換えて、新しい関数本体をポイントし、必要に応じて内部データ構造を調整します。</span><span class="sxs-lookup"><span data-stu-id="73363-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="73363-111">メソッドは、 `SetILFunctionBody` just-in-time (JIT) コンパイラによってコンパイルされたことがない関数に対してのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="73363-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="73363-112">[ICorProfilerInfo:: GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)メソッドを使用して、新しいメソッドの領域を割り当て、バッファーに互換性があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="73363-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73363-113">要件</span><span class="sxs-lookup"><span data-stu-id="73363-113">Requirements</span></span>  
 <span data-ttu-id="73363-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73363-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73363-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73363-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73363-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73363-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73363-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73363-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73363-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="73363-118">See also</span></span>

- [<span data-ttu-id="73363-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73363-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
