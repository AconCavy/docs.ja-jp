---
title: ICeeGen::GetSectionCreate メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de3a9c152f3074339dba330b7827cf795a7e537
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745976"
---
# <a name="iceegengetsectioncreate-method"></a>ICeeGen::GetSectionCreate メソッド
生成し、指定した名前とフラグの値を使用してコードのセクションを取得します。  
  
 このメソッドは廃止され、使用する必要があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `name`  
 [in]作成するセクションの名前を指定する文字列へのポインター。  
  
 `flags`  
 [in]オプションを指定するフラグ。  
  
 `section`  
 [out]新しく作成されたコード セクションへのポインター。  
  
## <a name="remarks"></a>Remarks  
 呼び出す`GetSectionCreate`別の方法で処理されない特別なセクションの要件がある場合にのみです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICeeGen インターフェイス](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
