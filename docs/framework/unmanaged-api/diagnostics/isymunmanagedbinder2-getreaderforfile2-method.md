---
title: ISymUnmanagedBinder2::GetReaderForFile2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db917820de92b2e347385afc5217c0ca190825cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776833"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 メソッド
メタデータ インターフェイスおよびファイル名を指定されたを返します、正しい[ISymUnmanagedReader](isymunmanagedreader-interface.md)をモジュールに関連付けられているデバッグ シンボルを読み取る。  
  
 このメソッドより広範囲の検索よりもプログラム データベース (PDB) ファイル、 [isymunmanagedbinder::getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  
 `importer`  
 [in]メタデータ インポート インターフェイスへのポインター。  
  
 `fileName`  
 [in]ファイル名へのポインター。  
  
 `searchPath`  
 [in]検索パスへのポインター。  
  
 `searchPolicy`  
 [in]値、 [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)シンボル リーダーの検索を行うときに使用されるポリシーを指定する列挙体。  
  
 `pRetVal`  
 [out]設定されているポインターに返された[ISymUnmanagedReader](isymunmanagedreader-interface.md)インターフェイス。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="remarks"></a>Remarks  
 このバージョンのメソッドは、モジュール以外の領域の PDB ファイルを検索できます。 サーチのポリシーを結合することで制御できる[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)します。 たとえば、`AllowReferencePathAccess | AllowSymbolServerAccess`実行可能ファイルの横にあると、シンボル サーバーの PDB の検索はレジストリの照会やのみが実行可能ファイルのパスを使用します。 場合、`searchPath`パラメーターが指定されて、それらのディレクトリが常に検索されます。  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedBinder2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [GetReaderForFile メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
