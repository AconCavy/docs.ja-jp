---
title: ICLRRuntimeInfo::LoadLibrary メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65ac05a524297029ca50970bdd231c6a9112e35c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748385"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a>ICLRRuntimeInfo::LoadLibrary メソッド
によって表される共通言語ランタイム (CLR) から .NET Framework ライブラリを読み込み、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイス。  
  
 このメソッドは、 [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)関数。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzDllName`  
 [in]読み込まれるアセンブリの名前。  
  
 `phndModule`  
 [out]読み込まれたアセンブリへのハンドル。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pwzDllName` または `phndModule` が null です。|  
|E_OUTOFMEMORY|メモリが不足は、要求を処理するために使用できます。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、.NET Framework 再頒布可能パッケージに含まれている Dll のみを読み込みます。 ユーザーが生成したアセンブリを読み込むことことはできません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRRuntimeInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
