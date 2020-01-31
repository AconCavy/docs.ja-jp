---
title: ICorDebugProcess3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3
helpviewer_keywords:
- ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type:
- apiref
ms.openlocfilehash: 28d1d426276e9654c2122f03fb64735b7e67f44f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792482"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="87ff7-102">ICorDebugProcess3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87ff7-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="87ff7-103">カスタムのデバッガー通知を制御します。</span><span class="sxs-lookup"><span data-stu-id="87ff7-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87ff7-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="87ff7-104">Methods</span></span>  
  
|<span data-ttu-id="87ff7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="87ff7-105">Method</span></span>|<span data-ttu-id="87ff7-106">説明</span><span class="sxs-lookup"><span data-stu-id="87ff7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87ff7-107">SetEnableCustomNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="87ff7-107">SetEnableCustomNotification Method</span></span>](icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="87ff7-108">指定された型のカスタムデバッガー通知を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="87ff7-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87ff7-109">コメント</span><span class="sxs-lookup"><span data-stu-id="87ff7-109">Remarks</span></span>  
 <span data-ttu-id="87ff7-110">このインターフェイスは、ICorDebugProcess2 インターフェイスとインターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="87ff7-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87ff7-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="87ff7-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87ff7-112">要件</span><span class="sxs-lookup"><span data-stu-id="87ff7-112">Requirements</span></span>  
 <span data-ttu-id="87ff7-113">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87ff7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87ff7-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87ff7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87ff7-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87ff7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87ff7-116">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87ff7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ff7-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="87ff7-117">See also</span></span>

- [<span data-ttu-id="87ff7-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87ff7-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="87ff7-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="87ff7-119">Debugging</span></span>](index.md)
