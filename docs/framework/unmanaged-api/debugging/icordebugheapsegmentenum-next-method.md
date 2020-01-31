---
title: ICorDebugHeapSegmentEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 89ce4eafa46be3e9ba7cdb06884034a521e43bca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777533"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="1899b-102">ICorDebugHeapSegmentEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="1899b-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="1899b-103">マネージヒープのメモリ領域に関する情報を格納している、指定した数の[COR_HEAPOBJECT](cor-heapobject-structure.md)インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="1899b-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1899b-104">構文</span><span class="sxs-lookup"><span data-stu-id="1899b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1899b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1899b-105">Parameters</span></span>  
 <span data-ttu-id="1899b-106">celt</span><span class="sxs-lookup"><span data-stu-id="1899b-106">celt</span></span>  
 <span data-ttu-id="1899b-107">から取得するセグメントの数。</span><span class="sxs-lookup"><span data-stu-id="1899b-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="1899b-108">セグメント</span><span class="sxs-lookup"><span data-stu-id="1899b-108">segments</span></span>  
 <span data-ttu-id="1899b-109">入出力ポインターの配列。各ポインターは、マネージヒープ内のメモリ領域に関する情報を提供する[COR_HEAPOBJECT](cor-heapobject-structure.md)オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="1899b-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="1899b-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="1899b-110">pceltFetched</span></span>  
 <span data-ttu-id="1899b-111">入出力`segments`で実際に返される[COR_HEAPOBJECT](cor-heapobject-structure.md)オブジェクトの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1899b-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="1899b-112">`celt` が 1 の場合、この値は`null` になることがあります。</span><span class="sxs-lookup"><span data-stu-id="1899b-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1899b-113">コメント</span><span class="sxs-lookup"><span data-stu-id="1899b-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1899b-114">要件</span><span class="sxs-lookup"><span data-stu-id="1899b-114">Requirements</span></span>  
 <span data-ttu-id="1899b-115">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1899b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1899b-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1899b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1899b-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1899b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1899b-118">**.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1899b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1899b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1899b-119">See also</span></span>

- [<span data-ttu-id="1899b-120">ICorDebugHeapSegmentEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1899b-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="1899b-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1899b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
