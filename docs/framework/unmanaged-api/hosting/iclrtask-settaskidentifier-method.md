---
title: ICLRTask::SetTaskIdentifier メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
ms.openlocfilehash: e1b93356fd40aacdec2e764946e3e3b12d0bd306
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762943"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="7550e-102">ICLRTask::SetTaskIdentifier メソッド</span><span class="sxs-lookup"><span data-stu-id="7550e-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="7550e-103">共通言語ランタイム (CLR) に対して、指定された識別子の値を現在の[ICLRTask](iclrtask-interface.md)インスタンスによって表されるタスクに関連付けるように指示します。</span><span class="sxs-lookup"><span data-stu-id="7550e-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7550e-104">構文</span><span class="sxs-lookup"><span data-stu-id="7550e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7550e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7550e-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="7550e-106">から現在のインスタンスによって表されるタスクに関連付ける共通言語ランタイムの一意の識別子 `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="7550e-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7550e-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="7550e-107">Return Value</span></span>  
  
|<span data-ttu-id="7550e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7550e-108">HRESULT</span></span>|<span data-ttu-id="7550e-109">説明</span><span class="sxs-lookup"><span data-stu-id="7550e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7550e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7550e-110">S_OK</span></span>|<span data-ttu-id="7550e-111">`SetTaskIdentifier`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="7550e-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="7550e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7550e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7550e-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="7550e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7550e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7550e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7550e-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="7550e-115">The call timed out.</span></span>|  
|<span data-ttu-id="7550e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7550e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7550e-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="7550e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7550e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7550e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7550e-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="7550e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7550e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7550e-120">E_FAIL</span></span>|<span data-ttu-id="7550e-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7550e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7550e-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="7550e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7550e-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="7550e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7550e-124">解説</span><span class="sxs-lookup"><span data-stu-id="7550e-124">Remarks</span></span>  
 <span data-ttu-id="7550e-125">ホストは、デバッグ環境で CLR とホストを統合できるように、識別子をタスクに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="7550e-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="7550e-126">この識別子は、CLR には意味がありません。</span><span class="sxs-lookup"><span data-stu-id="7550e-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="7550e-127">CLR はこれをデバッガーアプリケーションに渡します。</span><span class="sxs-lookup"><span data-stu-id="7550e-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="7550e-128">デバッガーはこの識別子を使用して、CLR 呼び出し履歴をホストの呼び出し履歴に関連付けて、デバッガーのユーザーインターフェイスに表示されたときに、それぞれのトレース情報を統合できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7550e-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7550e-129">要件</span><span class="sxs-lookup"><span data-stu-id="7550e-129">Requirements</span></span>  
 <span data-ttu-id="7550e-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7550e-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7550e-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7550e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7550e-132">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7550e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7550e-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7550e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7550e-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="7550e-134">See also</span></span>

- [<span data-ttu-id="7550e-135">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7550e-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7550e-136">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7550e-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7550e-137">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7550e-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7550e-138">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7550e-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
