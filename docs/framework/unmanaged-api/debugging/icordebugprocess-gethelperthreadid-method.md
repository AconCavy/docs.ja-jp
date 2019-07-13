---
title: ICorDebugProcess::GetHelperThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad62b267eb0c49ff8fbefeb45b523c21edc705fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766048"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID メソッド
デバッガーの内部ヘルパーのスレッドのオペレーティング システム (OS) のスレッド ID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pThreadID`  
 [out]OS へのポインターはスレッド、デバッガーの内部ヘルパーのスレッドの ID です。  
  
## <a name="remarks"></a>Remarks  
 マネージ コードとアンマネージ デバッグ中は、デバッガーでブレークポイントにヒットした場合、指定した ID を持つスレッド引き続き実行されているようにする、デバッガーの責任です。 デバッガーは、ユーザーからは、このスレッドを非表示にする可能性がありますも。 ヘルパーのスレッドが存在しない場合、プロセスで、まだ、`GetHelperThreadID`にゼロが返される *`pThreadID`します。  
  
 時間の経過と共に変更可能性がありますので、ヘルパーのスレッドのスレッド ID をキャッシュすることはできません。 停止イベントごとにスレッド ID を再クエリする必要があります。  
  
 なければ、デバッガーのヘルパーのスレッドのスレッド ID すべてアンマネージ[icordebugmanagedcallback::createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)イベント、ため、デバッガー ヘルパー スレッドのスレッド ID を特定し、ユーザーから非表示にすることができます。 アンマネージの中にヘルパー スレッドとして識別されるスレッド`ICorDebugManagedCallback::CreateThread`イベントではマネージ ユーザー コードは実行されません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl します。 CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
