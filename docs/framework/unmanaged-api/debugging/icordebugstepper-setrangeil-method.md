---
title: ICorDebugStepper::SetRangeIL メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: 5a27f155021661022b27022bbb252e00dfa67255
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698781"
---
# <a name="icordebugsteppersetrangeil-method"></a>ICorDebugStepper::SetRangeIL メソッド

[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md)の呼び出しで、ネイティブコードに対して相対的な引数値を渡すか、またはステップスルー中のメソッドの MSIL (Microsoft 中間言語) コードに対する相対パスを指定するかを指定する値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `bIL`  
 から `true` 範囲が MSIL コードに対して相対的であることを指定するには、をに設定します。 `false`範囲がネイティブコードに対して相対的であることを指定するには、をに設定します。 既定値は `true` です。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
