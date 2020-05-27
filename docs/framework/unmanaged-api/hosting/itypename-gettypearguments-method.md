---
title: ITypeName::GetTypeArguments メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
ms.openlocfilehash: e059cdddef7926c1359a83bc562146203724aa60
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842116"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="d244d-102">ITypeName::GetTypeArguments メソッド</span><span class="sxs-lookup"><span data-stu-id="d244d-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="d244d-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="d244d-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d244d-104">構文</span><span class="sxs-lookup"><span data-stu-id="d244d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d244d-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="d244d-105">Requirements</span></span>  
 <span data-ttu-id="d244d-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d244d-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d244d-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d244d-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d244d-108">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d244d-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d244d-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d244d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d244d-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d244d-110">See also</span></span>

- [<span data-ttu-id="d244d-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d244d-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
