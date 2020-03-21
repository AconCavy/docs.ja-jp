---
title: IMetaDataEmit::DefineTypeRefByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: 23a6931b31ea2d7e4e8d1cb3dc8adf3a51216315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175747"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="5378b-102">IMetaDataEmit::DefineTypeRefByName メソッド</span><span class="sxs-lookup"><span data-stu-id="5378b-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="5378b-103">現在のスコープの外側にある、指定したスコープで定義されている型のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="5378b-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5378b-104">構文</span><span class="sxs-lookup"><span data-stu-id="5378b-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5378b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5378b-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="5378b-106">[in]解決スコープを指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="5378b-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="5378b-107">次のトークンタイプが有効です。</span><span class="sxs-lookup"><span data-stu-id="5378b-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="5378b-108">`mdModuleRef`型が、呼び出し元が定義されているアセンブリと同じアセンブリで定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="5378b-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="5378b-109">`mdAssemblyRef`型が、呼び出し元が定義されているアセンブリ以外のアセンブリで定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="5378b-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="5378b-110">`mdTypeRef`の場合、その型が入れ子にされた型です。</span><span class="sxs-lookup"><span data-stu-id="5378b-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="5378b-111">`mdModule`型が、呼び出し元が定義されているモジュールと同じモジュールで定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="5378b-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="5378b-112">型がグローバルに定義されている場合は Null。</span><span class="sxs-lookup"><span data-stu-id="5378b-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="5378b-113">[in]ユニコードでのターゲット型の名前。</span><span class="sxs-lookup"><span data-stu-id="5378b-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="5378b-114">[アウト]型に割り`mdTypeRef`当てられているトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5378b-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5378b-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="5378b-115">Requirements</span></span>  
 <span data-ttu-id="5378b-116">**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5378b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5378b-117">**ヘッダー:** コル・h</span><span class="sxs-lookup"><span data-stu-id="5378b-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5378b-118">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="5378b-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5378b-119">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5378b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5378b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5378b-120">See also</span></span>

- [<span data-ttu-id="5378b-121">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5378b-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5378b-122">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5378b-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
