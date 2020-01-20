---
title: 匿名型を射影する方法 (C#)
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 7797c8bfb12943af1ce7f975b170bf002aa7d6fc
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345730"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="dde2b-102">匿名型を射影する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="dde2b-102">How to project an anonymous type (C#)</span></span>
<span data-ttu-id="dde2b-103">短期間しか使用しないことがわかっている新しい型にクエリを射影することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dde2b-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="dde2b-104">単に射影で使用するために新しい型を作成するのは大きな負担です。</span><span class="sxs-lookup"><span data-stu-id="dde2b-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="dde2b-105">この場合は、匿名型に射影する方法が効率的です。</span><span class="sxs-lookup"><span data-stu-id="dde2b-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="dde2b-106">匿名型を使用すると、クラス名を指定することなくクラスを定義し、そのクラスのオブジェクトを宣言して初期化できます。</span><span class="sxs-lookup"><span data-stu-id="dde2b-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="dde2b-107">匿名型とは、*タプル*の数学的概念を C# で実装したものです。</span><span class="sxs-lookup"><span data-stu-id="dde2b-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="dde2b-108">タプルという数学用語は、1 タプル、2 タプル、3 タプル、4 タプル、5 タプル、n タプルという数列に基づいています。</span><span class="sxs-lookup"><span data-stu-id="dde2b-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="dde2b-109">組とは、それぞれが特定の型を持つオブジェクトの有限のシーケンスを意味します。</span><span class="sxs-lookup"><span data-stu-id="dde2b-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="dde2b-110">名前と値のペアの一覧と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="dde2b-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="dde2b-111">たとえば、[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) の XML ドキュメントのアドレス コンテンツは次のように表されます。</span><span class="sxs-lookup"><span data-stu-id="dde2b-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="dde2b-112">匿名型のインスタンスを作成するときは、注文 n のタプルを作成すると考えると簡単です。</span><span class="sxs-lookup"><span data-stu-id="dde2b-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="dde2b-113">`select` 句でタプルを作成するクエリを記述すると、そのクエリからタプルの `IEnumerable` が返されます。</span><span class="sxs-lookup"><span data-stu-id="dde2b-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dde2b-114">例</span><span class="sxs-lookup"><span data-stu-id="dde2b-114">Example</span></span>  
 <span data-ttu-id="dde2b-115">この例では、`select` 句で匿名型を射影しています。</span><span class="sxs-lookup"><span data-stu-id="dde2b-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="dde2b-116">さらに、`var` を使用して `IEnumerable` オブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="dde2b-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="dde2b-117">`foreach` ループ内では、繰り返し変数が、クエリ式で作成された匿名型のインスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="dde2b-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="dde2b-118">この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:顧客と注文 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)」。</span><span class="sxs-lookup"><span data-stu-id="dde2b-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 <span data-ttu-id="dde2b-119">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="dde2b-119">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  