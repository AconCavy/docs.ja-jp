---
title: ICeeGen::GetSectionBlock メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84ccbd7a8be7d90a541fb2d54baa3d7f66d3d31e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746120"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock メソッド
コード ベースのセクションのブロックを取得します。  
  
 このメソッドは廃止され、使用する必要があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
## <a name="parameters"></a>パラメーター  
 `section`  
 [in]コード ベースのブロックの取得元となるセクション。  
  
 `len`  
 [in]取得するブロックの長さ。  
  
 `align`  
 [in]ブロックの最初のバイトを揃えるセクションの先頭からの相対バイト。 これは、セクション内のブロックの位置です。  
  
 `ppBytes`  
 [out]取得されたブロックのアドレスを受け取る場所へのポインター。  
  
## <a name="remarks"></a>Remarks  
 呼び出す`GetSectionBlock`別の方法で処理されない特別なセクションの要件がある場合にのみです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICeeGen インターフェイス](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
