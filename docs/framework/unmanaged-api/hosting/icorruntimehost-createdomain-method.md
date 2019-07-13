---
title: ICorRuntimeHost::CreateDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fdacb690b31e7b9930825e5d54ef8fc95bb3a5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762132"
---
# <a name="icorruntimehostcreatedomain-method"></a>ICorRuntimeHost::CreateDomain メソッド
アプリケーション ドメインを作成します。 呼び出し元が型のインターフェイス ポインターを受け取る<xref:System._AppDomain>型のインスタンスに<xref:System.AppDomain?displayProperty=nameWithType>します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzFriendlyName`  
 [in]ドメインにわかりやすい名前を指定するために使用する省略可能なパラメーター。 この表示名は、ドメインを識別するためにデバッガーなどのユーザー インターフェイスで表示できます。  
  
 `pIdentityArray`  
 [in]ポインターの省略可能な配列`IIdentity`権限セットを確立するためにセキュリティ ポリシーを通じて割り当てられる証拠を表すインスタンス。 `IIdentity`オブジェクトを取得するには呼び出すことによって、 [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)メソッド。  
  
 `pAppDomain`  
 [out]型のインターフェイス ポインターを<xref:System._AppDomain>のインスタンスに<xref:System.AppDomain?displayProperty=nameWithType>さらに、ドメインを制御できます。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|操作が正常に完了しました。|  
|S_FALSE|操作を完了できませんでした。|  
|E_FAIL|未知の致命的なエラーが発生しました。 場合は、メソッドは、E_FAIL を返します、共通言語ランタイム (CLR) はプロセスで使用可能ではなくなりました。 Api をホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET framework のバージョン:** 1.0, 1.1  
  
## <a name="see-also"></a>関連項目

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
