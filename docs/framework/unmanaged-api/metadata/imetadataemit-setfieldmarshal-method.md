---
title: IMetaDataEmit::SetFieldMarshal メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: d0066c6590a9e0cf278e036111c2739f7cfaf679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003907"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="e1bfd-102">IMetaDataEmit::SetFieldMarshal メソッド</span><span class="sxs-lookup"><span data-stu-id="e1bfd-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="e1bfd-103">指定したトークンによって参照されるフィールド、メソッドの戻り値、またはメソッドパラメーターの PInvoke マーシャリング情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="e1bfd-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1bfd-104">構文</span><span class="sxs-lookup"><span data-stu-id="e1bfd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1bfd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e1bfd-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e1bfd-106">からターゲットデータ項目のトークン。</span><span class="sxs-lookup"><span data-stu-id="e1bfd-106">[in] The token for target data item.</span></span> <span data-ttu-id="e1bfd-107">これは、 `mdFieldDef` またはトークンのいずれか `mdParamDef` です。</span><span class="sxs-lookup"><span data-stu-id="e1bfd-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="e1bfd-108">からアンマネージ型のシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="e1bfd-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="e1bfd-109">からのバイト数 `pvNativeType` 。</span><span class="sxs-lookup"><span data-stu-id="e1bfd-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1bfd-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="e1bfd-110">Requirements</span></span>  
 <span data-ttu-id="e1bfd-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1bfd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1bfd-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e1bfd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1bfd-113">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1bfd-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1bfd-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1bfd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1bfd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1bfd-115">See also</span></span>

- [<span data-ttu-id="e1bfd-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e1bfd-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e1bfd-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e1bfd-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
