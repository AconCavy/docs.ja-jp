---
title: 型 'Object' の引数を使う場合は、'FilePut' ではなく 'FilePutObject' を使用してください。
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: c6ae755ad3eca4b1c50b83049885b6cf66f13c07
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100335"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>型 'Object' の引数を使う場合は、'FilePut' ではなく 'FilePutObject' を使用してください。

`FilePut` メソッドには、型 `Object`の引数が含まれています。 あいまいさを避けるため、`FilePutObject` の代わりに `FilePut` を使用する必要があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- `FilePut` を `FilePutObject` で置き換え  
  
- `Object` 引数をより具体的な種類にキャストします。  
  
- `My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。  
  
## <a name="see-also"></a>関連項目

- [マイファイル (コンピューター)](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My. Computer. FileSystem. WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
