---
title: 新しい型を射影する方法 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 5205a0c56651271dea0181ed96518c0e9d7f95f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168994"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="4dfa6-102">新しい型を射影する方法 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4dfa6-102">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="4dfa6-103">このセクションにあるその他の例では、<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement>、<xref:System.Collections.Generic.IEnumerable%601> の `string`、および <xref:System.Collections.Generic.IEnumerable%601> の `int` として結果を返すクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="4dfa6-104">これらは一般的な戻り値の型ですが、すべてのシナリオに適切であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="4dfa6-105">多くの場合、クエリを使用して、別の型の <xref:System.Collections.Generic.IEnumerable%601> を返すようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="4dfa6-106">例</span><span class="sxs-lookup"><span data-stu-id="4dfa6-106">Example</span></span>

<span data-ttu-id="4dfa6-107">この例では、`select` 句でオブジェクトをインスタンス化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="4dfa6-108">コードでは、まずコンストラクターを使用して新しいクラスを定義し、次に、式が新しいクラスの新しいインスタンスになるように `select` ステートメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="4dfa6-109">この例では、「[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");
  
        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );
  
        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

<span data-ttu-id="4dfa6-110">この例では、「<xref:System.Xml.Linq.XContainer.Element%2A>単一の子要素を取得する方法 (LINQ to XML) (C#)[」トピックで説明している ](how-to-retrieve-a-single-child-element-linq-to-xml.md) メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="4dfa6-111">また、キャストを使用して、<xref:System.Xml.Linq.XContainer.Element%2A> メソッドによって返された要素の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="4dfa6-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4dfa6-112">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
