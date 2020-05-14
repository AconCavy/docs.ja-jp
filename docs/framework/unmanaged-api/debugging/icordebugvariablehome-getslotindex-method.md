---
title: 'いい変数 Home:: GetSlotIndex メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 0bffd2db0a4a061a8629ff50a03a319feec6d836
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396551"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="52d67-102">いい変数 Home:: GetSlotIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="52d67-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="52d67-103">ローカル変数のマネージドスロットインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="52d67-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52d67-104">構文</span><span class="sxs-lookup"><span data-stu-id="52d67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52d67-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52d67-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="52d67-106">入出力ローカル変数のスロットインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="52d67-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52d67-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="52d67-107">Return Value</span></span>  
 <span data-ttu-id="52d67-108">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="52d67-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="52d67-109">値</span><span class="sxs-lookup"><span data-stu-id="52d67-109">Value</span></span>|<span data-ttu-id="52d67-110">説明</span><span class="sxs-lookup"><span data-stu-id="52d67-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="52d67-111">メソッド呼び出しによって、でスロットインデックス値が返されました `pSlotIndex` 。</span><span class="sxs-lookup"><span data-stu-id="52d67-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="52d67-112">現在のは、[関数の引数](icordebugvariablehome-interface.md)を表します。</span><span class="sxs-lookup"><span data-stu-id="52d67-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52d67-113">解説</span><span class="sxs-lookup"><span data-stu-id="52d67-113">Remarks</span></span>  
 <span data-ttu-id="52d67-114">このローカル変数のメタデータを取得するために、スロットインデックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="52d67-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52d67-115">要件</span><span class="sxs-lookup"><span data-stu-id="52d67-115">Requirements</span></span>  
 <span data-ttu-id="52d67-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52d67-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52d67-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52d67-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52d67-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52d67-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52d67-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52d67-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52d67-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="52d67-120">See also</span></span>

- [<span data-ttu-id="52d67-121">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52d67-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
