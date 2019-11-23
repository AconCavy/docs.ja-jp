---
title: IMetaDataTables::GetCodedTokenInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
ms.openlocfilehash: 577a4f6bb8315cfb1cb462703dd0cb9b23b60704
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434061"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="ee2b9-102">IMetaDataTables::GetCodedTokenInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="ee2b9-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="ee2b9-103">Gets a pointer to an array of tokens associated with the specified row index.</span><span class="sxs-lookup"><span data-stu-id="ee2b9-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee2b9-104">構文</span><span class="sxs-lookup"><span data-stu-id="ee2b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee2b9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ee2b9-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="ee2b9-106">[in] The kind of coded token to return.</span><span class="sxs-lookup"><span data-stu-id="ee2b9-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ee2b9-107">[out] A pointer to the length of `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="ee2b9-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="ee2b9-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span><span class="sxs-lookup"><span data-stu-id="ee2b9-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="ee2b9-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="ee2b9-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee2b9-110">［要件］</span><span class="sxs-lookup"><span data-stu-id="ee2b9-110">Requirements</span></span>  
 <span data-ttu-id="ee2b9-111">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee2b9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee2b9-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ee2b9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee2b9-113">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee2b9-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee2b9-114">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee2b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2b9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee2b9-115">See also</span></span>

- [<span data-ttu-id="ee2b9-116">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee2b9-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ee2b9-117">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee2b9-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
