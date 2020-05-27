---
title: IMetaDataEmit::DefinePinvokeMap メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
ms.openlocfilehash: 447ec44ed3efc4eec84d1e4acd6f2ec1a730bf74
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008028"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="17cd0-102">IMetaDataEmit::DefinePinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="17cd0-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="17cd0-103">指定したトークンによって参照されるメソッドの PInvoke 署名の特徴を設定します。</span><span class="sxs-lookup"><span data-stu-id="17cd0-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17cd0-104">構文</span><span class="sxs-lookup"><span data-stu-id="17cd0-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17cd0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17cd0-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="17cd0-106">からターゲットメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="17cd0-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="17cd0-107">からマッピングを行うために PInvoke によって使用されるフラグ。</span><span class="sxs-lookup"><span data-stu-id="17cd0-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="17cd0-108">からアンマネージ DLL 内の対象のエクスポートメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="17cd0-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="17cd0-109">からターゲットのネイティブ DLL のトークン。</span><span class="sxs-lookup"><span data-stu-id="17cd0-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17cd0-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="17cd0-110">Requirements</span></span>  
 <span data-ttu-id="17cd0-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17cd0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17cd0-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="17cd0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17cd0-113">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="17cd0-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17cd0-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17cd0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cd0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="17cd0-115">See also</span></span>

- [<span data-ttu-id="17cd0-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17cd0-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="17cd0-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17cd0-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
