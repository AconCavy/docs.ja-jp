---
title: IEnumDefinitionIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bbd8476b7778de6d0023f3a8522a44be6626884
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751520"
---
# <a name="ienumdefinitionidentity-interface"></a>IEnumDefinitionIdentity インターフェイス
コレクションの列挙子として機能`IDefinitionIdentity`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```cpp  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|新しいインターフェイス ポインターを取得`IEnumDefinitionIdentity`これと同じメンバーを含むオブジェクト`IEnumDefinitionIdentity`します。|  
|`IEnumDefinitionIdentity::Next`|指定した数を取得`IDefinitionIdentity`オブジェクト、現在の位置で開始します。|  
|`IEnumDefinitionIdentity::Reset`|これの先頭に、命令ポインターを移動`IEnumDefinitionIdentity`します。|  
|`IEnumDefinitionIdentity::Skip`|指定数の要素を現在の位置からでは、転送、命令ポインターを移動します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IDefinitionIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
