---
title: ICorDebugObjectValue::GetFieldValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fc65f5b55082970a0cd59a6850aaaa6779d0821
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766410"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue メソッド
このオブジェクトの値の指定したクラスの指定したフィールドの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pClass`  
 [in]フィールドの値を取得する対象のクラスを表す"ICorDebugClass"オブジェクトへのポインター。  
  
 `fieldDef`  
 [in]`mdFieldDef`フィールドを記述するメタデータを参照するトークン。  
  
 `ppValue`  
 [out]指定したフィールドの値を表す"ICorDebugValue"オブジェクトへのポインター。  
  
## <a name="remarks"></a>Remarks  
 指定された、クラス、`pClass`パラメーターに、オブジェクトの値のクラスの階層にする必要があり、フィールドはそのクラスのフィールドである必要があります。  
  
 `GetFieldValue`汎用オブジェクトおよびジェネリック クラスのメソッドは成功します。 たとえば場合、MyDictionary\<V > ディクショナリから継承\<文字列、V >、オブジェクトの値の種類 MyDictionary\<int32 > を渡して、`ICorDebugClass`ディクショナリのオブジェクト\<K, V > はディクショナリのフィールドを正常に取得\<string, int32 > です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
