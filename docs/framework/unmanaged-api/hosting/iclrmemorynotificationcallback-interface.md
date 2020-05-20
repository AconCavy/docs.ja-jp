---
title: ICLRMemoryNotificationCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: 52fc21044d345998ad72c045cdf5e80a8a03a38e
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703803"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="a9103-102">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9103-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="a9103-103">Win32 関数と同様の方法を使用して、ホストがメモリ不足状態を報告できるようにし `CreateMemoryResourceNotification` ます。</span><span class="sxs-lookup"><span data-stu-id="a9103-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9103-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a9103-104">Methods</span></span>  
  
|<span data-ttu-id="a9103-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a9103-105">Method</span></span>|<span data-ttu-id="a9103-106">説明</span><span class="sxs-lookup"><span data-stu-id="a9103-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9103-107">OnMemoryNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="a9103-107">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="a9103-108">コンピューターのメモリ負荷の共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="a9103-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9103-109">解説</span><span class="sxs-lookup"><span data-stu-id="a9103-109">Remarks</span></span>  
 <span data-ttu-id="a9103-110">ホストは、このインターフェイスを使用して、 `ICLRMemoryNotificationCallback` CLR のメモリリソースを解放するように要求します。</span><span class="sxs-lookup"><span data-stu-id="a9103-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9103-111">要件</span><span class="sxs-lookup"><span data-stu-id="a9103-111">Requirements</span></span>  
 <span data-ttu-id="a9103-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9103-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9103-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a9103-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9103-114">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a9103-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9103-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9103-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9103-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9103-116">See also</span></span>

- [<span data-ttu-id="a9103-117">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9103-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="a9103-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9103-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
