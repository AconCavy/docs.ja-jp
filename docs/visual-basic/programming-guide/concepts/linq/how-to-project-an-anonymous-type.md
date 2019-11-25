---
title: '方法 : 匿名型を射影する'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: f60c55b9bc25e4691edd275c6e7417fccf5798ab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347740"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="11726-102">How to: Project an Anonymous Type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11726-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="11726-103">短期間しか使用しないことがわかっている新しい型にクエリを射影することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="11726-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="11726-104">単に射影で使用するために新しい型を作成するのは大きな負担です。</span><span class="sxs-lookup"><span data-stu-id="11726-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="11726-105">この場合は、匿名型に射影する方法が効率的です。</span><span class="sxs-lookup"><span data-stu-id="11726-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="11726-106">匿名型を使用すると、クラス名を指定することなくクラスを定義し、そのクラスのオブジェクトを宣言して初期化できます。</span><span class="sxs-lookup"><span data-stu-id="11726-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="11726-107">匿名型とは、*タプル*の数学的概念を C# で実装したものです。</span><span class="sxs-lookup"><span data-stu-id="11726-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="11726-108">タプルという数学用語は、1 タプル、2 タプル、3 タプル、4 タプル、5 タプル、n タプルという数列に基づいています。</span><span class="sxs-lookup"><span data-stu-id="11726-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="11726-109">組とは、それぞれが特定の型を持つオブジェクトの有限のシーケンスを意味します。</span><span class="sxs-lookup"><span data-stu-id="11726-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="11726-110">名前と値のペアの一覧と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="11726-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="11726-111">たとえば、「[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)」という XML ドキュメントでは、住所の内容が次のように表現されます。</span><span class="sxs-lookup"><span data-stu-id="11726-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="11726-112">匿名型のインスタンスを作成するときは、注文 n のタプルを作成すると考えると簡単です。</span><span class="sxs-lookup"><span data-stu-id="11726-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="11726-113">`Select` 句でタプルを作成するクエリを記述すると、そのクエリからタプルの `IEnumerable` が返されます。</span><span class="sxs-lookup"><span data-stu-id="11726-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11726-114">例</span><span class="sxs-lookup"><span data-stu-id="11726-114">Example</span></span>  
 <span data-ttu-id="11726-115">この例では、`Select` 句で匿名型を射影しています。</span><span class="sxs-lookup"><span data-stu-id="11726-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="11726-116">さらに、`Dim` を使用して `IEnumerable` オブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="11726-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="11726-117">`For Each` ループ内では、繰り返し変数が、クエリ式で作成された匿名型のインスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="11726-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="11726-118">この例では、「[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="11726-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 <span data-ttu-id="11726-119">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="11726-119">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="11726-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="11726-120">See also</span></span>

- [<span data-ttu-id="11726-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11726-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
