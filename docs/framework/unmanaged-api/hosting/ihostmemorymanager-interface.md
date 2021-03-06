---
title: IHostMemoryManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: 0f71e4c45e43c2027b12998532f2b04401a51951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731333"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager インターフェイス

標準の Win32 仮想メモリ関数を使用する代わりに、共通言語ランタイム (CLR) がホストを介して仮想メモリ要求を行うことができるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace メソッド](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|共通言語ランタイム (CLR) が、指定されたメモリをオペレーティングシステムから取得したことをホストに通知します。|  
|[CreateMAlloc メソッド](ihostmemorymanager-createmalloc-method.md)|ホストによって作成されたヒープからメモリ割り当てを要求するために使用される [IHostMAlloc](ihostmalloc-interface.md) インスタンスへのインターフェイスポインターを取得します。|  
|[GetMemoryLoad メソッド](ihostmemorymanager-getmemoryload-method.md)|ホストによって報告された、現在使用されている物理メモリの量を取得します。|  
|[NeedsVirtualAddressSpace メソッド](ihostmemorymanager-needsvirtualaddressspace-method.md)|CLR が指定されたメモリを使用しようとしていることをホストに通知します。|  
|[RegisterMemoryNotificationCallback メソッド](ihostmemorymanager-registermemorynotificationcallback-method.md)|コンピューターの現在のメモリ負荷を CLR に通知するために、ホストが呼び出すコールバック関数へのポインターを登録します。|  
|[ReleasedVirtualAddressSpace メソッド](ihostmemorymanager-releasedvirtualaddressspace-method.md)|指定されたメモリを使用して CLR が終了したことをホストに通知します。|  
|[VirtualAlloc メソッド](ihostmemorymanager-virtualalloc-method.md)|対応する Win32 関数の論理ラッパーとして機能します。これは、呼び出し元プロセスの仮想アドレス空間にあるページの領域を予約またはコミットします。|  
|[VirtualFree メソッド](ihostmemorymanager-virtualfree-method.md)|呼び出しプロセスの仮想アドレス空間内のページの領域を解放、デ、または解放してデする、対応する Win32 関数の論理ラッパーとして機能します。|  
|[VirtualProtect メソッド](ihostmemorymanager-virtualprotect-method.md)|対応する Win32 関数の論理ラッパーとして機能します。これにより、呼び出し元プロセスの仮想アドレス空間でコミットされたページの領域の保護が変更されます。|  
|[VirtualQuery メソッド](ihostmemorymanager-virtualquery-method.md)|対応する Win32 関数の論理ラッパーとして機能し、呼び出し元プロセスの仮想アドレス空間にあるページの範囲に関する情報を取得します。|  
  
## <a name="remarks"></a>注釈  

 `IHostMemoryManager` また、は、ヒープ上でメモリ要求を行うためのポインターを取得し、ホストによって報告されたプロセスのメモリ負荷のレベルを取得するために、CLR のメソッドも提供します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostMalloc インターフェイス](ihostmalloc-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
