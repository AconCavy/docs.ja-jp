---
title: ICorDebugAppDomain2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
ms.openlocfilehash: f20ae6977504f958b7bfa8e2f073b7db6e8b822b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731476"
---
# <a name="icordebugappdomain2-interface"></a>ICorDebugAppDomain2 インターフェイス

配列、ポインター、関数ポインター、および参照型を操作するメソッドを提供します。 このインターフェイスは、の機能を持つ Appdomain インターフェイスの拡張です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetArrayOrPointerType メソッド](icordebugappdomain2-getarrayorpointertype-method.md)|指定した型、または指定した型へのポインターまたは参照の配列を取得します。|  
|[GetFunctionPointerType](icordebugappdomain2-getfunctionpointertype-method.md)|指定されたシグネチャを持つ関数へのポインターを取得します。|  
  
## <a name="remarks"></a>注釈  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
