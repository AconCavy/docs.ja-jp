---
title: CorDebugDecodeEventFlagsWindows 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec23e0f272852088987fcc74767d3645778eab45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955681"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a>CorDebugDecodeEventFlagsWindows 列挙体
Windows プラットフォームのデバッグ イベントに関する追加情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|デバッグ イベントが初回例外であることを示します。|  
  
## <a name="remarks"></a>Remarks  
 [ICorDebugProcess6::D ecodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)メソッドには、 `dwFlags`デバッグイベントに関する追加情報を提供し、ターゲットアーキテクチャに依存する値を持つパラメーターが含まれています。 `CorDebugDecodeEventFlagsWindows` 列挙体は、Windows プラットフォームでデバッグ イベントと共に使用できます。  
  
> [!NOTE]
> この列挙型は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
