---
title: ISymUnmanagedBinder3::GetReaderFromCallback メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ed0097e072b34dd43876ddf23abbc1f513670ff
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776822"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a>ISymUnmanagedBinder3::GetReaderFromCallback メソッド
実装またはコールバックを使用していずれかを指定できます、`IID_IDiaReadExeAtRVACallback`または`IID_IDiaReadExeAtOffsetCallback`をメモリからデバッグ ディレクトリ情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
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
  
 `callback`  
 [in]コールバック関数へのポインター。  
  
 `pRetVal`  
 [out]設定されているポインターに返された[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)インターフェイス。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedBinder3 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
