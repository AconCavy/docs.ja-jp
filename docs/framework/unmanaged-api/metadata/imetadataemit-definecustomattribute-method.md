---
title: IMetaDataEmit::DefineCustomAttribute メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: e6a732b98ae02ba2b273b45921b7de61ab4fd29f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432641"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="bfbe5-102">IMetaDataEmit::DefineCustomAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="bfbe5-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="bfbe5-103">指定したメタデータシグネチャを使用して、指定したオブジェクトにアタッチするカスタム属性の定義を作成し、そのカスタム属性定義へのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="bfbe5-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfbe5-104">構文</span><span class="sxs-lookup"><span data-stu-id="bfbe5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfbe5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bfbe5-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="bfbe5-106">から所有者項目のトークン。</span><span class="sxs-lookup"><span data-stu-id="bfbe5-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="bfbe5-107">からカスタム属性を識別するトークン。</span><span class="sxs-lookup"><span data-stu-id="bfbe5-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="bfbe5-108">からカスタム属性へのポインター。</span><span class="sxs-lookup"><span data-stu-id="bfbe5-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="bfbe5-109">から`pCustomAttribute`内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="bfbe5-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="bfbe5-110">入出力割り当てられた `mdCustomAttribute` トークン。</span><span class="sxs-lookup"><span data-stu-id="bfbe5-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfbe5-111">要件</span><span class="sxs-lookup"><span data-stu-id="bfbe5-111">Requirements</span></span>  
 <span data-ttu-id="bfbe5-112">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfbe5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfbe5-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="bfbe5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bfbe5-114">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="bfbe5-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfbe5-115">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfbe5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfbe5-116">参照</span><span class="sxs-lookup"><span data-stu-id="bfbe5-116">See also</span></span>

- [<span data-ttu-id="bfbe5-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfbe5-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bfbe5-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfbe5-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
