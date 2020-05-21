---
title: ICLRTask::YieldTask メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
ms.openlocfilehash: ccfca2f685a88f5802dd58667fbf1fac14727c88
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762904"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="8066b-102">ICLRTask::YieldTask メソッド</span><span class="sxs-lookup"><span data-stu-id="8066b-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="8066b-103">現在の[ICLRTask](iclrtask-interface.md)インスタンスが表すタスクを共通言語ランタイム (CLR) が確保し、他のタスクでプロセッサ時間を使用できるようにすることを要求します。</span><span class="sxs-lookup"><span data-stu-id="8066b-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8066b-104">構文</span><span class="sxs-lookup"><span data-stu-id="8066b-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8066b-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="8066b-105">Return Value</span></span>  
  
|<span data-ttu-id="8066b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8066b-106">HRESULT</span></span>|<span data-ttu-id="8066b-107">説明</span><span class="sxs-lookup"><span data-stu-id="8066b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8066b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8066b-108">S_OK</span></span>|<span data-ttu-id="8066b-109">`YieldTask`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="8066b-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="8066b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8066b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8066b-111">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="8066b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8066b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8066b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8066b-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="8066b-113">The call timed out.</span></span>|  
|<span data-ttu-id="8066b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8066b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8066b-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="8066b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8066b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8066b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8066b-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="8066b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8066b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8066b-118">E_FAIL</span></span>|<span data-ttu-id="8066b-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8066b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8066b-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8066b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8066b-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="8066b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8066b-122">解説</span><span class="sxs-lookup"><span data-stu-id="8066b-122">Remarks</span></span>  
 <span data-ttu-id="8066b-123">ホストは、 `YieldTask` 他のタスクまたはプロセスのプロセッサリソースを要求するためにを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8066b-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="8066b-124">このメソッドは、主に、長時間実行されるコードが CPU 時間を確保できるようにするためのものです。</span><span class="sxs-lookup"><span data-stu-id="8066b-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="8066b-125">ランタイムは、現在 `ICLRTask` のインスタンスが処理時間を生成できる状態のタスクを配置しようとしますが、成功は保証されません。</span><span class="sxs-lookup"><span data-stu-id="8066b-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8066b-126">要件</span><span class="sxs-lookup"><span data-stu-id="8066b-126">Requirements</span></span>  
 <span data-ttu-id="8066b-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8066b-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8066b-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8066b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8066b-129">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8066b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8066b-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8066b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8066b-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="8066b-131">See also</span></span>

- [<span data-ttu-id="8066b-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8066b-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8066b-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8066b-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8066b-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8066b-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8066b-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8066b-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
