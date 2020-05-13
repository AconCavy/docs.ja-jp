---
title: ICorDebugILCode::GetEHClauses メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
ms.openlocfilehash: e1fd68cd079b381d941d416831133c54e49ac48a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210385"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="52090-102">ICorDebugILCode::GetEHClauses メソッド</span><span class="sxs-lookup"><span data-stu-id="52090-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="52090-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="52090-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="52090-104">この中間言語 (IL) に対して定義されている例外処理 (EH) 句のリストへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="52090-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52090-105">構文</span><span class="sxs-lookup"><span data-stu-id="52090-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52090-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52090-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="52090-107">[入力] `clauses` 配列の記憶容量。</span><span class="sxs-lookup"><span data-stu-id="52090-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="52090-108">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52090-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="52090-109">[out] 情報が `clauses` アレイに書き込まれる場合に、対象となる句の数。</span><span class="sxs-lookup"><span data-stu-id="52090-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="52090-110">句</span><span class="sxs-lookup"><span data-stu-id="52090-110">clauses</span></span>  
 <span data-ttu-id="52090-111">入出力この IL に対して定義されている例外処理句に関する情報を格納する[CorDebugEHClause](cordebugehclause-structure.md)オブジェクトの配列。</span><span class="sxs-lookup"><span data-stu-id="52090-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52090-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="52090-112">Remarks</span></span>  
 <span data-ttu-id="52090-113">`cClauses`が0で、 `pcClauses` が**null**以外の場合、 `pcClauses` は使用可能な例外処理句の数に設定されます。</span><span class="sxs-lookup"><span data-stu-id="52090-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="52090-114">`cClauses` が 0 以外の場合は、`clauses` アレイの記憶容量を表します。</span><span class="sxs-lookup"><span data-stu-id="52090-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="52090-115">メソッドが戻るとき、`clauses` には、`cClauses` の最大項目が含まれ、`pcClauses` は、実際に`clauses` アレイに書き込まれる句の数が設定されます。</span><span class="sxs-lookup"><span data-stu-id="52090-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52090-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="52090-116">Requirements</span></span>  
 <span data-ttu-id="52090-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52090-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52090-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52090-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52090-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52090-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52090-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52090-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52090-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="52090-121">See also</span></span>

- [<span data-ttu-id="52090-122">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52090-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="52090-123">CorDebugEHClause 構造体</span><span class="sxs-lookup"><span data-stu-id="52090-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="52090-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="52090-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
