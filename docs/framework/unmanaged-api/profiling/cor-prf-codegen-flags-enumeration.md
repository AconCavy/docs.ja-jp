---
title: COR_PRF_CODEGEN_FLAGS 列挙体
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: c49bdcb9345960bce018cefd4443948f997c7267
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428363"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="8066b-102">COR_PRF_CODEGEN_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="8066b-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="8066b-103">[ICorProfilerFunctionControl:: SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)メソッドで設定できるコード生成フラグを定義します。</span><span class="sxs-lookup"><span data-stu-id="8066b-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8066b-104">構文</span><span class="sxs-lookup"><span data-stu-id="8066b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="8066b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="8066b-105">Members</span></span>  
  
|<span data-ttu-id="8066b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8066b-106">Member</span></span>|<span data-ttu-id="8066b-107">説明</span><span class="sxs-lookup"><span data-stu-id="8066b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="8066b-108">関数は、この関数の本体にインライン展開されません。</span><span class="sxs-lookup"><span data-stu-id="8066b-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="8066b-109">ただし、関数自体は、その呼び出し元にインライン展開される場合があります。</span><span class="sxs-lookup"><span data-stu-id="8066b-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="8066b-110">この関数の本体では、すべての最適化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="8066b-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="8066b-111">ただし、関数自体を呼び出し元にインライン化することはできます。</span><span class="sxs-lookup"><span data-stu-id="8066b-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8066b-112">コメント</span><span class="sxs-lookup"><span data-stu-id="8066b-112">Remarks</span></span>  
 <span data-ttu-id="8066b-113">`COR_PRF_CODEGEN_FLAGS` 列挙体は、プロファイラーが JIT 再コンパイル関数のコード生成を制御できるようにするために、 [ICorProfilerFunctionControl:: SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="8066b-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8066b-114">要件</span><span class="sxs-lookup"><span data-stu-id="8066b-114">Requirements</span></span>  
 <span data-ttu-id="8066b-115">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8066b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8066b-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8066b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8066b-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8066b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8066b-118">**.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8066b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8066b-119">参照</span><span class="sxs-lookup"><span data-stu-id="8066b-119">See also</span></span>

- [<span data-ttu-id="8066b-120">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="8066b-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
