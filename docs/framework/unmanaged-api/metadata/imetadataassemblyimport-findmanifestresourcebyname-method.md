---
title: IMetaDataAssemblyImport::FindManifestResourceByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
ms.openlocfilehash: f0c390509a698fdc4682ba81182d4b407d8718c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448257"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="dee50-102">IMetaDataAssemblyImport::FindManifestResourceByName メソッド</span><span class="sxs-lookup"><span data-stu-id="dee50-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="dee50-103">指定した名前のマニフェストリソースへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="dee50-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee50-104">構文</span><span class="sxs-lookup"><span data-stu-id="dee50-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="dee50-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dee50-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="dee50-106">からリソースの名前。</span><span class="sxs-lookup"><span data-stu-id="dee50-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="dee50-107">入出力`mdManifestResource` メタデータトークンを格納するために使用される配列。それぞれがマニフェストリソースを表します。</span><span class="sxs-lookup"><span data-stu-id="dee50-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dee50-108">コメント</span><span class="sxs-lookup"><span data-stu-id="dee50-108">Remarks</span></span>  
 <span data-ttu-id="dee50-109">`FindManifestResourceByName` メソッドは、参照を解決するために共通言語ランタイムによって採用されている標準の規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="dee50-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dee50-110">要件</span><span class="sxs-lookup"><span data-stu-id="dee50-110">Requirements</span></span>  
 <span data-ttu-id="dee50-111">**プラットフォーム:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dee50-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dee50-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="dee50-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dee50-113">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="dee50-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dee50-114">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dee50-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee50-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="dee50-115">See also</span></span>

- [<span data-ttu-id="dee50-116">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dee50-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="dee50-117">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="dee50-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
