---
title: ICorDebugHeapEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: ff290cd8ad331ff109c3bbbf87638d22b9b183bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208539"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="56ba0-102">ICorDebugHeapEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56ba0-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="56ba0-103">マネージド ヒープのオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="56ba0-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="56ba0-104">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="56ba0-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56ba0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="56ba0-105">Methods</span></span>  
  
|<span data-ttu-id="56ba0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="56ba0-106">Method</span></span>|<span data-ttu-id="56ba0-107">説明</span><span class="sxs-lookup"><span data-stu-id="56ba0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56ba0-108">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="56ba0-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="56ba0-109">マネージヒープ上のオブジェクトに関する情報を格納している、指定した数の[COR_HEAPOBJECT](cor-heapobject-structure.md)インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="56ba0-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56ba0-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="56ba0-110">Remarks</span></span>  
 <span data-ttu-id="56ba0-111">`ICorDebugHeapEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="56ba0-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="56ba0-112">`ICorDebugHeapEnum`インスタンスには、 [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md)メソッドを呼び出すことによって[COR_HEAPOBJECT](cor-heapobject-structure.md)インスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="56ba0-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="56ba0-113">コレクション内の各[COR_HEAPOBJECT](cor-heapobject-structure.md)インスタンスは、ヒープ上のライブオブジェクト、またはオブジェクトではなく、ガベージコレクターによってまだ収集されていないオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="56ba0-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="56ba0-114">コレクション内の[COR_HEAPOBJECT](cor-heapobject-structure.md)オブジェクトを列挙するには、[次](icordebugheapenum-next-method.md)のメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="56ba0-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56ba0-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="56ba0-115">Requirements</span></span>  
 <span data-ttu-id="56ba0-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56ba0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56ba0-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56ba0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56ba0-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56ba0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56ba0-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56ba0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ba0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="56ba0-120">See also</span></span>

- [<span data-ttu-id="56ba0-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="56ba0-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
