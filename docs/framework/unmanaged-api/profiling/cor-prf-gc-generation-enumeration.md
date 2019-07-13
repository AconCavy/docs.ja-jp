---
title: COR_PRF_GC_GENERATION 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74e70f58600205d44a9ba052981b2cc67b3a44ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753810"
---
# <a name="corprfgcgeneration-enumeration"></a>COR_PRF_GC_GENERATION 列挙型
ガベージ コレクション ジェネレーションを識別します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|オブジェクトは、ジェネレーション 0 として格納されます。|  
|`COR_PRF_GC_GEN_1`|オブジェクトは、第 1 世代として格納されます。|  
|`COR_PRF_GC_GEN_2`|オブジェクトは、第 2 世代として格納されます。|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|オブジェクトは、大きなオブジェクト ヒープに格納されます。|  
  
## <a name="remarks"></a>Remarks  
 ガベージ コレクターには、年齢に基づいてジェネレーションに分割オブジェクトによってメモリ管理のパフォーマンスが向上します。 現在、ガベージ コレクターは、0、1、2、およびラージ オブジェクトに使用される特殊なヒープ セグメントの番号、3 つの世代を使用します。 サイズが特定の値より大きいオブジェクトは、大きなオブジェクト ヒープに格納されます。 割り当てられたその他のオブジェクトをジェネレーション 0 に属するを起動します。 ジェネレーション 0 ガベージ コレクションが行われた後に存在するすべてのオブジェクトは、第 1 世代に昇格されます。 ジェネレーション 1 のガベージ コレクションが行われた後に存在するオブジェクトは、ジェネレーション 2 に移動します。  
  
 生成結果の使用は、ガベージ コレクターはいつでも割り当てられたオブジェクトのサブセットのみを使用することを意味します。  
  
 `COR_PRF_GC_GENERATION`列挙型を使用して、 [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)構造体。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
