---
title: ISymUnmanagedWriter::DefineDocument メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
ms.openlocfilehash: 6413935df86b85a959fa4f354c6233d18baf99d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727576"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a>ISymUnmanagedWriter::DefineDocument メソッド

ソース ドキュメントを定義します。 Guid は、既知の言語、ベンダー、およびドキュメントの種類に対して提供されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  

 `url`  
 から `WCHAR` ドキュメントを識別する URL (uniform resource locator) を定義するへのポインター。  
  
 `language`  
 からドキュメントの言語を定義する GUID へのポインター。  
  
 `languageVendor`  
 からドキュメント言語のベンダの id を定義する GUID へのポインター。  
  
 `documentType`  
 からドキュメントの種類を定義する GUID へのポインター。  
  
 `pRetVal`  
 入出力返された [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) インターフェイスへのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)
