---
title: アトミック化された XName および XNamespace オブジェクト (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: 0ffed5d00364f6614b439480607ed521f52754ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345727"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="efc90-102">アトミック化された XName および XNamespace オブジェクト (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efc90-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="efc90-103"><xref:System.Xml.Linq.XName> オブジェクトと <xref:System.Xml.Linq.XNamespace> オブジェクトは "*アトミック化*" されています。つまり、同じ修飾名を含んでいる場合は、同じオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="efc90-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="efc90-104">これによってクエリのパフォーマンスが向上します。これは、2 つのアトミック化された名前の等価性を比べる場合に、基になる中間言語が、2 つの参照が同じオブジェクトを指しているかどうかを判別するだけで済むためです。</span><span class="sxs-lookup"><span data-stu-id="efc90-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="efc90-105">基になるコードは、時間のかかる文字列比較を行う必要がありません。</span><span class="sxs-lookup"><span data-stu-id="efc90-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>

## <a name="atomization-semantics"></a><span data-ttu-id="efc90-106">アトミック化のセマンティクス</span><span class="sxs-lookup"><span data-stu-id="efc90-106">Atomization Semantics</span></span>

<span data-ttu-id="efc90-107">アトミック化とは、2 個の <xref:System.Xml.Linq.XName> オブジェクトのローカル名が同じであり、これらのオブジェクトが同じ名前空間にある場合に、同じインスタンスを共有するという意味です。</span><span class="sxs-lookup"><span data-stu-id="efc90-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="efc90-108">同様に、2 個の <xref:System.Xml.Linq.XNamespace> オブジェクトに同じ名前空間 URI がある場合も、これらのオブジェクトは同じインスタンスを共有します。</span><span class="sxs-lookup"><span data-stu-id="efc90-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>

<span data-ttu-id="efc90-109">アトミック化されたオブジェクトをクラスに対して有効にするには、クラスのコンストラクターがパブリックではなく、プライベートであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="efc90-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="efc90-110">その理由は、コンストラクターがパブリックであれば、アトミック化されていないオブジェクトを作成できるからです。</span><span class="sxs-lookup"><span data-stu-id="efc90-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="efc90-111"><xref:System.Xml.Linq.XName> クラスと <xref:System.Xml.Linq.XNamespace> クラスは暗黙的な変換演算子を実装して、文字列を <xref:System.Xml.Linq.XName> または <xref:System.Xml.Linq.XNamespace> に変換します。</span><span class="sxs-lookup"><span data-stu-id="efc90-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="efc90-112">この方法でこれらのオブジェクトのインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="efc90-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="efc90-113">コンストラクターにはアクセスできないため、コンストラクターを使用してインスタンスを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="efc90-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>

<span data-ttu-id="efc90-114"><xref:System.Xml.Linq.XName> と <xref:System.Xml.Linq.XNamespace> は等値演算子と非等値演算子も実装して、比較する 2 個のオブジェクトが同じインスタンスを参照しているかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="efc90-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>

## <a name="example"></a><span data-ttu-id="efc90-115">例</span><span class="sxs-lookup"><span data-stu-id="efc90-115">Example</span></span>

<span data-ttu-id="efc90-116">次のコードは <xref:System.Xml.Linq.XElement> オブジェクトを作成して、同じ名前が同じインスタンスを共有することを示します。</span><span class="sxs-lookup"><span data-stu-id="efc90-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

<span data-ttu-id="efc90-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="efc90-117">This example produces the following output:</span></span>

```console
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

<span data-ttu-id="efc90-118">前述のように、アトミック化されたオブジェクトの利点は、パラメーターとして <xref:System.Xml.Linq.XName> がある軸メソッドの 1 つを使用するときに、目的の要素を選択するために、軸メソッドが、2 つの名前が同じインスタンスを参照していることを判別するだけで済むことです。</span><span class="sxs-lookup"><span data-stu-id="efc90-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>

<span data-ttu-id="efc90-119">次の例では、<xref:System.Xml.Linq.XName> を <xref:System.Xml.Linq.XContainer.Descendants%2A> メソッド呼び出しに渡すので、アトミック化パターンによってパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="efc90-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

<span data-ttu-id="efc90-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="efc90-120">This example produces the following output:</span></span>

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a><span data-ttu-id="efc90-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="efc90-121">See also</span></span>

- [<span data-ttu-id="efc90-122">パフォーマンス (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efc90-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
