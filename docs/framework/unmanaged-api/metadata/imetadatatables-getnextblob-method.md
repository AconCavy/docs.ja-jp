---
title: IMetaDataTables::GetNextBlob メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: 086448248364403b718408ad8bd32e48447742d0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490382"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="028e6-102">IMetaDataTables::GetNextBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="028e6-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="028e6-103">テーブル内の次のバイナリラージオブジェクト (BLOB) のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="028e6-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028e6-104">構文</span><span class="sxs-lookup"><span data-stu-id="028e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="028e6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="028e6-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="028e6-106">からBlob の列から返されるインデックス。</span><span class="sxs-lookup"><span data-stu-id="028e6-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="028e6-107">入出力次の BLOB のインデックスを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="028e6-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="028e6-108">要件</span><span class="sxs-lookup"><span data-stu-id="028e6-108">Requirements</span></span>  
 <span data-ttu-id="028e6-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="028e6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="028e6-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="028e6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="028e6-111">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="028e6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="028e6-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="028e6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028e6-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="028e6-113">See also</span></span>

- [<span data-ttu-id="028e6-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="028e6-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="028e6-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="028e6-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
