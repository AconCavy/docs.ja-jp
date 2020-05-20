---
title: ICLRControl::GetCLRManager メソッド
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
ms.openlocfilehash: 04cb45cd021532b6cb3d74a195cbd62e1ab8d31d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615853"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="ec8ce-102">ICLRControl::GetCLRManager メソッド</span><span class="sxs-lookup"><span data-stu-id="ec8ce-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="ec8ce-103">ホストが共通言語ランタイム (CLR) を構成するために使用できる任意のマネージャー型のインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec8ce-104">構文</span><span class="sxs-lookup"><span data-stu-id="ec8ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec8ce-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ec8ce-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="ec8ce-106">から`IID`返されるマネージャーの型の。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="ec8ce-107">次の `IID` 値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="ec8ce-108">IID_ICLRDebugManager: が ICLRDebugManager 型であることを指定し `ppObject` ます。 [ICLRDebugManager](iclrdebugmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ec8ce-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="ec8ce-109">IID_ICLRErrorReportingManager: が ICLRErrorReportingManager 型であることを指定し `ppObject` ます。 [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ec8ce-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="ec8ce-110">IID_ICLRGCManager: が ICLRGCManager 型であることを指定し `ppObject` ます。 [ICLRGCManager](iclrgcmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ec8ce-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="ec8ce-111">IID_ICLRHostProtectionManager: が ICLRHostProtectionManager 型であることを指定し `ppObject` ます。 [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ec8ce-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="ec8ce-112">IID_ICLROnEventManager: が ICLROnEventManager 型であることを指定し `ppObject` ます。 [ICLROnEventManager](iclroneventmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ec8ce-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="ec8ce-113">IID_ICLRPolicyManager: が ICLRPolicyManager 型であることを指定し `ppObject` ます。 [ICLRPolicyManager](iclrpolicymanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ec8ce-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="ec8ce-114">IID_ICLRTaskManager: が ICLRTaskManager 型であることを指定し `ppObject` ます。 [ICLRTaskManager](iclrtaskmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ec8ce-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="ec8ce-115">入出力要求されたマネージャーへのインターフェイスポインター。無効なマネージャーの種類が要求された場合は null。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec8ce-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="ec8ce-116">Return Value</span></span>  
  
|<span data-ttu-id="ec8ce-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec8ce-117">HRESULT</span></span>|<span data-ttu-id="ec8ce-118">説明</span><span class="sxs-lookup"><span data-stu-id="ec8ce-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec8ce-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec8ce-119">S_OK</span></span>|<span data-ttu-id="ec8ce-120">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="ec8ce-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ec8ce-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ec8ce-122">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ec8ce-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ec8ce-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ec8ce-124">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-124">The call timed out.</span></span>|  
|<span data-ttu-id="ec8ce-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ec8ce-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ec8ce-126">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ec8ce-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ec8ce-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ec8ce-128">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ec8ce-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ec8ce-129">E_FAIL</span></span>|<span data-ttu-id="ec8ce-130">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ec8ce-131">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ec8ce-132">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ec8ce-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="ec8ce-133">E_NOINTERFACE</span></span>|<span data-ttu-id="ec8ce-134">インターフェイス型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec8ce-135">要件</span><span class="sxs-lookup"><span data-stu-id="ec8ce-135">Requirements</span></span>  
 <span data-ttu-id="ec8ce-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec8ce-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec8ce-137">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ec8ce-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec8ce-138">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ec8ce-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec8ce-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec8ce-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec8ce-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec8ce-140">See also</span></span>

- [<span data-ttu-id="ec8ce-141">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec8ce-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="ec8ce-142">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec8ce-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
