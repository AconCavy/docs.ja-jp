---
title: ImportTypes メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 762f78900add70238971978ceecda089d0c725ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705112"
---
# <a name="importtypes-method"></a>ImportTypes メソッド

[Importfile メソッド](importfile-method.md)を使用してインポートされた各スコープからの型のインポートを開始します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 インポート先のアセンブリの ID。  
  
 `FileToken`  
 インポート元のファイルの ID。  
  
 `dwScope`  
 インポートする0から始まるスコープ。  
  
 `phEnum`  
 このスコープ内の型の列挙子ハンドルを受け取ります。  
  
 `ppImportScope`  
 必要に応じて、 [IMetaDataImport インターフェイス](../metadata/imetadataimport-interface.md) インターフェイスを受け取ります。  
  
 `pdwCountOfTypes`  
 必要に応じて、指定されたスコープ内の型の数を受け取ります。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
