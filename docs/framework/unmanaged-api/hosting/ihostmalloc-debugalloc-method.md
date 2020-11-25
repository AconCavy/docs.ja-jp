---
title: IHostMAlloc::DebugAlloc メソッド
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 49de0398dd32970bd8ceb0fd24178e75df5d14b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713495"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc メソッド

ホストがヒープから指定された量のメモリを割り当て、さらにメモリが割り当てられた場所を追跡するように要求します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cbSize`  
 から現在のメモリ割り当て要求のサイズ (バイト単位)。  
  
 `dwCriticalLevel`  
 から割り当てエラーの影響を示す [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) 値の1つ。  
  
 `pszFileName`  
 からデバッグ中の実行可能ファイルのコードファイル。  
  
 `iLineNo`  
 から割り当てが要求されたの行番号 `pszFileName` 。  
  
 `ppMem`  
 入出力割り当てられたメモリへのポインター。要求を完了できなかった場合は null。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`DebugAlloc` 正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。 後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_OUTOFMEMORY|割り当て要求を完了するのに十分なメモリがありませんでした。|  
  
## <a name="remarks"></a>注釈  

 CLR は、 [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md)メソッドを呼び出すことによって、 [IHostMalloc](ihostmalloc-interface.md)インスタンスへのインターフェイスポインターを取得します。 `DebugAlloc` ランタイムがデバッグ中に使用するコードファイルの情報を取得できるようにします。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostMemoryManager インターフェイス](ihostmemorymanager-interface.md)
- [IHostMalloc インターフェイス](ihostmalloc-interface.md)
