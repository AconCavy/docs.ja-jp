---
title: CorDebugIntercept 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: 3d3d4af8e9ee073c0aefec418a3b53c4589adf0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729110"
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept 列挙型

インターセプト (ステップ イン) できるコードの型を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`INTERCEPT_NONE`|インターセプトできるコードはありません。|  
|`INTERCEPT_CLASS_INIT`|コンストラクターをインターセプトできます。|  
|`INTERCEPT_EXCEPTION_FILTER`|例外フィルターをインターセプトできます。|  
|`INTERCEPT_SECURITY`|セキュリティを適用するコードをインターセプトできます。|  
|`INTERCEPT_CONTEXT_POLICY`|コンテキスト ポリシーをインターセプトできます。|  
|`INTERCEPT_INTERCEPTION`|使用されていません。|  
|`INTERCEPT_ALL`|すべてのコードをインターセプトできます。|  
  
## <a name="remarks"></a>注釈  

 インターセプトできるコードの型を確立するには、 [ICorDebugStepper:: SetInterceptMask](icordebugstepper-setinterceptmask-method.md) メソッドを使用します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
