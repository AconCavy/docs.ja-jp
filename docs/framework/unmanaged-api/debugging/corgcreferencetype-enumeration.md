---
title: CorGCReferenceType 列挙型
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cbecd5be9b1ac7c08e6970933a48eeb95f01a22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739377"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType 列挙型
ガベージ コレクトされる必要のあるオブジェクトのソースを識別します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー名|説明|  
|-----------------|-----------------|  
|`CorHandleStrong`|オブジェクト ハンドル テーブルからの強い参照へのハンドル。|  
|`CorHandleStrongPinning`|オブジェクト ハンドル テーブルから固定された強い参照へのハンドル。|  
|`CorHandleWeakShort`|オブジェクト ハンドル テーブルからの弱い参照をへのハンドル。|  
|`CorHandleWeakRefCount`|オブジェクト ハンドル テーブルから弱い参照カウント オブジェクトへのハンドル。|  
|`CorHandleStrongRefCount`|オブジェクト ハンドル テーブルから参照カウント オブジェクトへのハンドル。|  
|`CorHandleStrongDependent`|オブジェクト ハンドル テーブルから、依存オブジェクトへのハンドル。|  
|`CorHandleStrongAsyncPinned`|オブジェクト ハンドル テーブルからの非同期固定オブジェクト。|  
|`CorHandleStrongSizedByref`|ガベージ コレクション時に、すべてのオブジェクトおよびオブジェクト ルートの集合的なクロージャの概算サイズを保持する強力なハンドル。|  
|`CorReferenceStack`|マネージ スタックからの参照。|  
|`CorReferenceFinalizer`|ファイナライザー キューからの参照。|  
|CorHandleStrongOnly|ハンドル テーブルからの強い参照のみを返します。 この値は使用、 [icordebugprocess 5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドのみです。|  
|`CorHandleWeakOnly`|ハンドル テーブルからの弱い参照のみを返します。 この値は使用、 [icordebugprocess 5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドのみです。|  
|`CorHandleAll`|ハンドル テーブルからすべての参照を返します。 この値は使用、 [icordebugprocess 5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドのみです。|  
  
## <a name="remarks"></a>Remarks  
 `CorGCReferenceType`列挙体は次のように使用します。  
  
- 値として、`type`のフィールド、 [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)構造の参照またはハンドルのソースを示します。  
  
- として、`types`への引数、 [icordebugprocess 5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッド、列挙体に含めるハンドルの種類を指定します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
