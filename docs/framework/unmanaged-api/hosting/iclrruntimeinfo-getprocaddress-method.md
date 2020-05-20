---
title: ICLRRuntimeInfo::GetProcAddress メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: 2690a5c2e7c499d68ef9e903c62bff8f85e72e8e
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703870"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="5fa12-102">ICLRRuntimeInfo::GetProcAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="5fa12-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="5fa12-103">このインターフェイスに関連付けられている共通言語ランタイム (CLR) からエクスポートされた、指定された関数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5fa12-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="5fa12-104">このメソッドは、 [GetRealProcAddress](getrealprocaddress-function.md)関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="5fa12-104">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fa12-105">構文</span><span class="sxs-lookup"><span data-stu-id="5fa12-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fa12-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5fa12-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="5fa12-107">からエクスポートされた関数の名前。</span><span class="sxs-lookup"><span data-stu-id="5fa12-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="5fa12-108">入出力エクスポートされた関数のアドレス。</span><span class="sxs-lookup"><span data-stu-id="5fa12-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fa12-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="5fa12-109">Return Value</span></span>  
 <span data-ttu-id="5fa12-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="5fa12-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5fa12-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5fa12-111">HRESULT</span></span>|<span data-ttu-id="5fa12-112">説明</span><span class="sxs-lookup"><span data-stu-id="5fa12-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5fa12-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5fa12-113">S_OK</span></span>|<span data-ttu-id="5fa12-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="5fa12-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5fa12-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5fa12-115">E_POINTER</span></span>|<span data-ttu-id="5fa12-116">`pszProcName` または `ppProc` が null です。</span><span class="sxs-lookup"><span data-stu-id="5fa12-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="5fa12-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="5fa12-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="5fa12-118">指定された関数はエクスポートされた関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="5fa12-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fa12-119">解説</span><span class="sxs-lookup"><span data-stu-id="5fa12-119">Remarks</span></span>  
 <span data-ttu-id="5fa12-120">このメソッドを使用すると、CLR が読み込まれますが、初期化されません。</span><span class="sxs-lookup"><span data-stu-id="5fa12-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fa12-121">要件</span><span class="sxs-lookup"><span data-stu-id="5fa12-121">Requirements</span></span>  
 <span data-ttu-id="5fa12-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fa12-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fa12-123">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="5fa12-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5fa12-124">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5fa12-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fa12-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fa12-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa12-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fa12-126">See also</span></span>

- [<span data-ttu-id="5fa12-127">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5fa12-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="5fa12-128">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5fa12-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="5fa12-129">ホスティング</span><span class="sxs-lookup"><span data-stu-id="5fa12-129">Hosting</span></span>](index.md)
