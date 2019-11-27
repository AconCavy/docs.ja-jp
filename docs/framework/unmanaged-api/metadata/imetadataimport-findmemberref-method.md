---
title: IMetaDataImport::FindMemberRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: 59512cc1c1b280d7fe6deb2f9d721ad53547e356
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437959"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="693e9-102">IMetaDataImport::FindMemberRef メソッド</span><span class="sxs-lookup"><span data-stu-id="693e9-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="693e9-103">指定した <xref:System.Type> で囲まれ、指定された名前とメタデータシグネチャを持つメンバー参照の MemberRef トークンへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="693e9-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="693e9-104">構文</span><span class="sxs-lookup"><span data-stu-id="693e9-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="693e9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="693e9-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="693e9-106">から検索対象のメンバー参照を囲むクラスまたはインターフェイスの TypeRef トークン。</span><span class="sxs-lookup"><span data-stu-id="693e9-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="693e9-107">この値が `mdTokenNil`場合、グローバル変数またはグローバル関数参照に対して参照が行われます。</span><span class="sxs-lookup"><span data-stu-id="693e9-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="693e9-108">から検索対象のメンバー参照の名前。</span><span class="sxs-lookup"><span data-stu-id="693e9-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="693e9-109">からメンバー参照のバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="693e9-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="693e9-110">から`pvSigBlob`のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="693e9-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="693e9-111">入出力一致する MemberRef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="693e9-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="693e9-112">コメント</span><span class="sxs-lookup"><span data-stu-id="693e9-112">Remarks</span></span>  
 <span data-ttu-id="693e9-113">メンバーは、外側のクラスまたはインターフェイス (`td`)、その名前 (`szName`)、および必要に応じてシグネチャ (`pvSigBlob`) を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="693e9-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="693e9-114">シグネチャは特定のスコープにバインドされているため、`FindMemberRef` に渡される署名は、現在のスコープで生成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="693e9-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="693e9-115">署名には、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="693e9-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="693e9-116">トークンは、ローカルの TypeDef テーブルのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="693e9-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="693e9-117">現在のスコープのコンテキスト外でランタイムシグネチャを作成し、その署名を `FindMemberRef`の入力として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="693e9-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="693e9-118">`FindMemberRef` は、クラスまたはインターフェイスで直接定義されたメンバー参照だけを検索します。継承されたメンバー参照は見つかりません。</span><span class="sxs-lookup"><span data-stu-id="693e9-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="693e9-119">要件</span><span class="sxs-lookup"><span data-stu-id="693e9-119">Requirements</span></span>  
 <span data-ttu-id="693e9-120">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="693e9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="693e9-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="693e9-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="693e9-122">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="693e9-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="693e9-123">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="693e9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="693e9-124">参照</span><span class="sxs-lookup"><span data-stu-id="693e9-124">See also</span></span>

- [<span data-ttu-id="693e9-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="693e9-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="693e9-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="693e9-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
