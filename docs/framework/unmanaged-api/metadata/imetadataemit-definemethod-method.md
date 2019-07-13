---
title: IMetaDataEmit::DefineMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4297b21970fbca4b5aa53c31680394cab358d255
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777602"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod メソッド
指定したシグネチャを持つメソッドまたはグローバル関数の定義を作成し、そのメソッドの定義にトークンを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]`mdTypedef`親クラスまたはメソッドの親インターフェイスのトークン。 設定`td`に`mdTokenNil`グローバル関数を定義する場合、します。  
  
 `szName`  
 [in]Unicode でメンバーの名前。  
  
 `dwMethodFlags`  
 [in]値、 [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)メソッドまたはグローバル関数の属性を指定する列挙体。  
  
 `pvSigBlob`  
 [in]メソッド シグネチャ。 提供される、署名が保持されます。 任意のパラメーターの追加情報を指定する必要がある場合、 [imetadataemit::setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)メソッド。  
  
 `cbSigBlob`  
 [in]内のバイト数`pvSigBlob`します。  
  
 `ulCodeRVA`  
 [in]コードのアドレス。  
  
 `dwImplFlags`  
 [in]値、 [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)メソッドの実装の機能を指定する列挙体。  
  
 `pmd`  
 [out]メンバー トークンです。  
  
## <a name="remarks"></a>Remarks  
 メタデータ API が、呼び出し元が指定された外側のクラスまたはインターフェイスで指定された出力に、同じ順序でメソッドを保持するには、`td`パラメーター。  
  
 使用に関する追加情報`DefineMethod`し、特定のパラメーターの設定のとおりです。  
  
## <a name="slots-in-the-v-table"></a>V テーブル内のスロット  
 ランタイムでは、メソッドの定義を使用して、v テーブル スロットを設定します。 1 つまたは複数のスロットがスキップする必要がある場合、COM インターフェイスのレイアウトでパリティを保持するか、ダミー メソッドが定義されて v テーブル内のスロットを占有するには設定、`dwMethodFlags`に、`mdRTSpecialName`の値、 [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列挙型として名前を指定します。  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 場所*SequenceNumber*メソッドのシーケンス番号と*CountOfSlots* v テーブルでスキップするスロットの数です。 場合*CountOfSlots*は省略すると、1 が使用されます。 これらのダミー メソッドは、マネージまたはアンマネージ コードから呼び出すことでありしようとすると、これらをマネージまたはアンマネージ コードから呼び出すには、例外が生成されます。 その唯一の目的では、COM の統合ランタイムが生成する v テーブルの領域を占有します。  
  
## <a name="duplicate-methods"></a>メソッドが重複しています  
 重複するメソッドを定義する必要があります。 つまり、呼び出す必要はありません`DefineMethod`重複する一連の値の`td`、 `wzName`、および`pvSig`パラメーター。 (これら 3 つのパラメーター、メソッドを一意に定義します。)。 メソッド定義の 1 つが設定されている、重複する 3 つの要素を使用するただし、`mdPrivateScope`ビット、`dwMethodFlags`パラメーター。 (、`mdPrivateScope`ビットは、コンパイラはこのメソッドの定義への参照を出力しないことを意味します)。  
  
## <a name="method-implementation-information"></a>メソッドの実装に関する情報  
 メソッドの実装の詳細については多くの場合、メソッドの宣言時に呼ばれます。 そのため、必要はありませんで値を渡す、`ulCodeRVA`と`dwImplFlags`を呼び出すときに、パラメーター`DefineMethod`します。 後でを通じて値を指定することができます[imetadataemit::setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)または[imetadataemit::setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)必要に応じて、します。  
  
 プラットフォーム呼び出し (PInvoke) または COM 相互運用のシナリオなど、いくつかの状況でメソッドの本体を指定できませんと`ulCodeRVA`0 に設定する必要があります。 このような場合は、メソッドはタグが付いていない抽象として、ランタイムは、実装を見つけるため。  
  
## <a name="defining-a-method-for-pinvoke"></a>PInvoke のメソッドを定義します。  
 PInvoke によって呼び出される各アンマネージ関数では、非管理対象の関数を表すマネージ メソッドを定義する必要があります。 マネージ メソッドを定義するには、使用`DefineMethod`PInvoke を使用する方法に応じて、特定の値に設定されているパラメーターの一部で。  
  
- PInvoke の true - アンマネージ DLL 内にある外部のアンマネージ メソッドの呼び出しが含まれます。  
  
- ローカルの PInvoke - には、現在のマネージ モジュール内に埋め込まれているネイティブのアンマネージ メソッドの呼び出しが含まれます。  
  
 パラメーターの設定は、次の表に付与されます。  
  
|パラメーター|PInvoke が true の値|ローカルの PInvoke の値|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||設定`mdStatic`クリア;`mdSynchronized`と`mdAbstract`します。|  
|`pvSigBlob`|有効な共通言語ランタイム (CLR) メソッド署名で有効なパラメーターはマネージ型です。|有効なパラメーターを持つ有効な CLR メソッド署名はマネージ型です。|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|設定`miCil`と`miManaged`します。|設定`miNative`と`miUnmanaged`します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
