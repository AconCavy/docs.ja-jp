---
title: ICorDebugEval::GetResult メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
ms.openlocfilehash: 2d065d956319076d3b92eddafd4a2c25ffbfbac1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976266"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="0f29f-102">ICorDebugEval::GetResult メソッド</span><span class="sxs-lookup"><span data-stu-id="0f29f-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="0f29f-103">この評価の結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="0f29f-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f29f-104">構文</span><span class="sxs-lookup"><span data-stu-id="0f29f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f29f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f29f-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="0f29f-106">入出力評価が正常に完了した場合に、この評価の結果を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f29f-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f29f-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="0f29f-107">Remarks</span></span>  
 <span data-ttu-id="0f29f-108">`GetResult`メソッドは、評価が完了した後にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="0f29f-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="0f29f-109">評価が正常に完了し`ppResult`た場合は、結果を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f29f-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="0f29f-110">例外が発生して終了した場合は、スローされた例外が結果になります。</span><span class="sxs-lookup"><span data-stu-id="0f29f-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="0f29f-111">新しいオブジェクトの評価がの場合、結果は新しいオブジェクトへの参照になります。</span><span class="sxs-lookup"><span data-stu-id="0f29f-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f29f-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="0f29f-112">Requirements</span></span>  
 <span data-ttu-id="0f29f-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f29f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f29f-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f29f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f29f-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f29f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f29f-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f29f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
