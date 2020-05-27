---
title: IHostTaskManager::SetLocale メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: 841827017262b731fd5e6f6bd0b5862fecaf2744
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841725"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="9ee12-102">IHostTaskManager::SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="9ee12-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="9ee12-103">共通言語ランタイム (CLR) によって、現在実行中のタスクのロケール (カルチャ) が変更されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="9ee12-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ee12-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ee12-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ee12-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ee12-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="9ee12-106">から新しく割り当てられた地理的カルチャおよび言語にマップされるロケール識別子の値。</span><span class="sxs-lookup"><span data-stu-id="9ee12-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ee12-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ee12-107">Return Value</span></span>  
  
|<span data-ttu-id="9ee12-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ee12-108">HRESULT</span></span>|<span data-ttu-id="9ee12-109">説明</span><span class="sxs-lookup"><span data-stu-id="9ee12-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ee12-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ee12-110">S_OK</span></span>|<span data-ttu-id="9ee12-111">`SetLocale`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9ee12-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="9ee12-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9ee12-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9ee12-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="9ee12-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9ee12-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9ee12-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9ee12-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9ee12-115">The call timed out.</span></span>|  
|<span data-ttu-id="9ee12-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ee12-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9ee12-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9ee12-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9ee12-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9ee12-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9ee12-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="9ee12-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9ee12-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ee12-120">E_FAIL</span></span>|<span data-ttu-id="9ee12-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9ee12-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9ee12-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9ee12-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9ee12-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ee12-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9ee12-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9ee12-124">E_NOTIMPL</span></span>|<span data-ttu-id="9ee12-125">ホストでは、マネージユーザーコードでロケールを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="9ee12-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ee12-126">コメント</span><span class="sxs-lookup"><span data-stu-id="9ee12-126">Remarks</span></span>  
 <span data-ttu-id="9ee12-127">ランタイムは、 `SetLocale` プロパティの値 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> がマネージコードによって変更されたときにを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9ee12-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="9ee12-128">この方法を使用すると、ホストはロケールの同期に必要なメカニズムを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9ee12-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="9ee12-129">ホストでロケールをマネージコードから変更できない場合、またはロケールを同期する機構を実装していない場合は、このメソッドから E_NOTIMPL が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ee12-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ee12-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="9ee12-130">Requirements</span></span>  
 <span data-ttu-id="9ee12-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ee12-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ee12-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9ee12-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ee12-133">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9ee12-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ee12-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ee12-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee12-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ee12-135">See also</span></span>

- [<span data-ttu-id="9ee12-136">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ee12-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9ee12-137">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ee12-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9ee12-138">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ee12-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9ee12-139">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ee12-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="9ee12-140">SetUILocale メソッド</span><span class="sxs-lookup"><span data-stu-id="9ee12-140">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)
