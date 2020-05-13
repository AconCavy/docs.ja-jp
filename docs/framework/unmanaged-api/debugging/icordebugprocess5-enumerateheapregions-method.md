---
title: ICorDebugProcess5::EnumerateHeapRegions メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
ms.openlocfilehash: 50b0859d6727a25906f2c8b0f3fe96da228ab886
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213557"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="8d231-102">ICorDebugProcess5::EnumerateHeapRegions メソッド</span><span class="sxs-lookup"><span data-stu-id="8d231-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="8d231-103">マネージヒープのメモリ範囲の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8d231-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d231-104">構文</span><span class="sxs-lookup"><span data-stu-id="8d231-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d231-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d231-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="8d231-106">入出力マネージヒープ内にオブジェクトが格納されているメモリ範囲の列挙子である[ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d231-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d231-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="8d231-107">Remarks</span></span>  
 <span data-ttu-id="8d231-108">メソッドを呼び出す前に `ICorDebugProcess5::EnumerateHeapRegions` 、 [ICorDebugProcess5:: Getg](icordebugprocess5-getgcheapinformation-method.md)メソッドを呼び出し、 `areGCStructuresValid` 返された[COR_HEAPINFO](cor-heapinfo-structure.md)オブジェクトのフィールドの値を調べて、現在の状態のガベージコレクションヒープが列挙可能であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d231-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="8d231-109">さらに、 `ICorDebugProcess5::EnumerateHeapRegions` `E_FAIL` メモリ領域が作成される前に、プロセスの有効期間が早すぎると、メソッドはを返します。</span><span class="sxs-lookup"><span data-stu-id="8d231-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="8d231-110">このメソッドは、マネージオブジェクトを含む可能性があるすべてのメモリ領域を列挙することが保証されていますが、それらの領域にマネージオブジェクトが実際に存在することは保証されません。</span><span class="sxs-lookup"><span data-stu-id="8d231-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="8d231-111">[ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) collection オブジェクトには、空または予約済みのメモリ領域を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="8d231-111">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="8d231-112">[ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)インターフェイスオブジェクトは、ICorDebugEnum インターフェイスから派生した標準列挙子であり、 [COR_SEGMENT](cor-segment-structure.md)オブジェクトを列挙できます。</span><span class="sxs-lookup"><span data-stu-id="8d231-112">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](cor-segment-structure.md) objects.</span></span> <span data-ttu-id="8d231-113">各[COR_SEGMENT](cor-segment-structure.md)オブジェクトは、特定のセグメントのメモリ範囲に関する情報と、そのセグメント内のオブジェクトの生成を提供します。</span><span class="sxs-lookup"><span data-stu-id="8d231-113">Each [COR_SEGMENT](cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d231-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="8d231-114">Requirements</span></span>  
 <span data-ttu-id="8d231-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d231-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d231-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d231-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d231-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d231-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d231-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d231-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d231-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d231-119">See also</span></span>

- [<span data-ttu-id="8d231-120">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d231-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="8d231-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d231-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
