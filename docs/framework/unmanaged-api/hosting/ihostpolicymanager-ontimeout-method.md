---
title: IHostPolicyManager::OnTimeout メソッド
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
ms.openlocfilehash: fb0f943d710322257d052edc5c16108671622790
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804212"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="5087e-102">IHostPolicyManager::OnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="5087e-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="5087e-103">タイムアウトに応答して、 [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md)メソッドの呼び出しで指定されたアクションを共通言語ランタイム (CLR: common language runtime) が実行しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5087e-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5087e-104">構文</span><span class="sxs-lookup"><span data-stu-id="5087e-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5087e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5087e-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="5087e-106">から[EClrOperation](eclroperation-enumeration.md)値の1つ。タイムアウトした操作の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="5087e-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="5087e-107">から[Epolicyaction](epolicyaction-enumeration.md)値の1つ。 CLR がタイムアウトに応答して実行しているアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="5087e-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5087e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="5087e-108">Return Value</span></span>  
  
|<span data-ttu-id="5087e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5087e-109">HRESULT</span></span>|<span data-ttu-id="5087e-110">説明</span><span class="sxs-lookup"><span data-stu-id="5087e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5087e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5087e-111">S_OK</span></span>|<span data-ttu-id="5087e-112">`OnTimeout`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="5087e-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="5087e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5087e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5087e-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="5087e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5087e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5087e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5087e-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5087e-116">The call timed out.</span></span>|  
|<span data-ttu-id="5087e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5087e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5087e-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5087e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5087e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5087e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5087e-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="5087e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5087e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5087e-121">E_FAIL</span></span>|<span data-ttu-id="5087e-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5087e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5087e-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5087e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5087e-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="5087e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5087e-125">要件</span><span class="sxs-lookup"><span data-stu-id="5087e-125">Requirements</span></span>  
 <span data-ttu-id="5087e-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5087e-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5087e-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5087e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5087e-128">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5087e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5087e-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5087e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5087e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5087e-130">See also</span></span>

- [<span data-ttu-id="5087e-131">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="5087e-131">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="5087e-132">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="5087e-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="5087e-133">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5087e-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="5087e-134">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5087e-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
