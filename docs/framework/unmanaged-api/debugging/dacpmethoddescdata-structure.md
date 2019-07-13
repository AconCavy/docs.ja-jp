---
title: DacpMethodDescData 構造体
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 97079b824dbd0e056374af4173e49304babd6c32
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739134"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData 構造体

トランスポートのバッファー、メソッドのランタイム情報を定義します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a>メンバー

| メンバー                       | 説明                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | ランタイムがメソッドの特定のインスタンスを作成して使用可能なネイティブ コードを持つかどうかを示します。 |
| `bIsDynamic`                 | メソッドが、簡易コード生成を動的に生成されるかどうかを示します。           |
| `wSlotNumber`                | メソッドの表に、メソッドのスロット番号。                                                   |
| `NativeCodeAddr`             | メソッドの最初のネイティブ アドレス。                                                            |
| `data`                       | ランタイムによって内部的に使用するバッファーへのポインター。                                             |
| `MethodDescPtr`              | ポインター、`MethodDesc`ランタイム。                                                     |
| `nativeCodeInfo`             | メソッドを追跡するために、ランタイムによって内部的に使用するバッファーへのポインター。                            |
| `moduleInfo`                 | モジュールは、ランタイムによって内部的に使用するバッファーへのポインター。                      |
| `MDToken`                    | 指定されたメソッドに関連付けられているトークンです。                                                         |
| `payloadGC`                  | ランタイムによって内部的に使用するガベージ コレクション バッファーへのポインター。                          |
| `payloadGC2`                 | ランタイムによって内部的に使用するガベージ コレクション バッファーへのポインター。                          |
| `managedDynamicMethodObject` | 動的メソッドの場合、ランタイムはこのバッファー内部的に追跡情報をします。     |
| `requestedIP`                | ネイティブ コードのアドレスが指定されているとき、要求につき構造体を設定するために使用します。                    |
| `rejitDataCurrent`           | インストルメント化された最新バージョンのメソッドについて説明します。                                   |
| `rejitDataRequested`         | 要求されたネイティブのアドレスの Rejit 情報。                                             |
| `cJittedRejitVersions`       | メソッドは実装を通じて rejitted された回数。                           |

## <a name="remarks"></a>Remarks

この構造は、ランタイム内に収めるし、任意のヘッダーまたはライブラリ ファイルでは公開されません。 これを使用するには、上で指定した構造を定義します。

## <a name="requirements"></a>必要条件
**プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
**ヘッダー:** なし  
**ライブラリ:** なし  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [共有のデータ型](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
