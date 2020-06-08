---
title: ICLRStrongName::StrongNameFreeBuffer メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: 7aed3e6877bfcd83754d462cdba81ccc229d002f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504005"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="68ce2-102">ICLRStrongName::StrongNameFreeBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="68ce2-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="68ce2-103">[ICLRStrongName:: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md)、 [ICLRStrongName:: StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md)、 [ICLRStrongName:: StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md)などの厳密な名前のメソッドへの前回の呼び出しで割り当てられたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="68ce2-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68ce2-104">構文</span><span class="sxs-lookup"><span data-stu-id="68ce2-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68ce2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68ce2-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="68ce2-106">から解放するメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="68ce2-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68ce2-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="68ce2-107">Return Value</span></span>  
 <span data-ttu-id="68ce2-108">`S_OK`メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの[一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="68ce2-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68ce2-109">要件</span><span class="sxs-lookup"><span data-stu-id="68ce2-109">Requirements</span></span>  
 <span data-ttu-id="68ce2-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68ce2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68ce2-111">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="68ce2-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="68ce2-112">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="68ce2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68ce2-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68ce2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68ce2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="68ce2-114">See also</span></span>

- [<span data-ttu-id="68ce2-115">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68ce2-115">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
