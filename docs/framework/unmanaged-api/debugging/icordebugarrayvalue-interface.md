---
title: ICorDebugArrayValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: bd1e86b83c43af20604416f158ab9e74f399821b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894963"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="7cb14-102">ICorDebugArrayValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cb14-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="7cb14-103">1次元配列または多次元配列を表す、値のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="7cb14-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7cb14-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="7cb14-104">Methods</span></span>  
  
|<span data-ttu-id="7cb14-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7cb14-105">Method</span></span>|<span data-ttu-id="7cb14-106">説明</span><span class="sxs-lookup"><span data-stu-id="7cb14-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7cb14-107">GetBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="7cb14-107">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="7cb14-108">配列内の各次元のベースインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="7cb14-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="7cb14-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="7cb14-109">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="7cb14-110">配列内の要素の合計数を取得します。</span><span class="sxs-lookup"><span data-stu-id="7cb14-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="7cb14-111">GetDimensions メソッド</span><span class="sxs-lookup"><span data-stu-id="7cb14-111">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="7cb14-112">配列の次元を取得します。</span><span class="sxs-lookup"><span data-stu-id="7cb14-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="7cb14-113">GetElement メソッド</span><span class="sxs-lookup"><span data-stu-id="7cb14-113">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="7cb14-114">配列内の指定された要素を表す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="7cb14-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="7cb14-115">GetElementAtPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="7cb14-115">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="7cb14-116">配列を0から始まる1次元配列として扱い、指定された位置にある要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="7cb14-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="7cb14-117">GetElementType メソッド</span><span class="sxs-lookup"><span data-stu-id="7cb14-117">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="7cb14-118">配列内の要素の単純型を取得します。</span><span class="sxs-lookup"><span data-stu-id="7cb14-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="7cb14-119">GetRank メソッド</span><span class="sxs-lookup"><span data-stu-id="7cb14-119">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="7cb14-120">配列のディメンションの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="7cb14-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="7cb14-121">HasBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="7cb14-121">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="7cb14-122">配列にベースインデックスがあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="7cb14-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cb14-123">解説</span><span class="sxs-lookup"><span data-stu-id="7cb14-123">Remarks</span></span>  
 <span data-ttu-id="7cb14-124">`ICorDebugArrayValue`では、1次元配列と多次元配列の両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7cb14-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cb14-125">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="7cb14-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cb14-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="7cb14-126">Requirements</span></span>  
 <span data-ttu-id="7cb14-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cb14-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cb14-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cb14-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cb14-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cb14-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cb14-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cb14-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb14-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="7cb14-131">See also</span></span>

- [<span data-ttu-id="7cb14-132">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cb14-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
