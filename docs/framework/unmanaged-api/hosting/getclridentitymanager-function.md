---
title: GetCLRIdentityManager 関数
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
ms.openlocfilehash: 9d1196749e033c71b0c8923d0325eb4886122d1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733660"
---
# <a name="getclridentitymanager-function"></a>GetCLRIdentityManager 関数

共通言語ランタイム (CLR) が id を管理できるようにするインターフェイスへのポインターを取得します。  
  
 この関数は .NET Framework 4 で非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `riid`  
 から `REFIID` 取得するインターフェイスを指定する (インターフェイス識別子)。 この値は IID_ICLRAssemblyIdentityManager または IID_ICLRHostBindingPolicyManager のいずれかである必要があります。  
  
 `ppManager`  
 入出力 [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) または [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) オブジェクトのいずれかのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 関数へのポインターを取得するには、 [GetRealProcAddress](getrealprocaddress-function.md) 関数を呼び出し `GetCLRIdentityManager` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorWks.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
