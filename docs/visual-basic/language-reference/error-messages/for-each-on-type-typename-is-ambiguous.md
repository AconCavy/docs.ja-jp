---
title: 型が、'System.Collections.Generic.IEnumerable(Of T)' の複数のインスタンス生成を実装するため、型 '<typename>' の 'For Each' は不適切です。
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: d04a77291ecf09f88ad189667540e9e353246f28
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874079"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="6ae33-102">型が、'System.Collections.Generic.IEnumerable(Of T)' の複数のインスタンス生成を実装するため、型 '\<typename>' の 'For Each' は不適切です。</span><span class="sxs-lookup"><span data-stu-id="6ae33-102">'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>

<span data-ttu-id="6ae33-103">`For Each` ステートメントで、複数の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを含む反復子変数を指定しています。</span><span class="sxs-lookup"><span data-stu-id="6ae33-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="6ae33-104">反復子変数は、.NET Framework の `Collections` 名前空間のいずれかに <xref:System.Collections.IEnumerable?displayProperty=nameWithType> または <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> インターフェイスを実装する型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae33-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the .NET Framework.</span></span> <span data-ttu-id="6ae33-105">1 つのクラスで複数の構築されたジェネリック インターフェイスを、それぞれの構築に異なる型引数を使用して実装することができます。</span><span class="sxs-lookup"><span data-stu-id="6ae33-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="6ae33-106">これを行うクラスが反復子変数に使用されている場合、その変数には複数の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="6ae33-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="6ae33-107">このような場合、Visual Basic で呼び出すメソッドを選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="6ae33-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="6ae33-108">**エラー ID:** BC32096</span><span class="sxs-lookup"><span data-stu-id="6ae33-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6ae33-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6ae33-109">To correct this error</span></span>  
  
- <span data-ttu-id="6ae33-110">[DirectCast 演算子](../operators/directcast-operator.md)または [TryCast 演算子](../operators/trycast-operator.md)を使用して、反復子変数の型を、使用する <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを定義するインターフェイスにキャストします。</span><span class="sxs-lookup"><span data-stu-id="6ae33-110">Use [DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ae33-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ae33-111">See also</span></span>

- [<span data-ttu-id="6ae33-112">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="6ae33-112">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="6ae33-113">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6ae33-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
