---
title: ICLRRuntimeInfo::LoadLibrary メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
ms.openlocfilehash: 09c80c3a56d86943ebe00e5222bb5452ab44e150
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762176"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="94eba-102">ICLRRuntimeInfo::LoadLibrary メソッド</span><span class="sxs-lookup"><span data-stu-id="94eba-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="94eba-103">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)インターフェイスによって表される共通言語ランタイム (CLR) から .NET Framework ライブラリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="94eba-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="94eba-104">このメソッドは、 [LoadLibraryShim](loadlibraryshim-function.md)関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="94eba-104">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94eba-105">構文</span><span class="sxs-lookup"><span data-stu-id="94eba-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94eba-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94eba-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="94eba-107">から読み込むアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="94eba-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="94eba-108">入出力読み込まれたアセンブリへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="94eba-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94eba-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="94eba-109">Return Value</span></span>  
 <span data-ttu-id="94eba-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="94eba-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="94eba-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94eba-111">HRESULT</span></span>|<span data-ttu-id="94eba-112">説明</span><span class="sxs-lookup"><span data-stu-id="94eba-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94eba-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="94eba-113">S_OK</span></span>|<span data-ttu-id="94eba-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="94eba-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="94eba-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="94eba-115">E_POINTER</span></span>|<span data-ttu-id="94eba-116">`pwzDllName` または `phndModule` が null です。</span><span class="sxs-lookup"><span data-stu-id="94eba-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="94eba-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="94eba-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="94eba-118">要求を処理するのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="94eba-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94eba-119">解説</span><span class="sxs-lookup"><span data-stu-id="94eba-119">Remarks</span></span>  
 <span data-ttu-id="94eba-120">このメソッドは、.NET Framework 再頒布可能パッケージに含まれている Dll のみを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="94eba-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="94eba-121">ユーザーが生成したアセンブリを読み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="94eba-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94eba-122">要件</span><span class="sxs-lookup"><span data-stu-id="94eba-122">Requirements</span></span>  
 <span data-ttu-id="94eba-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94eba-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94eba-124">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="94eba-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="94eba-125">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="94eba-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94eba-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94eba-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94eba-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="94eba-127">See also</span></span>

- [<span data-ttu-id="94eba-128">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94eba-128">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="94eba-129">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94eba-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="94eba-130">ホスティング</span><span class="sxs-lookup"><span data-stu-id="94eba-130">Hosting</span></span>](index.md)
