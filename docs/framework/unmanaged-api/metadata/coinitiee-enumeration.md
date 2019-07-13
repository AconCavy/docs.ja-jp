---
title: COINITIEE 列挙型
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23f5a2b6b0970f3cb64ee339e6a1a409354a60e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780952"
---
# <a name="coinitiee-enumeration"></a>COINITIEE 列挙型
使用される定数を指定します[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)共通言語ランタイムを初期化するときにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|既定の初期化モード。 ランタイムを初期化し、既定値を作成します。 この<xref:System.AppDomain>します。|  
|`COINITEE_DLL`|マネージ DLL を実行することを初期化します。|  
|`COINITEE_MAIN`|マネージ EXE を実行することを初期化します。 これは、ランタイムを初期化しますが、既定値は作成されません<xref:System.AppDomain>、これは、exe ファイルのメイン ルーチンを入力した後に作成されます。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
