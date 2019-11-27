---
title: Init メソッド
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
ms.openlocfilehash: 986ae69e7ebb8f607be5d37fab426bcc787abb26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445640"
---
# <a name="init-method"></a><span data-ttu-id="3d068-102">Init メソッド</span><span class="sxs-lookup"><span data-stu-id="3d068-102">Init Method</span></span>
<span data-ttu-id="3d068-103">使用する[Ialink インターフェイス](ialink-interface.md)を実装するオブジェクトを準備します。</span><span class="sxs-lookup"><span data-stu-id="3d068-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d068-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d068-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d068-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d068-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="3d068-106">[IMetaDataDispenserEx インターフェイス](../metadata/imetadatadispenserex-interface.md)のメタデータディスペンサーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3d068-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="3d068-107">[IMetaDataError インターフェイス](../metadata/imetadataerror-interface.md)は、省略可能なエラー処理インターフェイスへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="3d068-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d068-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3d068-108">Return Value</span></span>  
 <span data-ttu-id="3d068-109">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="3d068-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d068-110">要件</span><span class="sxs-lookup"><span data-stu-id="3d068-110">Requirements</span></span>  
 <span data-ttu-id="3d068-111">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="3d068-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d068-112">参照</span><span class="sxs-lookup"><span data-stu-id="3d068-112">See also</span></span>

- [<span data-ttu-id="3d068-113">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d068-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3d068-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d068-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3d068-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="3d068-115">ALink API</span></span>](index.md)
