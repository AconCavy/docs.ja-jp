---
title: ICorProfilerFunctionControl インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
ms.openlocfilehash: 177127c8c53e4fee31f7007d04c49cc337cca458
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498727"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="e7ce0-102">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7ce0-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="e7ce0-103">特定のメソッドを再コンパイルする時に JIT コンパイラーがコードをどのように生成するかを制御するために、コード プロファイラーが共通言語ランタイム (CLR) と通信できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e7ce0-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7ce0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e7ce0-104">Methods</span></span>  
  
|<span data-ttu-id="e7ce0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e7ce0-105">Method</span></span>|<span data-ttu-id="e7ce0-106">説明</span><span class="sxs-lookup"><span data-stu-id="e7ce0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7ce0-107">SetCodegenFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="e7ce0-107">SetCodegenFlags Method</span></span>](icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="e7ce0-108">[COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md)列挙型の1つ以上のフラグを設定して、JUST-IN-TIME (JIT) 再コンパイル関数のコード生成を制御します。</span><span class="sxs-lookup"><span data-stu-id="e7ce0-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="e7ce0-109">SetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="e7ce0-109">SetILFunctionBody Method</span></span>](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="e7ce0-110">メソッドの中間共通言語 (CIL) 本体を置換します。</span><span class="sxs-lookup"><span data-stu-id="e7ce0-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="e7ce0-111">SetILInstrumentedCodeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="e7ce0-111">SetILInstrumentedCodeMap Method</span></span>](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="e7ce0-112">指定した共通中間言語 (CIL) マップ エントリを使用して、指定される関数のコード マップを設定します。</span><span class="sxs-lookup"><span data-stu-id="e7ce0-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7ce0-113">解説</span><span class="sxs-lookup"><span data-stu-id="e7ce0-113">Remarks</span></span>  
 <span data-ttu-id="e7ce0-114">`ICorProfilerFunctionControl` インターフェイスは、単一の再コンパイルされた関数に対してコード生成を制御するためにメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e7ce0-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="e7ce0-115">プロファイラーは、 [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md)コールバックを使用して、このインターフェイスのインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e7ce0-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="e7ce0-116">`ICorProfilerFunctionControl` の各インスタンスは一つの関数の全てのインスタンスを制御します。</span><span class="sxs-lookup"><span data-stu-id="e7ce0-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7ce0-117">要件</span><span class="sxs-lookup"><span data-stu-id="e7ce0-117">Requirements</span></span>  
 <span data-ttu-id="e7ce0-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ce0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7ce0-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7ce0-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7ce0-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7ce0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7ce0-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7ce0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ce0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7ce0-122">See also</span></span>

- [<span data-ttu-id="e7ce0-123">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7ce0-123">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="e7ce0-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7ce0-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e7ce0-125">EnumJITedFunctions2 メソッド</span><span class="sxs-lookup"><span data-stu-id="e7ce0-125">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)
