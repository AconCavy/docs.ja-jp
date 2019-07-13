---
title: SetManifestFile メソッド
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 825bb945e0d8662a4dadc9d688de6a677165df4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741469"
---
# <a name="setmanifestfile-method"></a>SetManifestFile メソッド
使用すると、指定するか、リンカーがアセンブリを作成するときに使用するマニフェスト ファイルをリセットできます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `pszFile`  
  
 内容が Win32 リソースの blob に格納するマニフェスト ファイルの名前。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は、S_OK を返します。  
  
## <a name="remarks"></a>Remarks  
 これを呼び出して、Win32ResBlob を求めます。 値、`pszFile`パラメーターは、内容の読み取りおよび RT_MANIFEST の ID で Win32 リソースにマニフェスト ファイルの名前。 NULL のパラメーターを使用して呼び出されると、以前に読み取られた、マニフェストはクリアされます。 これにより、1 つの初期化時に、リンカーの状態をリセットすることができます。  
  
## <a name="requirements"></a>必要条件  
 ALink.h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink3 インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
- [IALink インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Al.exe (アセンブリ リンカー)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
