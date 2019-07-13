---
title: ICorDebugStackWalk::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82f6c96e64b1197b5762c0ad7dbed5458b5d71a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760896"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next メソッド
移動、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)次のフレームにオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|次のフレームに、ランタイムが正常にアンワインドされました (「解説」を参照してください)。|  
|E_FAIL|`ICorDebugStackWalk`オブジェクトを移すことができません。|  
|CORDBG_S_AT_END_OF_STACK|このアンワインドの結果として、スタックの末尾に達しました。|  
|CORDBG_E_PAST_END_OF_STACK|フレーム ポインターがスタックの末尾に達してそのため、追加のフレームにはアクセスできません。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 `Next`メソッドの進歩、`ICorDebugStackWalk`呼び出し元のフレームにオブジェクトの場合にのみ、ランタイムは、現在のフレームをアンワインドできます。 それ以外の場合、オブジェクトは、ランタイムは、アンワインド可能な次のフレームを進めます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugStackWalk インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
