---
title: ICoreClrDebugTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5a3d06f72ed7163a414ef12e9bec650d8b20783
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774288"
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget インターフェイス
参照カウントを制御し、プロセスを列挙し、リモート Macintosh Silverlight ターゲットにアタッチされたデバッガーに関連付けられているメモリを解放するメソッドを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ICoreClrDebugTarget::EnumProcesses メソッド](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|リモート コンピューターで実行されているプロセスを列挙します。|  
|[ICoreClrDebugTarget::EnumRuntimes メソッド](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|リモート コンピューター上の指定されたプロセスでは、共通言語ランタイム (Clr) を列挙します。|  
|[ICoreClrDebugTarget::FreeMemory メソッド](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|このクラスの列挙メソッドによって割り当てられたメモリを解放します。|  
  
## <a name="remarks"></a>Remarks  
 現時点では、Macintosh コンピューターをリモートで実行されている Silverlight ベースのアプリケーションのターゲットのデバッグにのみ、この機能がサポートされています。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CoreClrRemoteDebuggingInterfaces.h  
  
 **ライブラリ:** mscordbi_macx86.dll  
  
 **.NET framework のバージョン:** 3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
