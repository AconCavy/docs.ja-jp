---
title: IMetaDataImport::GetNameFromToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 867fb0ee4bc1a093eb7fd46e25497d585c4d9b6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727498"
---
# <a name="imetadataimportgetnamefromtoken-method"></a>IMetaDataImport::GetNameFromToken メソッド

指定したメタデータ トークンによって参照されるオブジェクトの UTF-8 名を取得します。 このメソッドは、互換性のために残されています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `tk`  
 から名前を返すオブジェクトを表すトークン。  
  
 `pszUtf8NamePtr`  
 入出力ヒープ内の UTF-8 オブジェクト名へのポインター。  
  
## <a name="remarks"></a>注釈  

 `GetNameFromToken` は互換性のために残されています。 別の方法として、フィールドやメソッドなど、必要な特定の種類のトークンのプロパティを取得するには、メソッドを呼び出し `GetFieldProps` `GetMethodProps` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** 1.0  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
