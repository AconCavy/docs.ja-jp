---
title: ICorDebugThread4::HadUnhandledException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
ms.openlocfilehash: d9f0eff35dbe0058398d2d1c851ef85effa9cd28
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122419"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException メソッド
スレッドで未処理の例外が発生したかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppBlockingObjectEnum`  
 入出力[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体の順序付けられた列挙体のアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|スレッドの作成以降、ハンドルされない例外が発生しました。|  
|S_FALSE|スレッドでハンドルされない例外が発生していません。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、スレッドにハンドルされない例外が発生したかどうかを示します。 未処理の例外のコールバックがトリガーされるか、ネイティブの JIT アタッチが開始されるまで、このメソッドは S_OK を返すことが保証されます。 処理不能な例外が返されるという保証はありませ[ん。](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)ただし、ハンドルされない例外コールバックを取得した後、またはネイティブ JIT アタッチによってプロセスがまだ続行されていない場合に発生します。 また、ネイティブ JIT アタッチがトリガーされたときに、ハンドルされない例外を持つ複数のスレッドを使用することもできます。 このような場合は、どの例外が JIT アタッチをトリガーしたかを判断する方法はありません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugThread4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)