---
title: "'AddressOf' オペランドはメソッドの名前でなければなりません。かっこは不要です。"
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: b8c67c2390df91c6a4af66e020365544e6bf369b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751632"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a>'AddressOf' オペランドはメソッドの名前でなければなりません。かっこは不要です。
`AddressOf` 演算子は、特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。 構文は次のとおりです。  
  
 `AddressOf` `procedurename`  
  
 かっこで囲んで引数以下を挿入した`AddressOf`none は必要に応じて、します。  
  
 **エラー ID:** BC30577  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 次の引数を囲むかっこを削除`AddressOf`します。  
  
2. 引数がメソッド名を確認します。  
  
## <a name="see-also"></a>関連項目

- [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)
