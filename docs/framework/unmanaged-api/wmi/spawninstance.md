---
title: SpawnInstance 関数 (アンマネージ API リファレンス)
description: SpawnInstance 関数は、クラスの新しいインスタンスを作成します。
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 176bc83dd02381af8c2bc3995a37e7fee7c1bebf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732230"
---
# <a name="spawninstance-function"></a>SpawnInstance 関数

クラスの新しいインスタンスが作成されます。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
からこのパラメーターは使用されていません。

`ptr`  
から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`lFlags`  
[in] 予約されています。 このパラメーターには0を指定する必要があります。

`ppNewInstance`  
入出力クラスの新しいインスタンスへのポインターを受け取ります。 エラーが発生した場合、新しいオブジェクトは返されず、 `ppNewInstance` 未変更のままになります。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80040 | `ptr` は有効なクラス定義ではなく、新しいインスタンスを生成できません。 このファイルが不完全であるか、 [Putclasswmi](putclasswmi.md)を呼び出して Windows Management に登録されていません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | メモリ不足のため、操作を完了できません。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` が `null`です。 |
| `WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
  
## <a name="remarks"></a>注釈

この関数は、 [IWbemClassObject:: SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) メソッドの呼び出しをラップします。

`ptr` は、Windows 管理から取得したクラス定義である必要があります。 (インスタンスからインスタンスを生成することはサポートされていますが、返されたインスタンスが空であることに注意してください)。次に、このクラス定義を使用して、新しいインスタンスを作成します。 Windows Management にインスタンスを書き込む場合は、 [Putinstancewmi](putinstancewmi.md) 関数を呼び出す必要があります。

で返された新しいオブジェクトは、 `ppNewClass` 自動的に現在のオブジェクトのサブクラスになります。 この動作をオーバーライドすることはできません。 サブクラス (派生クラス) を作成する方法は他にもありません。

## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils .idl  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
