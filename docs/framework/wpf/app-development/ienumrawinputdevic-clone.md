---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: abc8a6e4780c8fe50afcf1b04f7e14aeb6452704
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949592"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
同じリストを反復処理するため、現在の列挙子と同じ状態の別の未加工入力デバイスの列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppenum`  
  
 [out]受け取る出力変数のアドレス、 [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md)インターフェイス ポインター。 メソッドが成功した場合は、この output 変数の値が定義されていません。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 HRESULT:このメソッドでは、標準の戻り値 E_INVALIDARG、E_UNEXPECTED、E_OUTOFMEMORY をサポートしています。  
  
## <a name="remarks"></a>Remarks  
 このメソッドでは、後でそのポイントに返すために列挙体シーケンス内のポイントを録音することです。 呼び出し元は、最初の列挙子から個別にこの新しい列挙子を解放する必要があります。
