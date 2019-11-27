---
title: IMetaDataEmit::DeleteToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
ms.openlocfilehash: e8c145632911817e8e19d587bb8afead0a6c33af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434341"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="9b3e6-102">IMetaDataEmit::DeleteToken メソッド</span><span class="sxs-lookup"><span data-stu-id="9b3e6-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="9b3e6-103">現在のメタデータスコープから指定されたトークンを削除します。</span><span class="sxs-lookup"><span data-stu-id="9b3e6-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b3e6-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b3e6-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b3e6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b3e6-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="9b3e6-106">から削除するトークン。</span><span class="sxs-lookup"><span data-stu-id="9b3e6-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b3e6-107">要件</span><span class="sxs-lookup"><span data-stu-id="9b3e6-107">Requirements</span></span>  
 <span data-ttu-id="9b3e6-108">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b3e6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b3e6-109">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9b3e6-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b3e6-110">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="9b3e6-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b3e6-111">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b3e6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3e6-112">参照</span><span class="sxs-lookup"><span data-stu-id="9b3e6-112">See also</span></span>

- [<span data-ttu-id="9b3e6-113">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b3e6-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9b3e6-114">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b3e6-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
