---
title: IMetaDataImport::EnumParams メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: f9a58a70b5264d7f1eb33fb0e09c702c94a13e85
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491765"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="52b39-102">IMetaDataImport::EnumParams メソッド</span><span class="sxs-lookup"><span data-stu-id="52b39-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="52b39-103">指定した MethodDef トークンによって参照されるメソッドのパラメーターを表す ParamDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="52b39-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52b39-104">構文</span><span class="sxs-lookup"><span data-stu-id="52b39-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52b39-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52b39-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="52b39-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="52b39-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="52b39-107">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="52b39-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="52b39-108">から列挙するパラメーターを使用してメソッドを表す MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="52b39-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="52b39-109">入出力ParamDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="52b39-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="52b39-110">[in] `rParams` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="52b39-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="52b39-111">入出力で返された ParamDef トークンの数 `rParams` 。</span><span class="sxs-lookup"><span data-stu-id="52b39-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52b39-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="52b39-112">Return Value</span></span>  
  
|<span data-ttu-id="52b39-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52b39-113">HRESULT</span></span>|<span data-ttu-id="52b39-114">説明</span><span class="sxs-lookup"><span data-stu-id="52b39-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="52b39-115">`EnumParams`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="52b39-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="52b39-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="52b39-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="52b39-117">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="52b39-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52b39-118">要件</span><span class="sxs-lookup"><span data-stu-id="52b39-118">Requirements</span></span>  
 <span data-ttu-id="52b39-119">**プラットフォーム:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52b39-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52b39-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="52b39-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52b39-121">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="52b39-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52b39-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52b39-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b39-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="52b39-123">See also</span></span>

- [<span data-ttu-id="52b39-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52b39-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="52b39-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52b39-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
