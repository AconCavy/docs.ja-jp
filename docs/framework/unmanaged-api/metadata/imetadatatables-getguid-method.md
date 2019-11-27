---
title: IMetaDataTables::GetGuid メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 1f0c52efd4b55d19cbd7b2407c4b2d7c893b1009
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436087"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="85f16-102">IMetaDataTables::GetGuid メソッド</span><span class="sxs-lookup"><span data-stu-id="85f16-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="85f16-103">指定したインデックス位置にある行から GUID を取得します。</span><span class="sxs-lookup"><span data-stu-id="85f16-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f16-104">構文</span><span class="sxs-lookup"><span data-stu-id="85f16-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85f16-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="85f16-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="85f16-106">からGUID の取得元となる行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="85f16-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="85f16-107">入出力GUID へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="85f16-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85f16-108">コメント</span><span class="sxs-lookup"><span data-stu-id="85f16-108">Remarks</span></span>  
 <span data-ttu-id="85f16-109">このメソッドは、一貫性のある結果を返さないため、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="85f16-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="85f16-110">GUID テーブルの詳細については、共通言語基盤 (CLI) のドキュメント (特に「パーティション II: メタデータの定義とセマンティクス」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85f16-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="85f16-111">ドキュメントはオンラインで入手できます。MSDN の「[ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212)」 (ECMA の C# および共通言語基盤の標準規格) と、ECMA のインターナショナル Web サイトにある「[Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85f16-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f16-112">要件</span><span class="sxs-lookup"><span data-stu-id="85f16-112">Requirements</span></span>  
 <span data-ttu-id="85f16-113">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85f16-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85f16-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="85f16-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85f16-115">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="85f16-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85f16-116">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85f16-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f16-117">参照</span><span class="sxs-lookup"><span data-stu-id="85f16-117">See also</span></span>

- [<span data-ttu-id="85f16-118">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85f16-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="85f16-119">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85f16-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
