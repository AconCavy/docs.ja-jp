---
title: IHostMemoryManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: 09b4a06892cdc450eed9dead503a990b6f19804e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501509"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="23382-102">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23382-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="23382-103">標準の Win32 仮想メモリ関数を使用する代わりに、共通言語ランタイム (CLR) がホストを介して仮想メモリ要求を行うことができるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23382-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23382-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-104">Methods</span></span>  
  
|<span data-ttu-id="23382-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-105">Method</span></span>|<span data-ttu-id="23382-106">説明</span><span class="sxs-lookup"><span data-stu-id="23382-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23382-107">AcquiredVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-107">AcquiredVirtualAddressSpace Method</span></span>](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="23382-108">共通言語ランタイム (CLR) が、指定されたメモリをオペレーティングシステムから取得したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="23382-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="23382-109">CreateMAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-109">CreateMAlloc Method</span></span>](ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="23382-110">ホストによって作成されたヒープからメモリ割り当てを要求するために使用される[IHostMAlloc](ihostmalloc-interface.md)インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="23382-110">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="23382-111">GetMemoryLoad メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-111">GetMemoryLoad Method</span></span>](ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="23382-112">ホストによって報告された、現在使用されている物理メモリの量を取得します。</span><span class="sxs-lookup"><span data-stu-id="23382-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="23382-113">NeedsVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-113">NeedsVirtualAddressSpace Method</span></span>](ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="23382-114">CLR が指定されたメモリを使用しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="23382-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="23382-115">RegisterMemoryNotificationCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-115">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="23382-116">コンピューターの現在のメモリ負荷を CLR に通知するために、ホストが呼び出すコールバック関数へのポインターを登録します。</span><span class="sxs-lookup"><span data-stu-id="23382-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="23382-117">ReleasedVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-117">ReleasedVirtualAddressSpace Method</span></span>](ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="23382-118">指定されたメモリを使用して CLR が終了したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="23382-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="23382-119">VirtualAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-119">VirtualAlloc Method</span></span>](ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="23382-120">対応する Win32 関数の論理ラッパーとして機能します。これは、呼び出し元プロセスの仮想アドレス空間にあるページの領域を予約またはコミットします。</span><span class="sxs-lookup"><span data-stu-id="23382-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="23382-121">VirtualFree メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-121">VirtualFree Method</span></span>](ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="23382-122">呼び出しプロセスの仮想アドレス空間内のページの領域を解放、デ、または解放してデする、対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="23382-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="23382-123">VirtualProtect メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-123">VirtualProtect Method</span></span>](ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="23382-124">対応する Win32 関数の論理ラッパーとして機能します。これにより、呼び出し元プロセスの仮想アドレス空間でコミットされたページの領域の保護が変更されます。</span><span class="sxs-lookup"><span data-stu-id="23382-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="23382-125">VirtualQuery メソッド</span><span class="sxs-lookup"><span data-stu-id="23382-125">VirtualQuery Method</span></span>](ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="23382-126">対応する Win32 関数の論理ラッパーとして機能し、呼び出し元プロセスの仮想アドレス空間にあるページの範囲に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="23382-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23382-127">解説</span><span class="sxs-lookup"><span data-stu-id="23382-127">Remarks</span></span>  
 <span data-ttu-id="23382-128">`IHostMemoryManager`また、は、ヒープ上でメモリ要求を行うためのポインターを取得し、ホストによって報告されたプロセスのメモリ負荷のレベルを取得するために、CLR のメソッドも提供します。</span><span class="sxs-lookup"><span data-stu-id="23382-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23382-129">要件</span><span class="sxs-lookup"><span data-stu-id="23382-129">Requirements</span></span>  
 <span data-ttu-id="23382-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23382-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23382-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="23382-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23382-132">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="23382-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23382-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23382-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23382-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="23382-134">See also</span></span>

- [<span data-ttu-id="23382-135">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23382-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="23382-136">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23382-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
