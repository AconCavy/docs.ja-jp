---
title: IAssemblyCacheItem インターフェイス
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
ms.openlocfilehash: 72922d1fd0f8ae5e59fe76c7aa50f9c52dcd5302
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719945"
---
# <a name="iassemblycacheitem-interface"></a>IAssemblyCacheItem インターフェイス

グローバルアセンブリキャッシュ内の1つのアセンブリを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AbortItem メソッド](iassemblycacheitem-abortitem-method.md)|アセンブリが解放される前に、グローバルアセンブリキャッシュ内のアセンブリでクリーンアップ操作を実行できるようにします。|  
|[Commit メソッド](iassemblycacheitem-commit-method.md)|キャッシュされたアセンブリ参照をメモリにコミットします。|  
|[CreateStream メソッド](iassemblycacheitem-createstream-method.md)|指定された名前と形式を使用してストリームを作成します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [グローバル アセンブリ キャッシュ](../../app-domains/gac.md)
- [IAssemblyCache インターフェイス](iassemblycache-interface.md)
