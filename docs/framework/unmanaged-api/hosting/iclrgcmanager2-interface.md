---
title: ICLRGCManager2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: 0f3ecc0d497eaee937647df47ba0956335a2fe41
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703951"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="f2156-102">ICLRGCManager2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2156-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="f2156-103">ホストが共通言語ランタイムのガベージコレクションシステムと対話できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f2156-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2156-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f2156-104">Methods</span></span>  
  
|<span data-ttu-id="f2156-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f2156-105">Method</span></span>|<span data-ttu-id="f2156-106">説明</span><span class="sxs-lookup"><span data-stu-id="f2156-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2156-107">SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="f2156-107">SetGCStartupLimitsEx Method</span></span>](iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="f2156-108">ガベージコレクションセグメントのサイズとガベージコレクションシステムのジェネレーション0の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="f2156-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="f2156-109">より大きいジェネレーション0およびセグメントサイズを有効に `DWORD` します。</span><span class="sxs-lookup"><span data-stu-id="f2156-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2156-110">解説</span><span class="sxs-lookup"><span data-stu-id="f2156-110">Remarks</span></span>  
 <span data-ttu-id="f2156-111">このインターフェイスは、 [ICLRGCManager インターフェイス](iclrgcmanager-interface.md)から継承されます。</span><span class="sxs-lookup"><span data-stu-id="f2156-111">This interface inherits from the [ICLRGCManager Interface](iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="f2156-112">共通言語ランタイム (CLR) は、マネージ型を使用してガベージコレクション機構を実装し <xref:System.GC> ます。</span><span class="sxs-lookup"><span data-stu-id="f2156-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="f2156-113">ガベージコレクションシステムの詳細については、「[ガベージコレクション](../../../standard/garbage-collection/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2156-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2156-114">要件</span><span class="sxs-lookup"><span data-stu-id="f2156-114">Requirements</span></span>  
 <span data-ttu-id="f2156-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2156-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2156-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f2156-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2156-117">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f2156-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2156-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2156-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2156-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2156-119">See also</span></span>

- [<span data-ttu-id="f2156-120">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="f2156-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="f2156-121">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="f2156-121">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="f2156-122">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2156-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="f2156-123">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2156-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="f2156-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2156-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f2156-125">ホスティング</span><span class="sxs-lookup"><span data-stu-id="f2156-125">Hosting</span></span>](index.md)
