---
title: ICLRSyncManager::GetRWLockOwnerNext メソッド
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
ms.openlocfilehash: e5a8f69e66bb4b6373aea2c753bff9351bff8128
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762488"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="2f0e0-102">ICLRSyncManager::GetRWLockOwnerNext メソッド</span><span class="sxs-lookup"><span data-stu-id="2f0e0-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="2f0e0-103">現在のリーダーライターロックでブロックされている次の[IHostTask](ihosttask-interface.md)インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-103">Gets the next [IHostTask](ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f0e0-104">構文</span><span class="sxs-lookup"><span data-stu-id="2f0e0-104">Syntax</span></span>  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f0e0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f0e0-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="2f0e0-106">から[Createrwlockowneriterator](iclrsyncmanager-createrwlockowneriterator-method.md)の呼び出しを使用して作成された反復子。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="2f0e0-107">入出力ロックを待機している次のへのポインター `IHostTask` 。タスクが待機していない場合は null。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f0e0-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="2f0e0-108">Return Value</span></span>  
  
|<span data-ttu-id="2f0e0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f0e0-109">HRESULT</span></span>|<span data-ttu-id="2f0e0-110">説明</span><span class="sxs-lookup"><span data-stu-id="2f0e0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f0e0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f0e0-111">S_OK</span></span>|<span data-ttu-id="2f0e0-112">`GetRWLockOwnerNext`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="2f0e0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f0e0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f0e0-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f0e0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f0e0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f0e0-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-116">The call timed out.</span></span>|  
|<span data-ttu-id="2f0e0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f0e0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f0e0-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f0e0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f0e0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f0e0-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f0e0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f0e0-121">E_FAIL</span></span>|<span data-ttu-id="2f0e0-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f0e0-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f0e0-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f0e0-125">解説</span><span class="sxs-lookup"><span data-stu-id="2f0e0-125">Remarks</span></span>  
 <span data-ttu-id="2f0e0-126">`ppOwnerHostTask`が null に設定されている場合、イテレーションは終了し、ホストは[DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md)メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f0e0-127">CLR は `AddRef` 、 `IHostTask` `ppOwnerHostTask` ホストがポインターを保持している間に、このタスクが終了しないようにするを指すに対してを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="2f0e0-128">ホストは、 `Release` 終了時に参照カウントをデクリメントするためにを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f0e0-129">要件</span><span class="sxs-lookup"><span data-stu-id="2f0e0-129">Requirements</span></span>  
 <span data-ttu-id="2f0e0-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f0e0-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f0e0-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2f0e0-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f0e0-132">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2f0e0-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f0e0-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f0e0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0e0-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f0e0-134">See also</span></span>

- [<span data-ttu-id="2f0e0-135">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f0e0-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2f0e0-136">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f0e0-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
