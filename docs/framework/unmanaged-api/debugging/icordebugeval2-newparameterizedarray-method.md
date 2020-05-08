---
title: ICorDebugEval2::NewParameterizedArray メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 9d589bfc3093d03d87acb47ade0fc6c972bcd335
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976110"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="c8042-102">ICorDebugEval2::NewParameterizedArray メソッド</span><span class="sxs-lookup"><span data-stu-id="c8042-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="c8042-103">指定した要素の型と次元の新しい配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c8042-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8042-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8042-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8042-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8042-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="c8042-106">から配列に格納されている要素の型を表す、の型のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c8042-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="c8042-107">から配列の次元数。</span><span class="sxs-lookup"><span data-stu-id="c8042-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="c8042-108">.NET Framework バージョン2.0 では、この値は1である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8042-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="c8042-109">から配列の各次元のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="c8042-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="c8042-110">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="c8042-110">[in] Optional.</span></span> <span data-ttu-id="c8042-111">配列の各次元の下限。</span><span class="sxs-lookup"><span data-stu-id="c8042-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="c8042-112">この値を省略すると、次元ごとに下限0が想定されます。</span><span class="sxs-lookup"><span data-stu-id="c8042-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8042-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="c8042-113">Remarks</span></span>  
 <span data-ttu-id="c8042-114">配列の要素は、ジェネリック型のインスタンスである場合があります。</span><span class="sxs-lookup"><span data-stu-id="c8042-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="c8042-115">配列は常に、スレッドが現在実行されているアプリケーションドメインで作成されます。</span><span class="sxs-lookup"><span data-stu-id="c8042-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="c8042-116">.NET Framework 2.0 では、の`rank`値は1である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8042-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8042-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="c8042-117">Requirements</span></span>  
 <span data-ttu-id="c8042-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8042-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8042-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8042-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8042-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8042-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8042-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8042-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
