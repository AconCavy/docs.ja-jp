---
title: ICorDebugILFrame4::GetLocalVariableEx メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: c9dfbdc141c19cb9bee87a34d838c5e7c6b366df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724963"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx メソッド

[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 この中間言語 (IL) スタック フレーム内の指定されたローカル変数の値を取得して、オプションでプロファイラー ReJIT インストルメンテーションに追加された変数にアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `flags`  
 からプロファイラー ReJIT インストルメンテーションに追加された変数がフレームに含まれるかどうかを指定する [Ilcodekind](ilcodekind-enumeration.md) 列挙体のメンバー。  
  
 `dwIndex`  
 [in] IL スタック フレーム内のローカル変数のインデックス。  
  
 `ppValue`  
 入出力取得された値を表す "ICorDebugValue" オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 このメソッドは、オプションでプロファイラー ReJIT インストルメンテーションに追加された変数にアクセスする点を除いて、 [Getlocalvariable](icordebugilframe-getlocalvariable-method.md) メソッドに似ています。 値を指定してこのメソッドを呼び出す `flags` `ILCODE_ORIGINAL_IL` ことは、 [getlocalvariable](icordebugilframe-getlocalvariable-method.md)を呼び出すことと同じです。メソッドが追加のローカル変数でインストルメント化されている場合、これらの変数にはアクセスできません。 `ILCODE_REJIT_IL` は、デバッガーがプロファイラー ReJIT インストルメンテーションに追加されたローカル変数にアクセスできるようにします。 IL がインストルメントされていない場合、メソッドは `E_INVALIDARG` を返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugILFrame4 インターフェイス](icordebugilframe4-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [ReJIT: How-To ガイド](/archive/blogs/davbr/rejit-a-how-to-guide)
