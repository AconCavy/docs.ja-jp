---
title: COR_SEGMENT 構造体
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
ms.openlocfilehash: a5c743064b8ca645cf45d02b8800c88187bf4c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179280"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="296b3-102">COR_SEGMENT 構造体</span><span class="sxs-lookup"><span data-stu-id="296b3-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="296b3-103">マネージド ヒープのメモリ領域に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="296b3-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="296b3-104">構文</span><span class="sxs-lookup"><span data-stu-id="296b3-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;
    CORDB_ADDRESS end;
    CorDebugGenerationTypes gen;
    ULONG heap;
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="296b3-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="296b3-105">Members</span></span>  
  
|<span data-ttu-id="296b3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="296b3-106">Member</span></span>|<span data-ttu-id="296b3-107">説明</span><span class="sxs-lookup"><span data-stu-id="296b3-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="296b3-108">メモリ領域の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="296b3-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="296b3-109">メモリ領域の終了アドレス。</span><span class="sxs-lookup"><span data-stu-id="296b3-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="296b3-110">メモリ領域の生成を示す [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) 列挙メンバー。</span><span class="sxs-lookup"><span data-stu-id="296b3-110">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="296b3-111">メモリ領域が存在するヒープ番号。</span><span class="sxs-lookup"><span data-stu-id="296b3-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="296b3-112">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="296b3-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="296b3-113">解説</span><span class="sxs-lookup"><span data-stu-id="296b3-113">Remarks</span></span>  
 <span data-ttu-id="296b3-114">`COR_SEGMENTS` 構造体は、マネージド ヒープのメモリ領域を表します。</span><span class="sxs-lookup"><span data-stu-id="296b3-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="296b3-115">`COR_SEGMENTS` オブジェクトは、[ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) メソッドを呼び出すことによって入力される [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) コレクション オブジェクトのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="296b3-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="296b3-116">`heap` フィールドは、報告されたヒープに対応するプロセッサ番号です。</span><span class="sxs-lookup"><span data-stu-id="296b3-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="296b3-117">ワークステーション ガベージ コレクターでは、ワークステーションにガベージ コレクション ヒープが 1 つしかないため、その値は常に 0 です。</span><span class="sxs-lookup"><span data-stu-id="296b3-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="296b3-118">サーバー ガベージ コレクターでは、その値はヒープがアタッチされているプロセッサに対応します。</span><span class="sxs-lookup"><span data-stu-id="296b3-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="296b3-119">ガベージ コレクターの実装の詳細が原因で、実際のプロセッサ数よりも、ガベージ コレクション ヒープが多かったり少なかったりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="296b3-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="296b3-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="296b3-120">Requirements</span></span>  
 <span data-ttu-id="296b3-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="296b3-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="296b3-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="296b3-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="296b3-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="296b3-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="296b3-124">**.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="296b3-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="296b3-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="296b3-125">See also</span></span>

- [<span data-ttu-id="296b3-126">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="296b3-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="296b3-127">デバッグ</span><span class="sxs-lookup"><span data-stu-id="296b3-127">Debugging</span></span>](index.md)
