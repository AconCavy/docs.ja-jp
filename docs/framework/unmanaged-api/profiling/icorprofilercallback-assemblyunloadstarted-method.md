---
title: ICorProfilerCallback::AssemblyUnloadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfcf2c74a2a44bd0539bf78e237e42553696b16c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762993"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a>ICorProfilerCallback::AssemblyUnloadStarted メソッド
アセンブリがアンロードされることをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a>パラメーター  
 `assemblyId`  
 [in]アンロードされているアセンブリを識別します。  
  
## <a name="remarks"></a>Remarks  
 値`assemblyId`は後の情報の要求は無効です、`AssemblyUnloadStarted`メソッドを返します。-これはこのアセンブリに関する情報を取得、プロファイラーの最後のチャンスです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [AssemblyUnloadFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
