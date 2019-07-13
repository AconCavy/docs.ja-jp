---
title: ICorDebugAssembly3::GetContainerAssembly メソッド
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbe28c01891464ff45dfec97b1d8b4685ba8a51a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744375"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly メソッド
この `ICorDebugAssembly3` オブジェクトのコンテナー アセンブリを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppAssembly`  
 コンテナー アセンブリを表す ICorDebugAssembly オブジェクトのアドレスへのポインターまたは**null**メソッドの呼び出しが失敗した場合。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` メソッドの呼び出しが成功した場合それ以外の場合、 `S_FALSE`、および`ppAssembly`は**null**します。  
  
## <a name="remarks"></a>Remarks  
 このアセンブリが 1 つのコンテナー アセンブリ内の他のアセンブリとマージされている場合、このメソッドはコンテナー アセンブリを返します。 詳細な情報と用語については、次を参照してください。、 [icordebugprocess 6::enablevirtualmodulesplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)トピック。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugAssembly3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
