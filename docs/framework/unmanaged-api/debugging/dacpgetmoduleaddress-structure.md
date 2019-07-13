---
title: DacpGetModuleAddress 構造体
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 145b06f89b45b165b9d6329a4c16ac5739406113
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739183"
---
# <a name="dacpgetmoduleaddress-structure"></a>DacpGetModuleAddress 構造体

モジュールのアドレスの要求のコンテナーを定義します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a>メンバー

| メンバー      | 説明                |
| ----------- | -------------------------- |
| `ModulePtr` | モジュールへのポインター。 |

## <a name="methods"></a>メソッド

| メソッド                                                                                               | 説明                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [要求](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | 指定したランタイムの構造体から構造の作成要求を実行します。 |

## <a name="remarks"></a>Remarks

この構造は、ランタイム内に収めるし、任意のヘッダーまたはライブラリ ファイルでは公開されません。 これを使用する構造を定義、上で指定した場所`CLRDATA_ADDRESS`は 64 ビット符号なし整数。

## <a name="requirements"></a>必要条件
**プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
**ヘッダー:** なし  
**ライブラリ:** なし  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
