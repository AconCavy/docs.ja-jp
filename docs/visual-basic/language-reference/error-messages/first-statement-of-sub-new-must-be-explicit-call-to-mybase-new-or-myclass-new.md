---
title: "'<constructorname>' の基本クラス '<baseclassname>' にある '<derivedclassname>' が古い形式に設定されているため、この 'Sub New' の最初のステートメントは、明示的な 'MyBase.New' または 'MyClass.New' への呼び出しでなければなりません: '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 89b6c241bb637f2efc6014c4640b3b463c4facfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801882"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a>この 'Sub New' の最初のステートメントは、ためには、'mybase.new' または 'myclass.new' の明示的な呼び出しにある必要があります、'\<ある >' の基底クラスの\<baseclassname >' の'\<derivedclassname >' 旧式とマークされて: '\<errormessage >'
クラス コンストラクターが基底クラスのコンストラクターを明示的に呼び出さず、暗黙的な基底クラスのコンストラクターが <xref:System.ObsoleteAttribute> 属性およびエラーとして扱うことを示すディレクティブでマークされています。  
  
 派生クラスのコンス トラクターが基底クラスのコンス トラクターを呼び出さない場合、Visual Basic はパラメーターなしの基本クラス コンス トラクターへの暗黙の呼び出しを生成しようとします。 引数を指定せずに呼び出すことができる基底クラスにアクセス可能なコンス トラクターがない場合、Visual Basic は、暗黙の呼び出しを生成できません。 この場合、必要なコンス トラクターがでマークされた、<xref:System.ObsoleteAttribute>属性は、Visual Basic で呼び出すことはできませんので。  
  
 <xref:System.ObsoleteAttribute> を適用することで、任意のプログラミング要素を使用しない要素としてマークできます。 これを行う場合は、属性の<xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False`に設定できます。 `True`に設定した場合、コンパイラは要素を使用する試みをエラーとして扱います。 `False`に設定した場合、または既定値の `False`を使用した場合、コンパイラは要素を使用する試みに対して警告を発行します。  
  
 **エラー ID:** BC30920  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 引用符で囲まれたエラー メッセージを確認し、適切な処理を行います。  
  
2. `MyBase.New()` または `MyClass.New()` の呼び出しを `Sub New` の最初のステートメントとして派生クラスに含めます。  
  
## <a name="see-also"></a>関連項目

- [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)
