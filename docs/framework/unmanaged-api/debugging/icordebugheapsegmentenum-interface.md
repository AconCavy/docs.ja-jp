---
title: ICorDebugHeapSegmentEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: acf490895db35af1c5d0d1e7fe7e3de5ae2a16b6
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904287"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="b3b2e-102">ICorDebugHeapSegmentEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b3b2e-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="b3b2e-103">マネージド ヒープのメモリ領域の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="b3b2e-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="b3b2e-104">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="b3b2e-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3b2e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b3b2e-105">Methods</span></span>  
  
|<span data-ttu-id="b3b2e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b3b2e-106">Method</span></span>|<span data-ttu-id="b3b2e-107">説明</span><span class="sxs-lookup"><span data-stu-id="b3b2e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3b2e-108">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="b3b2e-108">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="b3b2e-109">マネージヒープの領域に関する情報を格納している、指定した数の[COR_SEGMENT](cor-segment-structure.md)インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="b3b2e-109">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3b2e-110">注釈</span><span class="sxs-lookup"><span data-stu-id="b3b2e-110">Remarks</span></span>  
 <span data-ttu-id="b3b2e-111">`ICorDebugHeapSegmentEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="b3b2e-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="b3b2e-112">`ICorDebugHeapSegmentEnum`インスタンスには、 [ICorDebugProcess5:: EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md)メソッドを呼び出すことによって[COR_SEGMENT](cor-segment-structure.md)インスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="b3b2e-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_SEGMENT](cor-segment-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="b3b2e-113">コレクション内の[COR_SEGMENT](cor-segment-structure.md)オブジェクトは、 [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md)メソッドを呼び出すことによって列挙できます。</span><span class="sxs-lookup"><span data-stu-id="b3b2e-113">The [COR_SEGMENT](cor-segment-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="b3b2e-114">`ICorDebugHeapSegmentEnum`コレクションオブジェクトは、マネージオブジェクトを含む可能性があるすべてのメモリ領域を列挙しますが、それらの領域にマネージオブジェクトが実際に存在することを保証するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="b3b2e-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="b3b2e-115">これには、空または予約済みのメモリ領域に関する情報が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3b2e-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b2e-116">要件</span><span class="sxs-lookup"><span data-stu-id="b3b2e-116">Requirements</span></span>  
 <span data-ttu-id="b3b2e-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3b2e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b2e-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3b2e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3b2e-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3b2e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3b2e-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3b2e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b2e-121">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="b3b2e-121">See also</span></span>

- [<span data-ttu-id="b3b2e-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b3b2e-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
