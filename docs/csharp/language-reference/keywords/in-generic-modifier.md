---
title: in (ジェネリック修飾子) - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: f736540a37d3226bccfc07749dcf06ca018663e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694572"
---
# <a name="in-generic-modifier-c-reference"></a>in (ジェネリック修飾子) (C# リファレンス)

ジェネリック型パラメーターの `in` キーワードは、型パラメーターが反変であることを指定します。 `in` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。

反変性は、ジェネリック パラメーターによって指定された型よりも弱い派生型を使用できるようにする機能です。 これにより、反変性のインターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。 ジェネリック型パラメーターの共変性および反変性は参照型ではサポートされますが、値型ではサポートされません。

型をジェネリック インターフェイスまたはデリゲートで反変として宣言できるのは、メソッドの戻り値の型ではなく、メソッドのパラメーターの型を定義する場合のみです。 `in`、`ref`、`out` パラメーターはインバリアントである必要があります。これは、これらのパラメーターが共変でも反変でもないことを意味します。

反変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、インターフェイス型パラメーターによって指定された型よりも弱い派生型の引数を受け取ることができます。 たとえば、<xref:System.Collections.Generic.IComparer%601> インターフェイスでは、T 型が反変なので、`Employee` が `Person` を継承する場合、特別な変換メソッドを使用しなくても `IComparer<Person>` 型のオブジェクトを `IComparer<Employee>` 型のオブジェクトに割り当てることができます。

反変のデリゲートには、型は同じでありながらより弱い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。

詳細については、「[共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)」を参照してください。

## <a name="contravariant-generic-interface"></a>反変のジェネリック インターフェイス

次の例では、反変のジェネリック インターフェイスを宣言、拡張、および実装する方法を示します。 また、このインターフェイスを実装するクラスの暗黙的な変換を使用する方法も示します。

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>反変の汎用デリゲート

次の例では、反変の汎用デリゲートを宣言、インスタンス化、および呼び出す方法を示します。 また、デリゲート型を暗黙的に変換する方法も示します。

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [out](out-generic-modifier.md)
- [共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)
- [修飾子](modifiers.md)
