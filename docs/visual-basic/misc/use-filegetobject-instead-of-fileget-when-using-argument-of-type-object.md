---
title: 型 'Object' の引数を使用する場合は、'FileGet' ではなく 'FileGetObject' を使用してください。
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 318a0772a99aa86d9a4633e6021f77616a43fc7e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059406"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>型 'Object' の引数を使用する場合は、'FileGet' ではなく 'FileGetObject' を使用してください。

`FileGet` メソッドには、型 `Object`の引数が含まれています。 あいまいさを避けるため、`FileGetObject` の代わりに `FileGet` を使用する必要があります。  
  
 `My.Computer.Filesystem` によって提供される機能は、`FileGet` または `FileGetObject` よりも使いやすく、パフォーマンスが優れています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `FileGet` を `FileGetObject` で置き換え  
  
2. `Object` 引数をより具体的な種類にキャストします。  
  
## <a name="see-also"></a>こちらもご覧ください

- [マイファイル (コンピューター)](xref:Microsoft.VisualBasic.FileIO.FileSystem)
