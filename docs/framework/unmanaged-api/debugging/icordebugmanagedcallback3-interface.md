---
title: ICorDebugManagedCallback3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: 63e3f166c4cbf17f4892dccf770343bfbf6e0284
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209748"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="f8167-102">ICorDebugManagedCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8167-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="f8167-103">有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f8167-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8167-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f8167-104">Methods</span></span>  
  
|<span data-ttu-id="f8167-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f8167-105">Method</span></span>|<span data-ttu-id="f8167-106">説明</span><span class="sxs-lookup"><span data-stu-id="f8167-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8167-107">CustomNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="f8167-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="f8167-108">有効なカスタムデバッガー通知が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="f8167-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8167-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="f8167-109">Remarks</span></span>  
 <span data-ttu-id="f8167-110">このインターフェイスは、" [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) [" というインターフェイスを論理的](icordebugmanagedcallback-interface.md)に拡張したものです。</span><span class="sxs-lookup"><span data-stu-id="f8167-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8167-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f8167-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8167-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="f8167-112">Requirements</span></span>  
 <span data-ttu-id="f8167-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8167-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8167-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8167-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8167-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8167-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8167-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8167-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8167-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8167-117">See also</span></span>

- [<span data-ttu-id="f8167-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8167-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="f8167-119">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8167-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="f8167-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8167-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f8167-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f8167-121">Debugging</span></span>](index.md)
