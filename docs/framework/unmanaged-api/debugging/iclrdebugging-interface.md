---
title: ICLRDebugging インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 6eea7f6c222b8e30376ec72ee0c193a68c23f0d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723559"
---
# <a name="iclrdebugging-interface"></a>ICLRDebugging インターフェイス

デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[OpenVirtualProcess メソッド](iclrdebugging-openvirtualprocess-method.md)|プロセスに読み込まれた共通言語ランタイム (CLR) モジュールに対応する "のプロセス" インターフェイスを取得します。|  
|[CanUnloadNow メソッド](iclrdebugging-canunloadnow-method.md)|[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)インターフェイスによって提供されたライブラリがまだ使用中であるか、またはアンロードできるかどうかを判断します。|  
  
## <a name="remarks"></a>注釈  

 インターフェイスのインスタンスを取得する `ICLRDebugging` には、 [clrcreateinstance](../hosting/clrcreateinstance-function.md) 関数を使用します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
