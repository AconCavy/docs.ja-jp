---
title: LoadStringRC 関数
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 8bd0292ddf22453f8892ed8bddd10c2144877097
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008517"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="9d5c6-102">LoadStringRC 関数</span><span class="sxs-lookup"><span data-stu-id="9d5c6-102">LoadStringRC Function</span></span>
<span data-ttu-id="9d5c6-103">現在のスレッドの既定のカルチャを使用して、HRESULT 値をエラー メッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="9d5c6-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d5c6-105">構文</span><span class="sxs-lookup"><span data-stu-id="9d5c6-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d5c6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d5c6-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="9d5c6-107">からHRESULT。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="9d5c6-108">入出力正常に完了したときのエラーメッセージを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="9d5c6-109">からエラーメッセージバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="9d5c6-110">から無効.</span><span class="sxs-lookup"><span data-stu-id="9d5c6-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d5c6-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="9d5c6-111">Return Value</span></span>  
 <span data-ttu-id="9d5c6-112">このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="9d5c6-113">リターン コード</span><span class="sxs-lookup"><span data-stu-id="9d5c6-113">Return code</span></span>|<span data-ttu-id="9d5c6-114">説明</span><span class="sxs-lookup"><span data-stu-id="9d5c6-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9d5c6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d5c6-115">S_OK</span></span>|<span data-ttu-id="9d5c6-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="9d5c6-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9d5c6-117">E_INVALIDARG</span></span>|<span data-ttu-id="9d5c6-118">`szBuffer`が null または `iMax` がゼロ (0) です。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d5c6-119">コメント</span><span class="sxs-lookup"><span data-stu-id="9d5c6-119">Remarks</span></span>  
 <span data-ttu-id="9d5c6-120">メソッドが正常に完了しなかった場合、には `szBuffer` 空の文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d5c6-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="9d5c6-121">Requirements</span></span>  
 <span data-ttu-id="9d5c6-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d5c6-123">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9d5c6-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d5c6-124">**ライブラリ:** Mscoree.dll と Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="9d5c6-125">Mscorwks.dll の代わりに Mscoree.dll を使用して、.NET Framework の正しいバージョンをターゲットにするようにしてください。</span><span class="sxs-lookup"><span data-stu-id="9d5c6-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="9d5c6-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d5c6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d5c6-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d5c6-127">See also</span></span>

- [<span data-ttu-id="9d5c6-128">LoadStringRCEx 関数</span><span class="sxs-lookup"><span data-stu-id="9d5c6-128">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)
- [<span data-ttu-id="9d5c6-129">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="9d5c6-129">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
