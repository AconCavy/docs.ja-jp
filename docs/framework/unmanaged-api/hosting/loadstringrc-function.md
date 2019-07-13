---
title: LoadStringRC 関数
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9047bf973224cdbc1f67463ef70f15f81089f827
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768456"
---
# <a name="loadstringrc-function"></a>LoadStringRC 関数
現在のスレッドの既定のカルチャを使用して、HRESULT 値をエラー メッセージに変換します。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `iResourceID`  
 [in]HRESULT。  
  
 `szBuffer`  
 [out]正常完了時にエラー メッセージを格納するバッファー。  
  
 `iMax`  
 [in]エラー メッセージのバッファーのサイズ。  
  
 `bQuiet`  
 [in]無視されます。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値だけでなく、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`szBuffer` null または`iMax`はゼロ (0)。|  
  
## <a name="remarks"></a>Remarks  
 メソッドが正常に完了しない場合`szBuffer`空の文字列が含まれています。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll と Mscorwks.dll します。 Mscorwks.dll の代わりに MSCorEE.dll を使用して、正しいバージョンの .NET Framework を対象にすることを確認します。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [LoadStringRCEx 関数](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
