---
title: IHostPolicyManager::OnDefaultAction メソッド
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: e6aa8cb814e509d310c2f5b5524e0fd6727fc43f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804284"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="85109-102">IHostPolicyManager::OnDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="85109-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="85109-103">スレッドの中止またはアンロードに応じて、 [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md)メソッドの呼び出しによって設定された既定のアクションを共通言語ランタイム (CLR: common language runtime) が実行しようとしていることをホストに通知し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="85109-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85109-104">構文</span><span class="sxs-lookup"><span data-stu-id="85109-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85109-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="85109-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="85109-106">から[EClrOperation](eclroperation-enumeration.md)値の1つ。 CLR が応答するイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="85109-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="85109-107">からイベントへの応答として CLR が実行しているアクションを示す[Epolicyaction](epolicyaction-enumeration.md)値の1つ。</span><span class="sxs-lookup"><span data-stu-id="85109-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85109-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="85109-108">Return Value</span></span>  
  
|<span data-ttu-id="85109-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85109-109">HRESULT</span></span>|<span data-ttu-id="85109-110">説明</span><span class="sxs-lookup"><span data-stu-id="85109-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85109-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="85109-111">S_OK</span></span>|<span data-ttu-id="85109-112">`OnDefaultAction`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="85109-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="85109-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85109-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="85109-114">CLR がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しを処理できません。</span><span class="sxs-lookup"><span data-stu-id="85109-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="85109-115">なく</span><span class="sxs-lookup"><span data-stu-id="85109-115">successfully</span></span>|  
|<span data-ttu-id="85109-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="85109-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="85109-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="85109-117">The call timed out.</span></span>|  
|<span data-ttu-id="85109-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="85109-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="85109-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="85109-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="85109-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="85109-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="85109-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="85109-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="85109-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85109-122">E_FAIL</span></span>|<span data-ttu-id="85109-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="85109-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85109-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="85109-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="85109-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="85109-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85109-126">要件</span><span class="sxs-lookup"><span data-stu-id="85109-126">Requirements</span></span>  
 <span data-ttu-id="85109-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85109-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85109-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="85109-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85109-129">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="85109-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85109-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85109-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85109-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="85109-131">See also</span></span>

- [<span data-ttu-id="85109-132">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="85109-132">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="85109-133">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="85109-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="85109-134">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85109-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="85109-135">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85109-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
