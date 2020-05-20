---
title: ICLRReferenceAssemblyEnum::Get メソッド
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
ms.openlocfilehash: 5afa7b37b804b6a11a894e0e6c7708c7787a20ae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703367"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="2e02b-102">ICLRReferenceAssemblyEnum::Get メソッド</span><span class="sxs-lookup"><span data-stu-id="2e02b-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="2e02b-103">指定されたインデックス位置にあるアセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="2e02b-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e02b-104">構文</span><span class="sxs-lookup"><span data-stu-id="2e02b-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e02b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e02b-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="2e02b-106">から返されるアセンブリ id の0から始まるインデックス。</span><span class="sxs-lookup"><span data-stu-id="2e02b-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="2e02b-107">入出力アセンブリ id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="2e02b-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="2e02b-108">[入力、出力]バッファーのサイズ `pwzBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="2e02b-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e02b-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="2e02b-109">Return Value</span></span>  
  
|<span data-ttu-id="2e02b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e02b-110">HRESULT</span></span>|<span data-ttu-id="2e02b-111">説明</span><span class="sxs-lookup"><span data-stu-id="2e02b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e02b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e02b-112">S_OK</span></span>|<span data-ttu-id="2e02b-113">`Get`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="2e02b-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="2e02b-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2e02b-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="2e02b-115">`pwzBuffer` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="2e02b-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="2e02b-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="2e02b-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="2e02b-117">列挙には、これ以上項目が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="2e02b-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="2e02b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2e02b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2e02b-119">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="2e02b-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2e02b-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2e02b-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2e02b-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2e02b-121">The call timed out.</span></span>|  
|<span data-ttu-id="2e02b-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e02b-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2e02b-123">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2e02b-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2e02b-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2e02b-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2e02b-125">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="2e02b-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2e02b-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e02b-126">E_FAIL</span></span>|<span data-ttu-id="2e02b-127">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2e02b-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2e02b-128">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="2e02b-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2e02b-129">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="2e02b-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e02b-130">解説</span><span class="sxs-lookup"><span data-stu-id="2e02b-130">Remarks</span></span>  
 <span data-ttu-id="2e02b-131">`Get`は通常、2回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2e02b-131">`Get` is typically called twice.</span></span> <span data-ttu-id="2e02b-132">最初の呼び出しでは、に null 値を指定し、に `pwzBuffer` `pcchBufferSize` 適したサイズに設定し `pwzBuffer` ます。</span><span class="sxs-lookup"><span data-stu-id="2e02b-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="2e02b-133">2番目の呼び出しでは、適切にサイズ `pwzBuffer` を指定し、完了時に正規のアセンブリ id データを格納します。</span><span class="sxs-lookup"><span data-stu-id="2e02b-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e02b-134">要件</span><span class="sxs-lookup"><span data-stu-id="2e02b-134">Requirements</span></span>  
 <span data-ttu-id="2e02b-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e02b-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e02b-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2e02b-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e02b-137">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2e02b-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e02b-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e02b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e02b-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e02b-139">See also</span></span>

- [<span data-ttu-id="2e02b-140">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e02b-140">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="2e02b-141">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e02b-141">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
