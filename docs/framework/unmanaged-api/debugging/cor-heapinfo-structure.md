---
title: COR_HEAPINFO 構造体
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: 5400350e1c489ec4c2ff3cddf83a4f1a8a0c7947
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726601"
---
# <a name="cor_heapinfo-structure"></a>COR_HEAPINFO 構造体

列挙可能かどうかなど、ガベージ コレクション ヒープに関する情報が提供されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`areGCStructuresValid`|`true` ガベージコレクション構造体が有効で、ヒープを列挙できる場合は。それ以外の場合は `false` 。|  
|`pointerSize`|ターゲットアーキテクチャのポインターのサイズ (バイト単位)。|  
|`numHeaps`|プロセス内の論理ガベージコレクションヒープの数。|  
|`concurrent`|`TRUE` 同時実行 (バックグラウンド) ガベージコレクションが有効な場合は。それ以外の場合は `FALSE` 。|  
|`gcType`|ガベージコレクターがワークステーションまたはサーバーのどちらで実行されているかを示す [CorDebugGCType](cordebuggctype-enumeration.md) 列挙体のメンバー。|  
  
## <a name="remarks"></a>注釈  

 構造体のインスタンス `COR_HEAPINFO` は、 [ICorDebugProcess5:: Getg apinformation](icordebugprocess5-getgcheapinformation-method.md) メソッドを呼び出すことによって返されます。  
  
 ガベージコレクションヒープ上のオブジェクトを列挙する前に、必ずフィールドをチェックし `areGCStructuresValid` て、ヒープが列挙可能な状態であることを確認する必要があります。 詳細については、「 [ICorDebugProcess5:: Getg](icordebugprocess5-getgcheapinformation-method.md) 」を参照してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
