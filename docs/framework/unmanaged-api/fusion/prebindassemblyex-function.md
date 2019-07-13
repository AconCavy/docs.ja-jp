---
title: PreBindAssemblyEx 関数
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a23d3c4fd8eef2e361abf1602157cb4fbb820b48
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773862"
---
# <a name="prebindassemblyex-function"></a>PreBindAssemblyEx 関数
アセンブリのポリシー適用後の表示名を取得します。  
  
 この関数は、.NET Framework インフラストラクチャをサポートし、コードから直接使用するものではありません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAppCtx`  
 [in]アプリケーションのコンテキストを識別します。  
  
 `pName`  
 [in]アセンブリ名を識別します。  
  
 `pAsmParent`  
 [in]親アセンブリを識別します。 このパラメーターは無視されます。  
  
 `pwzRuntimeVersion`  
 [in]ランタイムのバージョンを識別します。  
  
 `ppNamePostPolicy`  
 [out]後のポリシーの表示名が含まれています。  
  
 `pvReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `pvReserved` null 参照である必要があります。  
  
## <a name="remarks"></a>Remarks  
 `ppNamePostPolicy`関数が HRESULT FUSION_E_REF_DEF_MISMATCH を返す場合にのみ、出力パラメーターを設定します。 それ以外の場合、これが null です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
