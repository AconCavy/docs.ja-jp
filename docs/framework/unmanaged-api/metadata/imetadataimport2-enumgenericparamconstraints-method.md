---
title: IMetaDataImport2::EnumGenericParamConstraints メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
ms.openlocfilehash: af226f9317b67b23e03d06614ed5b9c956939c22
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503420"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="7bef2-102">IMetaDataImport2::EnumGenericParamConstraints メソッド</span><span class="sxs-lookup"><span data-stu-id="7bef2-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="7bef2-103">指定したトークンによって表されるジェネリックパラメーターに関連付けられているジェネリックパラメーター制約の配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="7bef2-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bef2-104">構文</span><span class="sxs-lookup"><span data-stu-id="7bef2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bef2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7bef2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7bef2-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7bef2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="7bef2-107">から  制約を列挙するジェネリックパラメーターを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="7bef2-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="7bef2-108">入出力列挙するジェネリックパラメーター制約の配列。</span><span class="sxs-lookup"><span data-stu-id="7bef2-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7bef2-109">から  に格納するトークンの要求された最大数 `rGenericParamConstraints` 。</span><span class="sxs-lookup"><span data-stu-id="7bef2-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="7bef2-110">入出力に格納されているトークンの数へのポインター `rGenericParamConstraints` 。</span><span class="sxs-lookup"><span data-stu-id="7bef2-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bef2-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="7bef2-111">Return Value</span></span>  
  
|<span data-ttu-id="7bef2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bef2-112">HRESULT</span></span>|<span data-ttu-id="7bef2-113">説明</span><span class="sxs-lookup"><span data-stu-id="7bef2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7bef2-114">`EnumGenericParameterConstraints`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="7bef2-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7bef2-115">`phEnum`にメンバー要素がありません。</span><span class="sxs-lookup"><span data-stu-id="7bef2-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="7bef2-116">この場合、 `pcGenericParameterConstraints` は 0 (ゼロ) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="7bef2-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7bef2-117">要件</span><span class="sxs-lookup"><span data-stu-id="7bef2-117">Requirements</span></span>  
 <span data-ttu-id="7bef2-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bef2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bef2-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="7bef2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bef2-120">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="7bef2-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7bef2-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bef2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bef2-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="7bef2-122">See also</span></span>

- [<span data-ttu-id="7bef2-123">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7bef2-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="7bef2-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7bef2-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
