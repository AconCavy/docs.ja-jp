---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime メソッド
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d5149c7e3430c5e7c59a47c4ab5dc98d878de39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766669"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>ICLRAppDomainResourceMonitor::GetCurrentCpuTime メソッド
アプリケーション ドメインが作成されたために、現在のアプリケーション ドメインで実行中にすべてのスレッドによって使用されているプロセッサの合計時間を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwAppDomainId`  
 [in]要求されたアプリケーション ドメインの ID。  
  
 `pMilliseconds`  
 [out]アプリケーション ドメインが作成されたために、現在のアプリケーション ドメインで実行中にすべてのスレッドによって使用されているプロセッサの合計時間へのポインター。 このパラメーターは、`null` に設定できます。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|COR_E_APPDOMAINUNLOADED|アプリケーション ドメインがアンロードされたか、存在しません。|  
|E_FAIL|アプリケーション ドメインのリソース監視が有効になっていません。<br /><br /> \- または -<br /><br /> その他のすべてのエラー。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドはアンマネージと同等のマネージ<xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>プロパティ。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAppDomainResourceMonitor インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [アプリケーション ドメインのリソース監視](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
