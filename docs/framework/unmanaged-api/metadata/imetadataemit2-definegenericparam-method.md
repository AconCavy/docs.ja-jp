---
title: IMetaDataEmit2::DefineGenericParam メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: c9ff918121e7bb4ee972e674207810358b3f36f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712912"
---
# <a name="imetadataemit2definegenericparam-method"></a>IMetaDataEmit2::DefineGenericParam メソッド

ジェネリック型パラメーターの定義を作成し、そのジェネリック型パラメーターへのトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `tk`  
 から `mdTypeDef` `mdMethodDef` ジェネリックパラメーターを定義するメソッドまたはコンストラクターを表すまたはトークン。  
  
 `ulParamSeq`  
 からジェネリックパラメーターのインデックス。  
  
 `dwParamFlags`  
 からジェネリックパラメーターの型を記述する [Corgenericparamattr](corgenericparamattr-enumeration.md) 列挙体の値。  
  
 `szname`  
 からパラメーターの名前。  
  
 `reserved`  
 からこのパラメーターは、将来の拡張のために予約されています。  
  
 `rtkConstraints`  
 から型制約の0から終わる配列。 配列メンバーは `mdTypeDef` 、、 `mdTypeRef` 、またはメタデータトークンである必要があり `mdTypeSpec` ます。  
  
 `pgp`  
 入出力ジェネリックパラメーターを表すトークン。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
