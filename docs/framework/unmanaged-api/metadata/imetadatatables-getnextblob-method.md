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
ms.openlocfilehash: 145fdde302e7e942ea77049b3faeabf60894dd94
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448409"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="f4349-102">IMetaDataTables::GetNextBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="f4349-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="f4349-103">テーブル内の次のバイナリラージオブジェクト (BLOB) のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f4349-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4349-104">構文</span><span class="sxs-lookup"><span data-stu-id="f4349-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4349-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4349-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="f4349-106">からBlob の列から返されるインデックス。</span><span class="sxs-lookup"><span data-stu-id="f4349-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="f4349-107">入出力次の BLOB のインデックスを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="f4349-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4349-108">要件</span><span class="sxs-lookup"><span data-stu-id="f4349-108">Requirements</span></span>  
 <span data-ttu-id="f4349-109">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4349-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4349-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f4349-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4349-111">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4349-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4349-112">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4349-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4349-113">参照</span><span class="sxs-lookup"><span data-stu-id="f4349-113">See also</span></span>

- [<span data-ttu-id="f4349-114">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4349-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="f4349-115">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4349-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
