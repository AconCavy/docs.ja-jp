---
title: ICorDebugMutableDataTarget::SetThreadContext メソッド
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6629af393eeadb68292f8f2360ecb60c09a0cd03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764616"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget::SetThreadContext メソッド
スレッドのコンテキスト (レジスタの値) を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwThreadID`  
 [in] オペレーティング システム定義のスレッド識別子。  
  
 `contextSize`  
 [in]書き込まれる `pContext` バッファーのサイズ。  
  
 `pContext`  
 [in]書き込まれるバイト数へのポインター。  
  
## <a name="remarks"></a>Remarks  
 `SetThreadContext` メソッドは、オペレーティング システム定義の `dwThreadID` 引数で指定されるスレッドの現在のコンテキストを更新します。 コンテキスト レコードの形式はにより示されるプラットフォームによって決まります、 [icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)メソッド。 これは、Windows、[コンテキスト](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context)構造体。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugMutableDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
