---
title: ICLRSyncManager::CreateRWLockOwnerIterator メソッド
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
ms.openlocfilehash: f8fde4905c41dffde90c6361b5a8cdffa15deb4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503966"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="4eb33-102">ICLRSyncManager::CreateRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="4eb33-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="4eb33-103">リーダーライターロックを待機しているタスクのセットを決定するために使用するホストの反復子を共通言語ランタイム (CLR) が作成することを要求します。</span><span class="sxs-lookup"><span data-stu-id="4eb33-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eb33-104">構文</span><span class="sxs-lookup"><span data-stu-id="4eb33-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4eb33-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4eb33-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="4eb33-106">から目的のリーダーライターロックに関連付けられているクッキー。</span><span class="sxs-lookup"><span data-stu-id="4eb33-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="4eb33-107">入出力[GetRWLockOwnerNext](iclrsyncmanager-getrwlockownernext-method.md)メソッドおよび[DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md)メソッドに渡すことができる反復子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4eb33-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4eb33-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="4eb33-108">Return Value</span></span>  
  
|<span data-ttu-id="4eb33-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4eb33-109">HRESULT</span></span>|<span data-ttu-id="4eb33-110">説明</span><span class="sxs-lookup"><span data-stu-id="4eb33-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4eb33-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4eb33-111">S_OK</span></span>|<span data-ttu-id="4eb33-112">`CreateRWLockOwnerIterator`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="4eb33-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="4eb33-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4eb33-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4eb33-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="4eb33-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4eb33-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4eb33-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4eb33-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4eb33-116">The call timed out.</span></span>|  
|<span data-ttu-id="4eb33-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4eb33-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4eb33-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4eb33-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4eb33-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4eb33-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4eb33-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="4eb33-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4eb33-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4eb33-121">E_FAIL</span></span>|<span data-ttu-id="4eb33-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4eb33-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4eb33-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="4eb33-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4eb33-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="4eb33-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4eb33-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="4eb33-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="4eb33-126">`CreateRWLockOwnerIterator`は、現在マネージコードを実行しているスレッドで呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="4eb33-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4eb33-127">解説</span><span class="sxs-lookup"><span data-stu-id="4eb33-127">Remarks</span></span>  
 <span data-ttu-id="4eb33-128">通常、ホストは `CreateRWLockOwnerIterator` 、 `DeleteRWLockOwnerIterator` デッドロックの検出時に、、およびの各メソッドを呼び出し `GetRWLockOwnerNext` ます。</span><span class="sxs-lookup"><span data-stu-id="4eb33-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="4eb33-129">ホストは、リーダーライターロックが有効であることを CLR が防ぐため、リーダーライターロックが引き続き有効であることを保証する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="4eb33-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="4eb33-130">ホストでは、次のようないくつかの方法でロックの有効性を確認できます。</span><span class="sxs-lookup"><span data-stu-id="4eb33-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="4eb33-131">ホストは、このブロックでデッドロックが発生しないようにするために、リーダーライターロック (たとえば、 [IHostSemaphore:: ReleaseSemaphore](ihostsemaphore-releasesemaphore-method.md)) でのリリース呼び出しをブロックできます。</span><span class="sxs-lookup"><span data-stu-id="4eb33-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="4eb33-132">ホストは、リーダーライターロックに関連付けられているイベントオブジェクトでの終了の待機をブロックできます。このブロックによってデッドロックが発生しないようにします。</span><span class="sxs-lookup"><span data-stu-id="4eb33-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4eb33-133">`CreateRWLockOwnerIterator`は、現在アンマネージコードを実行しているスレッドでのみ呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4eb33-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eb33-134">要件</span><span class="sxs-lookup"><span data-stu-id="4eb33-134">Requirements</span></span>  
 <span data-ttu-id="4eb33-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4eb33-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eb33-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4eb33-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4eb33-137">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4eb33-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4eb33-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eb33-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb33-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="4eb33-139">See also</span></span>

- [<span data-ttu-id="4eb33-140">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4eb33-140">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="4eb33-141">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4eb33-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
