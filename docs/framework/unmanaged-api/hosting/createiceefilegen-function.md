---
title: CreateICeeFileGen 関数
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96968de84182b74f7baa89d5dfc12a4797ade595
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779231"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen 関数
作成、 [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)オブジェクト。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ceeFileGen`  
 [out]新しいアドレスへのポインター`ICeeFileGen`オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、標準の COM エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 `ICeeFileGen`オブジェクトが共通言語ランタイム (CLR) のポータブル実行可能 (PE) ファイルを作成するために使用します。  
  
 呼び出す、 [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)を破棄する関数、`ICeeFileGen`オブジェクトの終了時にします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** ICeeFileGen.h  
  
 **ライブラリ:** MSCorPE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
