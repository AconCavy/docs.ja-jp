---
title: ICLRTaskManager::SetLocale メソッド
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
ms.openlocfilehash: 8f316d91aab4c3862a0ad45b41539a4b80791ab9
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762792"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="af9a7-102">ICLRTaskManager::SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="af9a7-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="af9a7-103">現在実行中のタスクのロケール識別子 (地理的なカルチャおよび言語にマップされる) の値がホストによって変更されたことを、共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="af9a7-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9a7-104">構文</span><span class="sxs-lookup"><span data-stu-id="af9a7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af9a7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="af9a7-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="af9a7-106">から新しく割り当てられた地理的カルチャおよび言語にマップされるロケール識別子の値。</span><span class="sxs-lookup"><span data-stu-id="af9a7-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af9a7-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="af9a7-107">Return Value</span></span>  
  
|<span data-ttu-id="af9a7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af9a7-108">HRESULT</span></span>|<span data-ttu-id="af9a7-109">説明</span><span class="sxs-lookup"><span data-stu-id="af9a7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af9a7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="af9a7-110">S_OK</span></span>|<span data-ttu-id="af9a7-111">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="af9a7-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="af9a7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="af9a7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="af9a7-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="af9a7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="af9a7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="af9a7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="af9a7-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="af9a7-115">The call timed out.</span></span>|  
|<span data-ttu-id="af9a7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="af9a7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="af9a7-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="af9a7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="af9a7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="af9a7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="af9a7-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="af9a7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="af9a7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="af9a7-120">E_FAIL</span></span>|<span data-ttu-id="af9a7-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="af9a7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="af9a7-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="af9a7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="af9a7-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="af9a7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af9a7-124">解説</span><span class="sxs-lookup"><span data-stu-id="af9a7-124">Remarks</span></span>  
 <span data-ttu-id="af9a7-125">`SetLocale`ホストに、ロケールの同期に必要なメカニズムを実行する機会を与えます。</span><span class="sxs-lookup"><span data-stu-id="af9a7-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af9a7-126">要件</span><span class="sxs-lookup"><span data-stu-id="af9a7-126">Requirements</span></span>  
 <span data-ttu-id="af9a7-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af9a7-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af9a7-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="af9a7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af9a7-129">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="af9a7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af9a7-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af9a7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af9a7-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="af9a7-131">See also</span></span>

- [<span data-ttu-id="af9a7-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af9a7-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="af9a7-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af9a7-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="af9a7-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af9a7-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="af9a7-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af9a7-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
