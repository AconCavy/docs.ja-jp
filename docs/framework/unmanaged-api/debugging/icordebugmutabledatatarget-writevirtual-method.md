---
title: 'ICorDebugMutableDataTarget:: WriteVirtual メソッド'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 5947caa8dfb97574bb4b3c5634d962df153211c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132680"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget:: WriteVirtual メソッド
ターゲット プロセスのアドレス空間にメモリを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 [in] `pBuffer` の内容の書き込み先のアドレスです。  
  
 `pBuffer`  
 [in] 書き込むバイト数が格納されているバイト配列へのポインター。  
  
 `address`  
 [in] `pBuffer` のバイト数。  
  
## <a name="return-value"></a>戻り値  
 正常に完了した場合は `S_OK`、失敗した場合はその他の `HRESULT`。  
  
## <a name="remarks"></a>Remarks  
 バイトを書き込むことができない場合、メソッド呼び出しは失敗し、ターゲット アドレス空間のバイトは変更されません。 (それ以外の場合、ターゲットは不整合な状態になり、デバッグの信頼性がさらに低下します。)  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMutableDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
