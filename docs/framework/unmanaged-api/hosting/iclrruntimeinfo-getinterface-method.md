---
title: ICLRRuntimeInfo::GetInterface メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
ms.openlocfilehash: 9cf9d48bf50ffc1fc56270c13215acfef6d9c3af
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504057"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="6b520-102">ICLRRuntimeInfo::GetInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="6b520-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="6b520-103">現在のプロセスに CLR を読み込み、 [ICLRRuntimeHost](iclrruntimehost-interface.md)、 [ICLRStrongName](iclrstrongname-interface.md)、 [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md)などのランタイムインターフェイスポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="6b520-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md), and [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="6b520-104">このメソッドは、 `CorBindTo` 「[非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)」セクションのすべての \* 関数を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6b520-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b520-105">構文</span><span class="sxs-lookup"><span data-stu-id="6b520-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b520-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b520-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="6b520-107">からコクラスの CLSID インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="6b520-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="6b520-108">から要求されたインターフェイスの IID `rclsid` 。</span><span class="sxs-lookup"><span data-stu-id="6b520-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="6b520-109">入出力クエリされたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b520-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b520-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="6b520-110">Return Value</span></span>  
 <span data-ttu-id="6b520-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="6b520-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6b520-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b520-112">HRESULT</span></span>|<span data-ttu-id="6b520-113">説明</span><span class="sxs-lookup"><span data-stu-id="6b520-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b520-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b520-114">S_OK</span></span>|<span data-ttu-id="6b520-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="6b520-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="6b520-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6b520-116">E_POINTER</span></span>|<span data-ttu-id="6b520-117">`ppUnk` が null です。</span><span class="sxs-lookup"><span data-stu-id="6b520-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="6b520-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6b520-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6b520-119">要求を処理するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="6b520-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="6b520-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="6b520-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="6b520-121">以前の CLR バージョン2のアクティブ化ポリシーに、別のランタイムが既にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="6b520-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b520-122">解説</span><span class="sxs-lookup"><span data-stu-id="6b520-122">Remarks</span></span>  
 <span data-ttu-id="6b520-123">このメソッドを使用すると、CLR が読み込まれますが、初期化されません。</span><span class="sxs-lookup"><span data-stu-id="6b520-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="6b520-124">次の表は、とでサポートされている組み合わせを示して `rclsid` `riid` います。</span><span class="sxs-lookup"><span data-stu-id="6b520-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="6b520-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="6b520-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="6b520-126">IID_IMetaDataDispenser、IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="6b520-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="6b520-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="6b520-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="6b520-128">IID_IMetaDataDispenser、IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="6b520-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="6b520-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6b520-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="6b520-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6b520-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="6b520-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6b520-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="6b520-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6b520-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="6b520-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="6b520-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="6b520-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="6b520-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="6b520-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="6b520-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="6b520-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="6b520-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="6b520-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6b520-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="6b520-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6b520-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b520-139">要件</span><span class="sxs-lookup"><span data-stu-id="6b520-139">Requirements</span></span>  
 <span data-ttu-id="6b520-140">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b520-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b520-141">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="6b520-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6b520-142">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6b520-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b520-143">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b520-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b520-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b520-144">See also</span></span>

- [<span data-ttu-id="6b520-145">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b520-145">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="6b520-146">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b520-146">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6b520-147">ホスティング</span><span class="sxs-lookup"><span data-stu-id="6b520-147">Hosting</span></span>](index.md)
