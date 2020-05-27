---
title: IHostTaskManager::ReverseLeaveRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
ms.openlocfilehash: d328afcba9761f686dd38bdb2dd651994faaac2a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841855"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="8e595-102">IHostTaskManager::ReverseLeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="8e595-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="8e595-103">コントロールが共通言語ランタイム (CLR) を離れていること、およびマネージコードから呼び出されたアンマネージ関数を入力していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8e595-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e595-104">構文</span><span class="sxs-lookup"><span data-stu-id="8e595-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8e595-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="8e595-105">Return Value</span></span>  
  
|<span data-ttu-id="8e595-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e595-106">HRESULT</span></span>|<span data-ttu-id="8e595-107">説明</span><span class="sxs-lookup"><span data-stu-id="8e595-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e595-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e595-108">S_OK</span></span>|<span data-ttu-id="8e595-109">`ReverseLeaveRuntime`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="8e595-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="8e595-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8e595-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8e595-111">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="8e595-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8e595-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8e595-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8e595-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="8e595-113">The call timed out.</span></span>|  
|<span data-ttu-id="8e595-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8e595-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8e595-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="8e595-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8e595-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8e595-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8e595-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="8e595-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8e595-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8e595-118">E_FAIL</span></span>|<span data-ttu-id="8e595-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8e595-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8e595-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8e595-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8e595-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="8e595-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8e595-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8e595-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8e595-123">要求されたリソース割り当てを完了するために必要なメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="8e595-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e595-124">コメント</span><span class="sxs-lookup"><span data-stu-id="8e595-124">Remarks</span></span>  
 <span data-ttu-id="8e595-125">CLR はを呼び出して、 `ReverseLeaveRuntime` 現在実行中のタスクがアンマネージ関数に制御を返していることをホストに通知します。これは、プラットフォーム呼び出しによってマネージコードから呼び出されたものです。</span><span class="sxs-lookup"><span data-stu-id="8e595-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="8e595-126">への各呼び出し `ReverseLeaveRuntime` は、対応する[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)への呼び出しと一致します。</span><span class="sxs-lookup"><span data-stu-id="8e595-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e595-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="8e595-127">Requirements</span></span>  
 <span data-ttu-id="8e595-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e595-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e595-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8e595-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e595-130">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8e595-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e595-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e595-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e595-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e595-132">See also</span></span>

- [<span data-ttu-id="8e595-133">CallNeedsHostHook メソッド</span><span class="sxs-lookup"><span data-stu-id="8e595-133">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="8e595-134">EnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="8e595-134">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="8e595-135">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8e595-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8e595-136">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8e595-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8e595-137">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8e595-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8e595-138">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8e595-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="8e595-139">LeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="8e595-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="8e595-140">[プラットフォーム呼び出しの詳細](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8e595-140">[A Closer Look at Platform Invoke](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
