---
title: IMetaDataInfo::GetFileMapping メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 22af95ef4bd1fca0a8253faa6ce0e1c7a862054d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782661"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping メソッド
マップのファイルとマッピングの種類のメモリ領域を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppvData`  
 [out]マップされたファイルの先頭へのポインター。  
  
 `pcbData`  
 [out]マップ領域のサイズ。 場合`pdwMappingType`は`fmFlat`、これは、ファイルのサイズです。  
  
 `pdwMappingType`  
 [out]A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)マッピングの種類を示す値。 現在の実装の共通言語ランタイム (CLR) 常に返します`fmFlat`します。 その他の値は、将来使用するために予約されています。 ただし、将来のバージョンで有効にすることがありますまたはサービス リリースで他の値であるために、常に、戻り値を確認してください。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|すべての出力が入力されます。|  
|`E_INVALIDARG`|引数の値として NULL が渡されました。|  
|`COR_E_NOTSUPPORTED`|CLR の実装では、メモリ領域に関する情報を提供できません。 これは、次の理由で発生します。<br /><br /> メタデータ スコープが開かれた、`ofWrite`または`ofCopyMemory`フラグ。<br />-なしのメタデータ スコープが開かれた、`ofReadOnly`フラグ。<br />- [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)メソッドがファイルのメタデータ部分のみを開くために使用されました。<br />-ファイルは、ポータブル実行可能 (PE) ファイルではありません。 **注:** これらの条件は、CLR の実装に依存しが将来のバージョンの CLR が緩和される可能性があります。|  
  
## <a name="remarks"></a>Remarks  
 メモリを`ppvData`のみと基になるメタデータ スコープが開いている限りへのポインターが有効です。  
  
 このメソッドを呼び出すことによってメモリにディスク上のファイルのメタデータをマップするときに、機能するために、 [imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)メソッドを指定する必要がある、`ofReadOnly`とフラグを指定する必要があります、`ofWrite`または`ofCopyMemory`フラグ。  
  
 各スコープのファイル マッピングの種類の選択は、CLR の特定の実装に固有です。 ユーザーによって設定ことはできません。 常に、CLR の現在実装`fmFlat`で`pdwMappingType`がこれを変更できますで将来のバージョンの CLR または将来の指定したバージョンのサービス リリースです。 返される値を常に確認する必要があります`pdwMappingType`さまざまな種類がさまざまなレイアウトやオフセットを持つため、します。  
  
 3 つのパラメーターのいずれかの NULL を渡すことはサポートされていません。 メソッドを返します`E_INVALIDARG`出力のいずれもがいっぱいになるとします。 マッピングの種類や領域のサイズを無視すると、プログラムが異常終了があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataInfo インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping 列挙型](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
