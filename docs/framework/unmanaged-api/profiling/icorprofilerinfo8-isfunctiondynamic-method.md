---
title: 'ICorProfilerInfo8:: IsFunctionDynamic'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 01aa1df27dccf41060083333588e04bc5ea88520
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855934"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>ICorProfilerInfo8:: IsFunctionDynamic メソッド

関数にメタデータが関連付けられていないかどうかを判断します。

## <a name="syntax"></a>構文

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

#### <a name="parameters"></a>パラメーター

`functionId` \
から 対象の関数を識別する。`FunctionID`

`isDynamic` \
入出力関数にメタデータ`BOOL`がないかどうかを示す値を格納するへのポインター。

## <a name="remarks"></a>Remarks

関数は、メタデータがない場合は動的と見なされます。 IL スタブや LCG メソッドなどの特定のメソッドには、IMetaDataImport Api を使用して取得できるメタデータが関連付けられていません。 これらのメソッドは、命令ポインターを通じて、または[ICorProfilerCallback::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)をリッスンすることによって、プロファイラーによって検出されます。

## <a name="requirements"></a>必要条件

**・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** Corprof.idl、Corprof.idl

**ライブラリ**CorGuids .lib

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo8 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
