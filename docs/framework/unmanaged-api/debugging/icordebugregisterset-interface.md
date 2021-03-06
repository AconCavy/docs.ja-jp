---
title: ICorDebugRegisterSet インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: 940810288b72be0d4dfc5366176663c22c369ebb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712379"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet インターフェイス

現在コードを実行しているコンピューターで使用できるレジスタのセットを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetRegisters メソッド](icordebugregisterset-getregisters-method.md)|ビットマスクによって指定された、(現在コードを実行しているコンピューター上の) 各レジスタの値を取得します。|  
|[GetRegistersAvailable メソッド](icordebugregisterset-getregistersavailable-method.md)|現在使用できるレジスタを示すビットマスクを取得し `ICorDebugRegisterSet` ます。|  
|[GetThreadContext メソッド](icordebugregisterset-getthreadcontext-method.md)|現在のスレッドのコンテキストを取得します。|  
|[SetRegisters メソッド](icordebugregisterset-setregisters-method.md)|.NET Framework バージョン2.0 には実装されていません。|  
|[SetThreadContext メソッド](icordebugregisterset-setthreadcontext-method.md)|.NET Framework 2.0 には実装されていません。|  
  
## <a name="remarks"></a>注釈  

 インターフェイスでは、 `ICorDebugRegisterSet` 32 ビットレジスタのみがサポートされます。 追加のレジスタを必要とする IA-64 などのプラットフォームで [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) インターフェイスを使用します。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [ICorDebugRegisterSet2 インターフェイス](icordebugregisterset2-interface.md)
