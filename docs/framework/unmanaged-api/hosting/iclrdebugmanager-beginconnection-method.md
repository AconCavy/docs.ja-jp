---
title: ICLRDebugManager::BeginConnection メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: 98e4efe149cab1b822c9993e4df28806f773c61d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504252"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="a97b5-102">ICLRDebugManager::BeginConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="a97b5-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="a97b5-103">ホストとデバッガーの間の新しい接続を確立して、タスクの一覧を識別子とフレンドリ名に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="a97b5-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a97b5-104">構文</span><span class="sxs-lookup"><span data-stu-id="a97b5-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a97b5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a97b5-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="a97b5-106">から共通言語ランタイム (CLR) タスクのリストに関連付ける識別子。</span><span class="sxs-lookup"><span data-stu-id="a97b5-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="a97b5-107">からCLR タスクの一覧に関連付けるフレンドリ名。</span><span class="sxs-lookup"><span data-stu-id="a97b5-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a97b5-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="a97b5-108">Return Value</span></span>  
  
|<span data-ttu-id="a97b5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a97b5-109">HRESULT</span></span>|<span data-ttu-id="a97b5-110">説明</span><span class="sxs-lookup"><span data-stu-id="a97b5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a97b5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a97b5-111">S_OK</span></span>|<span data-ttu-id="a97b5-112">`BeginConnection`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="a97b5-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="a97b5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a97b5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a97b5-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="a97b5-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a97b5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a97b5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a97b5-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a97b5-116">The call timed out.</span></span>|  
|<span data-ttu-id="a97b5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a97b5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a97b5-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a97b5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a97b5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a97b5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a97b5-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="a97b5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a97b5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a97b5-121">E_FAIL</span></span>|<span data-ttu-id="a97b5-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a97b5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a97b5-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a97b5-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a97b5-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="a97b5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a97b5-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a97b5-125">E_INVALIDARG</span></span>|<span data-ttu-id="a97b5-126">`dwConnectionId`が0であるか、 `BeginConnection` 既にこの値を使用して呼び出されたか `dwConnectionId` 、または `szConnectionName` が null でした。</span><span class="sxs-lookup"><span data-stu-id="a97b5-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="a97b5-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a97b5-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a97b5-128">この接続に関連付けられたタスクの一覧を保持するために十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="a97b5-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a97b5-129">解説</span><span class="sxs-lookup"><span data-stu-id="a97b5-129">Remarks</span></span>  
 <span data-ttu-id="a97b5-130">[ICLRDebugManager](iclrdebugmanager-interface.md)には `BeginConnection` 、、 [Setconnectiontasks](iclrdebugmanager-setconnectiontasks-method.md)、 [endconnection](iclrdebugmanager-endconnection-method.md)という3つのメソッドが用意されており、タスクリストを識別子と表示名に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="a97b5-130">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a97b5-131">これら3つのメソッドは、一連のタスクごとに特定の順序で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a97b5-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="a97b5-132">`BeginConnection`は、新しい接続を確立するために最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a97b5-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="a97b5-133">`SetConnectionTasks`は、その接続に関連する一連のタスクを提供するために、次に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a97b5-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="a97b5-134">`EndConnection`は、タスク一覧と識別子とフレンドリ名の間の関連付けを削除するために最後に呼び出されます。ただし、異なる接続の呼び出しは入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a97b5-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a97b5-135">要件</span><span class="sxs-lookup"><span data-stu-id="a97b5-135">Requirements</span></span>  
 <span data-ttu-id="a97b5-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a97b5-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a97b5-137">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a97b5-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a97b5-138">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a97b5-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a97b5-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a97b5-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a97b5-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="a97b5-140">See also</span></span>

- [<span data-ttu-id="a97b5-141">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a97b5-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a97b5-142">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a97b5-142">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="a97b5-143">EndConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="a97b5-143">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="a97b5-144">SetConnectionTasks メソッド</span><span class="sxs-lookup"><span data-stu-id="a97b5-144">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="a97b5-145">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a97b5-145">IHostControl Interface</span></span>](ihostcontrol-interface.md)
