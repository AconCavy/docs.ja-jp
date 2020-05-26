---
title: IHostMemoryManager::VirtualFree メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
ms.openlocfilehash: 4d37b7d803509ebfa861b7502d419f868bd12e11
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804384"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="d9ba8-102">IHostMemoryManager::VirtualFree メソッド</span><span class="sxs-lookup"><span data-stu-id="d9ba8-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="d9ba8-103">対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="d9ba8-104">`VirtualFree`リリース、デ、またはリリースの Win32 実装では、呼び出しプロセスの仮想アドレス空間内のページの領域をデします。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ba8-105">構文</span><span class="sxs-lookup"><span data-stu-id="d9ba8-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9ba8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d9ba8-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="d9ba8-107">から解放される仮想メモリページのベースアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="d9ba8-108">から解放する領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="d9ba8-109">から解放操作の種類。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9ba8-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="d9ba8-110">Return Value</span></span>  
  
|<span data-ttu-id="d9ba8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9ba8-111">HRESULT</span></span>|<span data-ttu-id="d9ba8-112">説明</span><span class="sxs-lookup"><span data-stu-id="d9ba8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9ba8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9ba8-113">S_OK</span></span>|<span data-ttu-id="d9ba8-114">`VirtualFree`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="d9ba8-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9ba8-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9ba8-116">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9ba8-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9ba8-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9ba8-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-118">The call timed out.</span></span>|  
|<span data-ttu-id="d9ba8-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9ba8-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9ba8-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9ba8-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9ba8-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9ba8-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9ba8-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9ba8-123">E_FAIL</span></span>|<span data-ttu-id="d9ba8-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9ba8-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9ba8-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d9ba8-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="d9ba8-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="d9ba8-128">ホストを通じて割り当てられていないメモリを解放しようとしました。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9ba8-129">解説</span><span class="sxs-lookup"><span data-stu-id="d9ba8-129">Remarks</span></span>  
 <span data-ttu-id="d9ba8-130">`VirtualFree``lpAddress` [IHostMemoryManager:: VirtualAlloc](ihostmemorymanager-virtualalloc-method.md)関数の以前の呼び出しによって、パラメーターに関連付けられた仮想メモリページを解放します。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="d9ba8-131">ホストを通じて割り当てられていないメモリを解放しようとすると HOST_E_INVALIDOPERATION が返されます。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="d9ba8-132">セマンティクスは、の Win32 実装のセマンティクスと同じです `VirtualFree` 。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="d9ba8-133">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9ba8-134">要件</span><span class="sxs-lookup"><span data-stu-id="d9ba8-134">Requirements</span></span>  
 <span data-ttu-id="d9ba8-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9ba8-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9ba8-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d9ba8-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9ba8-137">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d9ba8-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9ba8-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9ba8-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ba8-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9ba8-139">See also</span></span>

- [<span data-ttu-id="d9ba8-140">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9ba8-140">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="d9ba8-141">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9ba8-141">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
