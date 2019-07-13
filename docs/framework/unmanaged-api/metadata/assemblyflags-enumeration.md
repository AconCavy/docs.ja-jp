---
title: AssemblyFlags 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 502e7841f8c413aa48732bcea0b6c2178d70c061
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776450"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags 列挙体
アセンブリの実行時の機能を記述する値が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`afImplicitExportedTypes`|エクスポートされた種類の定義がアセンブリを構成するファイル内で暗黙的なを指定します。 .NET Framework バージョン 1.0 および 1.1 では、この値は常に設定されると想定します。|  
|`afImplicitResources`|リソース定義がアセンブリを構成するファイル内で暗黙的なを指定します。 .NET Framework 1.0 および 1.1 では、この値は常に設定されると想定します。|  
|`afNonSideBySideAppDomain`|アセンブリは他のバージョンが同じアプリケーション ドメインで実行されている場合に実行できないことを指定します。|  
|`afNonSideBySideProcess`|アセンブリは他のバージョンが同じプロセスで実行されている場合に実行できないことを指定します。|  
|`afNonSideBySideMachine`|アセンブリは他のバージョンが同じコンピューターで実行されている場合に実行できないことを指定します。|  
  
## <a name="remarks"></a>Remarks  
 参照アセンブリのサイド バイ サイドでの互換性機能を記述する 0x0010 と 0x0070、両端を含むまでの値が使用されます。 これらの値を設定すると、アセンブリがサイド バイ サイドで互換性のあると見なされます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MsCorEE.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
