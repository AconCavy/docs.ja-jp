---
title: CLRCreateInstance 関数
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
ms.openlocfilehash: c3011149b9b23e776ad3baac9e41f3c42213654d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616828"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="eaa7b-102">CLRCreateInstance 関数</span><span class="sxs-lookup"><span data-stu-id="eaa7b-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="eaa7b-103">には、 [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)、または[ICLRDebugging](../debugging/iclrdebugging-interface.md)の3つのインターフェイスのいずれかが用意されています。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa7b-104">構文</span><span class="sxs-lookup"><span data-stu-id="eaa7b-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaa7b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eaa7b-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="eaa7b-106">からCLSID_CLRMetaHost、CLSID_CLRMetaHostPolicy、または CLSID_CLRDebugging の3つのクラス識別子のいずれか。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="eaa7b-107">から3つのインターフェイス識別子 (Iid が) のいずれか。 IID_ICLRMetaHost、IID_ICLRMetaHostPolicy、または IID_ICLRDebugging です。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="eaa7b-108">入出力[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)、または[ICLRDebugging](../debugging/iclrdebugging-interface.md)の3つのインターフェイスのいずれか。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaa7b-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="eaa7b-109">Return Value</span></span>  
 <span data-ttu-id="eaa7b-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="eaa7b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eaa7b-111">HRESULT</span></span>|<span data-ttu-id="eaa7b-112">説明</span><span class="sxs-lookup"><span data-stu-id="eaa7b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eaa7b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="eaa7b-113">S_OK</span></span>|<span data-ttu-id="eaa7b-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="eaa7b-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="eaa7b-115">E_POINTER</span></span>|<span data-ttu-id="eaa7b-116">`ppInterface` が null です。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaa7b-117">解説</span><span class="sxs-lookup"><span data-stu-id="eaa7b-117">Remarks</span></span>  
 <span data-ttu-id="eaa7b-118">次の表は、とでサポートされている組み合わせを示して `clsid` `riid` います。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="eaa7b-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="eaa7b-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="eaa7b-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="eaa7b-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="eaa7b-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="eaa7b-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="eaa7b-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="eaa7b-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="eaa7b-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="eaa7b-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="eaa7b-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="eaa7b-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="eaa7b-125">次のコードは、を使用して3つすべてのインターフェイスを取得する方法を示してい `CLRCreateInstance` ます。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="eaa7b-126">要件</span><span class="sxs-lookup"><span data-stu-id="eaa7b-126">Requirements</span></span>  
 <span data-ttu-id="eaa7b-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaa7b-128">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="eaa7b-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="eaa7b-129">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="eaa7b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eaa7b-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaa7b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa7b-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="eaa7b-131">See also</span></span>

- [<span data-ttu-id="eaa7b-132">ホスティング</span><span class="sxs-lookup"><span data-stu-id="eaa7b-132">Hosting</span></span>](index.md)
