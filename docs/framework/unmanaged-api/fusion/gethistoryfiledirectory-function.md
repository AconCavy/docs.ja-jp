---
title: GetHistoryFileDirectory 関数
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10eead2772a2bbd8abaf7b9c090a091687725972
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778656"
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory 関数
アプリケーション履歴ディレクトリのパスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wzDir`  
 [out]アプリケーション履歴ディレクトリへのパスを保持するバッファー。  
  
 `pdwSize`  
 [入力、出力]バッファーの長さ。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値だけでなく、WinError.h ファイルで定義されている標準の COM エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`wzDir` または`pdwSize`が null の場合、または、バージョン文字列が正しくありません。|  
  
## <a name="remarks"></a>Remarks  
 正常に完了、`pdwSize`引数パス文字列の長さを設定します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** Fusion.dll と Mscorwks.dll します。 Mscorwks.dll のではなく Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にすることを確認します。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CreateHistoryReader 関数](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [NukeDownloadedCache 関数](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
