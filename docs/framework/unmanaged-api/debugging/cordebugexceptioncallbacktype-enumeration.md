---
title: CorDebugExceptionCallbackType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
ms.openlocfilehash: cddcf66939a2ae7ab9e7f63a6fd61b72c56f6c7a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712730"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a>CorDebugExceptionCallbackType 列挙型

[ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)イベントから作成されたコールバックの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|例外がスローされました。|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|例外 windup プロセスによってユーザーコードが入力されました。|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|例外 windup プロセスにより、 `catch` ユーザーコードにブロックが見つかりました。|  
|`DEBUG_EXCEPTION_UNHANDLED`|例外は処理されませんでした。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
