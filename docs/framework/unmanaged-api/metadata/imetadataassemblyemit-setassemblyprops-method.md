---
title: IMetaDataAssemblyEmit::SetAssemblyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34335321207e98a518ff3e0fdb5ea1dc3ac68b75
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776259"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps メソッド
指定された `Assembly` メタデータ構造体を変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pma`  
 [in]メタデータ トークンを指定する、`Assembly`メタデータ構造を変更します。  
  
 `pbPublicKey`  
 [in]アセンブリの発行者の公開キーへのポインター。  
  
 `cbPublicKey`  
 [in]バイト サイズ`pbPublicKey`します。  
  
 `ulHashAlgId`  
 [in]アセンブリ ファイルをハッシュするために使用するハッシュ アルゴリズムの識別子。  
  
 `szName`  
 [in]アセンブリの人間が判読できるテキストの名前。  
  
 `pMetaData`  
 [in]アセンブリのバージョン、プラットフォーム、およびロケールの情報を含む ASSEMBLYMETADATA へのポインター。  
  
 `dwAssemblyFlags`  
 [in]ビットごとの組み合わせ[AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)アセンブリのさまざまな属性を指定する値。  
  
## <a name="remarks"></a>Remarks  
 作成する、`Assembly`メタデータ構造体を使用して、 [imetadataassemblyemit::defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
