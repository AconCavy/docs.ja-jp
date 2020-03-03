---
title: ICorDebugProcess4::ProcessStateChanged メソッド
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: adfd563e19389642ac0ed0a3cef4aae8a32fa466
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767190"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::ProcessStateChanged メソッド

デバッガーをプロセスの出力がデバッグ対象の実行を続行は ICorDebug パイプラインに通知します。

## <a name="syntax"></a>構文

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>パラメーター

 `eChange`\
[in]メンバー、 [CorDebugStateChange 列挙体](cordebugstatechange-enumeration.md)プロセスの実行状態の変更を記述します。

## <a name="remarks"></a>Remarks

指定されたメソッドは、`ICorDebugProcess4`インターフェイスし、仮想メソッド テーブルの 4 番目のスロットに対応しています。

## <a name="requirements"></a>必要条件

 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

 **ヘッダー:** なし

 **ライブラリ:** なし
 
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [ICorDebugProcess4 インターフェイス](icordebugprocess4-interface.md)
- [デバッグ インターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
