---
title: ICorDebugFunction2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: 55f219b5b834f365b87440e69bfa7d2c4e519235
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696094"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus メソッド

この ICorDebugFunction2 によって表される関数をステップ実行マイコードのみにマークします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `bIsJustMyCode`  
 から関数を `true` ユーザーコードとしてマークする場合はに設定します。それ以外の場合はに設定 `false` します。  
  
## <a name="return-values"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|関数は正常にマークされました。|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|デバッグできないため、関数をユーザーコードとしてマークできませんでした。|  
  
## <a name="remarks"></a>注釈  

 マイコードのみステッパは、非ユーザーコードをスキップします。 ユーザーコードは、デバッグ可能なコードのサブセットである必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
