---
title: ICorProfilerCallback4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 942ee8234b79c6579acc009960f4571801fc3185
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730293"
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4 インターフェイス

プロファイラーに情報を伝達するために共通言語ランタイム (CLR) が使用するコールバックメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReJITParameters メソッド](icorprofilercallback4-getrejitparameters-method.md)|再コンパイルされた新しいメソッド本体の代替コード生成フラグをコードプロファイラーで設定できるようにします。|  
|[MovedReferences2 メソッド](icorprofilercallback4-movedreferences2-method.md)|圧縮ガベージコレクションの結果として、ヒープ内のオブジェクトの新しいレイアウトを報告します。|  
|[ReJITCompilationFinished メソッド](icorprofilercallback4-rejitcompilationfinished-method.md)|Just-in-time (JIT) コンパイラが関数の再コンパイルを完了したことをプロファイラーに通知します。|  
|[ReJITCompilationStarted メソッド](icorprofilercallback4-rejitcompilationstarted-method.md)|Just-in-time (JIT) コンパイラが関数の再コンパイルを開始したことをプロファイラーに通知します。|  
|[ReJITError メソッド](icorprofilercallback4-rejiterror-method.md)|Recompile 要求の処理中に発生したエラーを報告します。|  
|[SurvivingReferences2 メソッド](icorprofilercallback4-survivingreferences2-method.md)|非圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトのレイアウトを報告します。|  
  
## <a name="remarks"></a>解説  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback2 インターフェイス](icorprofilercallback2-interface.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
