---
title: ICorProfilerInfo2::GetFunctionInfo2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d6c45e44f68621708d05ca43857cf1e100113166
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771077"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 メソッド
関数の親クラス、メタデータ トークン、および型引数が存在する場合はそれぞれの `ClassID` を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `funcId`  
 [in] 親クラスおよびその他の情報を取得する関数の ID。  
  
 `frameInfo`  
 [in] スタック フレームに関する情報を指す `COR_PRF_FRAME_INFO` 値。  
  
 `pClassId`  
 [out] 関数の親クラスへのポインター。  
  
 `pModuleId`  
 [out] 関数の親クラスが定義されているモジュールへのポインター。  
  
 `pToken`  
 [out] 関数のメタデータ トークンへのポインター。  
  
 `cTypeArgs`  
 [in] `typeArgs` 配列のサイズ。  
  
 `pcTypeArgs`  
 [out] `ClassID` 値の総数へのポインター。  
  
 `typeArgs`  
 [out] `ClassID` 値の配列。各値は、関数の型引数の ID です。 このメソッドが戻るとき、使用できる `ClassID` 値の一部または全部が `typeArgs` に格納されます。  
  
## <a name="remarks"></a>Remarks  
 プロファイラー コードを呼び出すことができます[icorprofilerinfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)を取得する、[メタデータ](../../../../docs/framework/unmanaged-api/metadata/index.md)指定したモジュールのインターフェイス。 `pToken` が参照している場所に返されるメタデータ トークンを使用すると、関数のメタデータにアクセスできます。  
  
 次の表に示すように、`pClassId` パラメーターで返されるクラス ID、および `typeArgs` パラメーターで返される型引数は、`frameInfo` パラメーターで渡される値によって異なります。  
  
|パラメーター `frameInfo` の値。|結果|  
|----------------------------------------|------------|  
|`FunctionEnter2` コールバックから取得された `COR_PRF_FRAME_INFO` 値|`pClassId` によって参照される場所に返される `ClassID` と、`typeArgs` 配列で返されるすべての型引数は正確です。|  
|`FunctionEnter2` コールバック以外のソースから取得された `COR_PRF_FRAME_INFO`|正確な `ClassID` と型引数を特定できません。 つまり、`ClassID` は null の可能性があり、一部の型引数は <xref:System.Object> として戻る可能性があります。|  
|0|正確な `ClassID` と型引数を特定できません。 つまり、`ClassID` は null の可能性があり、一部の型引数は <xref:System.Object> として戻る可能性があります。|  
  
 `GetFunctionInfo2` から制御が戻ったら、`typeArgs` バッファーのサイズが十分で、すべての `ClassID` 値を格納できたかどうかを確認する必要があります。 これを行うには、`pcTypeArgs` が指している値を `cTypeArgs` パラメーターの値と比較します。 `pcTypeArgs` の指す値が、`ClassID` 値のサイズで除算された `cTypeArgs` の値より大きい場合は、`pcTypeArgs` バッファーの割り当てを増やし、`cTypeArgs` を新しい大きいサイズに更新して、`GetFunctionInfo2` を再度呼び出します。  
  
 別の方法として、最初に `GetFunctionInfo2` を長さゼロの `pcTypeArgs` バッファーで呼び出して、適切なバッファーのサイズを取得します。 その後、バッファーのサイズを `pcTypeArgs` に返された値 (`ClassID` 値のサイズで除算された値) に設定し、`GetFunctionInfo2` を再度呼び出します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
