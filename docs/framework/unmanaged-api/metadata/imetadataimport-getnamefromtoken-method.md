---
title: IMetaDataImport::GetNameFromToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 6ed30f07fcec9c730e1514350c594399f0aa16e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437265"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="0570a-102">IMetaDataImport::GetNameFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="0570a-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="0570a-103">指定したメタデータ トークンによって参照されるオブジェクトの UTF-8 名を取得します。</span><span class="sxs-lookup"><span data-stu-id="0570a-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="0570a-104">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="0570a-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0570a-105">構文</span><span class="sxs-lookup"><span data-stu-id="0570a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0570a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0570a-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0570a-107">[in] The token representing the object to return the name for.</span><span class="sxs-lookup"><span data-stu-id="0570a-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="0570a-108">[out] A pointer to the UTF-8 object name in the heap.</span><span class="sxs-lookup"><span data-stu-id="0570a-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0570a-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="0570a-109">Remarks</span></span>  
 <span data-ttu-id="0570a-110">`GetNameFromToken` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="0570a-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="0570a-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span><span class="sxs-lookup"><span data-stu-id="0570a-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0570a-112">［要件］</span><span class="sxs-lookup"><span data-stu-id="0570a-112">Requirements</span></span>  
 <span data-ttu-id="0570a-113">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0570a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0570a-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0570a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0570a-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0570a-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0570a-116">**.NET Framework Versions:** 1.0</span><span class="sxs-lookup"><span data-stu-id="0570a-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0570a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0570a-117">See also</span></span>

- [<span data-ttu-id="0570a-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0570a-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0570a-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0570a-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
