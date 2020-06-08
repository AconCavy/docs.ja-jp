---
title: FunctionEnter3 関数
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: b435e1a3504dd623421f977ffc48264f8b0dcb5a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500703"
---
# <a name="functionenter3-function"></a><span data-ttu-id="f15fc-102">FunctionEnter3 関数</span><span class="sxs-lookup"><span data-stu-id="f15fc-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="f15fc-103">コントロールが関数に渡されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f15fc-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="f15fc-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f15fc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f15fc-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="f15fc-106">\[in] コントロールが渡される関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="f15fc-106">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f15fc-107">解説</span><span class="sxs-lookup"><span data-stu-id="f15fc-107">Remarks</span></span>  
 <span data-ttu-id="f15fc-108">`FunctionEnter3`コールバック関数は、関数が呼び出されていることをプロファイラーに通知しますが、引数の検査はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f15fc-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="f15fc-109">[ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 メソッド](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)を使用して、この関数の実装を登録します。</span><span class="sxs-lookup"><span data-stu-id="f15fc-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="f15fc-110">`FunctionEnter3`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f15fc-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="f15fc-111">実装では、ストレージクラス属性を使用する必要があり `__declspec(naked)` ます。</span><span class="sxs-lookup"><span data-stu-id="f15fc-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="f15fc-112">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="f15fc-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="f15fc-113">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f15fc-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="f15fc-114">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f15fc-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f15fc-115">要件</span><span class="sxs-lookup"><span data-stu-id="f15fc-115">Requirements</span></span>  
 <span data-ttu-id="f15fc-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f15fc-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f15fc-117">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="f15fc-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f15fc-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f15fc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f15fc-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f15fc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15fc-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f15fc-120">See also</span></span>

- [<span data-ttu-id="f15fc-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="f15fc-121">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="f15fc-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="f15fc-122">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="f15fc-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f15fc-123">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="f15fc-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f15fc-124">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="f15fc-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f15fc-125">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="f15fc-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="f15fc-126">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="f15fc-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f15fc-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="f15fc-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="f15fc-128">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="f15fc-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="f15fc-129">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="f15fc-130">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="f15fc-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
