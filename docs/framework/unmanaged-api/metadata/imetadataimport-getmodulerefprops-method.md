---
title: IMetaDataImport::GetModuleRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: f1784c9f3085ce188f9e540887dd02064f8448f3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503579"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="40c9e-102">IMetaDataImport::GetModuleRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="40c9e-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="40c9e-103">指定したメタデータ トークンによって参照されるモジュールの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="40c9e-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c9e-104">構文</span><span class="sxs-lookup"><span data-stu-id="40c9e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c9e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="40c9e-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="40c9e-106">からメタデータ情報を取得するモジュールを参照する ModuleRef メタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="40c9e-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="40c9e-107">入出力モジュール名を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="40c9e-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="40c9e-108">から要求されたサイズ ( `szName` ワイド文字単位)。</span><span class="sxs-lookup"><span data-stu-id="40c9e-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="40c9e-109">入出力返されたのサイズを `szName` ワイド文字数で返します。</span><span class="sxs-lookup"><span data-stu-id="40c9e-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c9e-110">要件</span><span class="sxs-lookup"><span data-stu-id="40c9e-110">Requirements</span></span>  
 <span data-ttu-id="40c9e-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40c9e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c9e-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="40c9e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40c9e-113">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="40c9e-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40c9e-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40c9e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c9e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="40c9e-115">See also</span></span>

- [<span data-ttu-id="40c9e-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40c9e-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="40c9e-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40c9e-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
