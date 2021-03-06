---
title: ICLRDomainManager::SetAppDomainManagerType メソッド
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
ms.openlocfilehash: 7c6b328793e6437682ad8d642e611be30e7b0fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702148"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType メソッド

<xref:System.AppDomainManager?displayProperty=nameWithType>既定のアプリケーションドメインを初期化するために使用されるアプリケーションドメインマネージャーのクラスから派生した型を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszAppDomainManagerAssembly`  
 からアプリケーションドメインマネージャーの種類を含むアセンブリの表示名です。たとえば、"使用しているバージョン = 1.0.0.0, Culture = ニュートラル, PublicKeyToken = 6856bccf150f00b3" のようになります。  
  
 `wszAppDomainManagerType`  
 から名前空間を含む、アプリケーションドメインマネージャーの型名。  
  
 `dwInitializeDomainFlags`  
 からアプリケーションドメインマネージャーに関する情報を提供する [EInitializeNewDomainFlags](einitializenewdomainflags-enumeration.md) 列挙値の組み合わせ。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
  
## <a name="remarks"></a>注釈  

 現時点では、に対して定義されている値 `dwInitializeDomainFlags` はのみです `eInitializeNewDomainFlags_NoSecurityChanges` 。これは、アプリケーションドメインマネージャーがメソッドの実行中にセキュリティ設定を変更しないことを共通言語ランタイム (CLR) に通知し <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> ます。 これにより、CLR は条件付き (APTCA) 属性を持つアセンブリの読み込みを最適化でき <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ます。 これにより、このアセンブリセットの推移的なクロージャが大きい場合に、起動時間が大幅に向上する可能性があります。  
  
> [!IMPORTANT]
> ホストがアプリケーションドメインマネージャーに対してを指定した場合 `eInitializeNewDomainFlags_NoSecurityChanges` 、 <xref:System.InvalidOperationException> アプリケーションドメインのセキュリティを変更しようとすると、がスローされます。  
  
 [ICLRControl:: SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)メソッドを呼び出すことは、を `ICLRDomainManager::SetAppDomainManagerType` 使用してを呼び出すことと同じです `eInitializeNewDomainFlags_None` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティング](index.md)
- [ICLRDomainManager インターフェイス](iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags 列挙体](einitializenewdomainflags-enumeration.md)
