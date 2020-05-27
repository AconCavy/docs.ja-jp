---
title: IMetaDataEmit::SetPinvokeMap メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: 0d34c7a2992a2779b96ec87f1a0175d8fcbce34a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007794"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="72782-102">IMetaDataEmit::SetPinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="72782-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="72782-103">[IMetaDataEmit::D efinepinvokemap](imetadataemit-definepinvokemap-method.md)の前の呼び出しで定義されているように、メソッドの PInvoke 署名の機能を設定または変更します。</span><span class="sxs-lookup"><span data-stu-id="72782-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72782-104">構文</span><span class="sxs-lookup"><span data-stu-id="72782-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72782-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72782-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="72782-106">から`mdToken`マッピング情報が適用される。</span><span class="sxs-lookup"><span data-stu-id="72782-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="72782-107">からマッピングを行うために PInvoke によって使用されるフラグ。</span><span class="sxs-lookup"><span data-stu-id="72782-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="72782-108">これは、値のビットマスクです `CorPinvokeMap` 。</span><span class="sxs-lookup"><span data-stu-id="72782-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="72782-109">からネイティブ DLL 内のターゲットエクスポートの名前。</span><span class="sxs-lookup"><span data-stu-id="72782-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="72782-110">から`mdModuleRef`ターゲットのアンマネージ DLL のトークン。</span><span class="sxs-lookup"><span data-stu-id="72782-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72782-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="72782-111">Requirements</span></span>  
 <span data-ttu-id="72782-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72782-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72782-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="72782-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72782-114">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="72782-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72782-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72782-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72782-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="72782-116">See also</span></span>

- [<span data-ttu-id="72782-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72782-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="72782-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72782-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
