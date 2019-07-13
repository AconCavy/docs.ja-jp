---
title: ImportFileEx メソッド
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fcf714cb0c1c1dd59ae2ec56279870c0bb3e1c4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741727"
---
# <a name="importfileex-method"></a>ImportFileEx メソッド
インポートには、アセンブリまたはバインドされていないモジュールが示されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `pszFilename`  
 インポート元のファイルの完全修飾名。  
  
 `pszTargetName`  
 ターゲット ファイルの名前を省略可能です。  
  
 `fSmartImport`  
 TRUE の場合は、ImportTypes が使用されますが、それ以外の場合にインポートし、手動で実行する必要があります。  
  
 `dwOpenFlags`  
 渡すフラグ[OpenScope メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)します。  
  
 `pImportToken`  
 インポートされるファイルの ID を受け取ります。  
  
 `ppAssemblyScope`  
 アセンブリ インポート スコープを受け取る[IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイス。 ファイルはアセンブリでない場合、NULL に設定されます。  
  
 `pdwCountOfScopes`  
 インポートされたファイルやスコープの数を受け取ります。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は、S_OK を返します。  
  
## <a name="requirements"></a>必要条件  
 Alink.h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink2 インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
