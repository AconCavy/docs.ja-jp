---
title: ICorRuntimeHost::CreateEvidence メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3b17ca32051cd5fc0673ef26124b855a66f9785
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779983"
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence メソッド
型のインターフェイス ポインターを取得<xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>、ホストに渡すセキュリティ証拠を作成することができます、 [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)または[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pEvidence`  
 [out]インターフェイス ポインターを<xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>インスタンスのセキュリティ証拠を作成するために使用します。 このポインターは型指定`IUnknown`呼び出し元が呼び出す通常必要がありますので、`QueryInterface`へのポインターを取得するには、このインターフェイスで、<xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|操作が正常に完了しました。|  
|S_FALSE|操作を完了できませんでした。|  
|E_FAIL|未知の致命的なエラーが発生しました。 場合は、メソッドは、E_FAIL を返します、共通言語ランタイム (CLR) はプロセスで使用可能ではなくなりました。 Api をホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、ネイティブ コードから設定することはできません、空のコレクションを返します。 使用する必要があります、<xref:System.Security.Policy.Evidence>メソッド代わりにします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET framework のバージョン:** 1.0, 1.1  
  
## <a name="see-also"></a>関連項目

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
