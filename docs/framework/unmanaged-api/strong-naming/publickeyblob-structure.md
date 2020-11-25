---
title: PublicKeyBlob 構造体
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
ms.openlocfilehash: 42cd3cc22fbbb8eb3d5ac44544fce36650b6461f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705931"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob 構造体

公開キーと秘密キーのペアの公開キーをバイナリ形式で表します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`SigAlgId`|`ALG_ID`公開キーの署名アルゴリズム (WinCrypt .h で定義されている型の) の識別子。|  
|`HashAlgId`|`ALG_ID`公開キーのハッシュアルゴリズム (WinCrypt .h で定義されている型の) の識別子。|  
|`cbPublicKey`|キーの長さ (バイト単位)。|  
|`PublicKey`|CryptoAPI によって返される形式のキー値を格納する可変長バイト配列。|  
  
## <a name="remarks"></a>注釈  

 `PublicKeyBlob`構造体は、公開キーと秘密キーのペアの公開キーを表すために、 [StrongNameGetPublicKey](strongnamegetpublickey-function.md)、 [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)、およびその他の厳密な名前関数によって使用されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameGetPublicKey 関数](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration 関数](strongnamesignaturegeneration-function.md)
