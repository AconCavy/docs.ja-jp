---
title: ICorProfilerInfo::SetILFunctionBody メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abe0a0fc177c9ec89f4621e7defb5330c911034b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778609"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a>ICorProfilerInfo::SetILFunctionBody メソッド
指定したモジュール内の指定した関数の本体を置き換えます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleId`  
 [in]関数が存在するモジュールの ID。  
  
 `methodid`  
 [in]本文を置換する関数のトークンです。  
  
 `pbNewILMethodHeader`  
 [in]関数の新しいヘッダー。  
  
## <a name="remarks"></a>Remarks  
 `SetILFunctionBody`メソッドは、関数の新しい本文をポイントし、必要に応じて内部データ構造を調整できるように、メタデータ内の関数の相対仮想アドレスを置き換えます。  
  
 `SetILFunctionBody`ことはありません - イン タイム (JIT) コンパイラによってコンパイルされた関数のみでメソッドを呼び出すことができます。  
  
 使用して、 [icorprofilerinfo::getilfunctionbodyallocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)バッファーとの互換性があることを確認する新しいメソッドの領域を割り当てるためのメソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
