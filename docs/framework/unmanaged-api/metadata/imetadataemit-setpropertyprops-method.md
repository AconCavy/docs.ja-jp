---
title: IMetaDataEmit::SetPropertyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e78c4d7319a931ca7090d6f99651bc9660e4af8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782050"
---
# <a name="imetadataemitsetpropertyprops-method"></a>IMetaDataEmit::SetPropertyProps メソッド
前回の呼び出しによって定義されるプロパティのメタデータに格納されている機能の設定[DefineProperty メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetPropertyProps (   
    [in]  mdProperty      pr,   
    [in]  DWORD           dwPropFlags,   
    [in]  DWORD           dwCPlusTypeFlag,   
    [in]  void const      *pValue,   
    [in]  ULONG           cchValue,   
    [in]  mdMethodDef     mdSetter,   
    [in]  mdMethodDef     mdGetter,   
    [in]  mdMethodDef     rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pr`  
 [in]変更するプロパティのトークン  
  
 `dwPropFlags`  
 [in]プロパティのフラグ。  
  
 `dwCPlusTypeFlag`  
 [in]プロパティの既定値の型。  
  
 `pValue`  
 [in]プロパティの既定値。  
  
 `cchValue`  
 [in] \(Unicode) の数の文字について`pValue`です。  
  
 `mdSetter`  
 [in]このメソッドは、プロパティ値を設定します。  
  
 `mdGetter`  
 [in]このメソッドは、プロパティ値を取得します。  
  
 `rmdOtherMethods[]`  
 [in]プロパティに関連付けられているその他のメソッドの配列。 この配列を`mdTokenNil`トークンです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
