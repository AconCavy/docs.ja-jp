---
title: IHostAssemblyManager::GetNonHostStoreAssemblies メソッド
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
ms.openlocfilehash: 9a1440be7011130b16d7112ae15026eb74856190
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501595"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="b9a57-102">IHostAssemblyManager::GetNonHostStoreAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="b9a57-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="b9a57-103">ホストが読み込みのために共通言語ランタイム (CLR) を必要とするアセンブリのリストを表す[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b9a57-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a57-104">構文</span><span class="sxs-lookup"><span data-stu-id="b9a57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9a57-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b9a57-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="b9a57-106">入出力`ICLRAssemblyReferenceList`ホストが CLR を読み込むことを想定しているアセンブリへの参照の一覧を含むのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b9a57-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9a57-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="b9a57-107">Return Value</span></span>  
  
|<span data-ttu-id="b9a57-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9a57-108">HRESULT</span></span>|<span data-ttu-id="b9a57-109">説明</span><span class="sxs-lookup"><span data-stu-id="b9a57-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9a57-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9a57-110">S_OK</span></span>|<span data-ttu-id="b9a57-111">`GetNonHostStoreAssemblies`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="b9a57-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="b9a57-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9a57-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9a57-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="b9a57-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9a57-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9a57-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9a57-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b9a57-115">The call timed out.</span></span>|  
|<span data-ttu-id="b9a57-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9a57-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9a57-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="b9a57-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9a57-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9a57-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9a57-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="b9a57-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9a57-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9a57-120">E_FAIL</span></span>|<span data-ttu-id="b9a57-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b9a57-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9a57-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="b9a57-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9a57-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="b9a57-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b9a57-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b9a57-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b9a57-125">要求されたの参照の一覧を作成するのに十分なメモリがありませんでした `ICLRAssemblyReferenceList` 。</span><span class="sxs-lookup"><span data-stu-id="b9a57-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9a57-126">解説</span><span class="sxs-lookup"><span data-stu-id="b9a57-126">Remarks</span></span>  
 <span data-ttu-id="b9a57-127">CLR は、次の一連のガイドラインを使用して参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="b9a57-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="b9a57-128">まず、によって返されるアセンブリ参照の一覧を参照し `GetNonHostStoreAssemblies` ます。</span><span class="sxs-lookup"><span data-stu-id="b9a57-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="b9a57-129">アセンブリが一覧に表示されている場合、CLR は通常どおりにバインドします。</span><span class="sxs-lookup"><span data-stu-id="b9a57-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="b9a57-130">アセンブリが一覧に表示されず、ホストが[IHostAssemblyStore](ihostassemblystore-interface.md)の実装を提供した場合、CLR は[IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md)を呼び出して、バインド先のアセンブリをホストが指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b9a57-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="b9a57-131">それ以外の場合、CLR はアセンブリへのバインドに失敗します。</span><span class="sxs-lookup"><span data-stu-id="b9a57-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="b9a57-132">ホストが null に設定されている場合、 `ppReferenceList` CLR はまずグローバルアセンブリキャッシュをプローブし、 `ProvideAssembly` を呼び出してから、アプリケーションベースをプローブしてアセンブリ参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="b9a57-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9a57-133">初期化時に、CLR は `GetNonHostStoreAssemblies` 1 回だけを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b9a57-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="b9a57-134">メソッドが再度呼び出されていません。</span><span class="sxs-lookup"><span data-stu-id="b9a57-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9a57-135">要件</span><span class="sxs-lookup"><span data-stu-id="b9a57-135">Requirements</span></span>  
 <span data-ttu-id="b9a57-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9a57-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9a57-137">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b9a57-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9a57-138">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b9a57-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9a57-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9a57-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a57-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9a57-140">See also</span></span>

- [<span data-ttu-id="b9a57-141">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b9a57-141">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b9a57-142">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b9a57-142">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="b9a57-143">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b9a57-143">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
