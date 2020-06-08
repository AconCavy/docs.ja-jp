---
title: '方法: 射影の型を制御する'
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: 6b809188f68805afcca960bd809e079d997e79c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357258"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a><span data-ttu-id="b8b94-102">方法: プロジェクションの型を制御する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8b94-102">How to: Control the Type of a Projection (Visual Basic)</span></span>
<span data-ttu-id="b8b94-103">射影は、1 つのデータのセットを取得し、フィルター処理し、その形式を変更し、その型も変更するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="b8b94-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="b8b94-104">ほとんどのクエリ式は射影を実行します。</span><span class="sxs-lookup"><span data-stu-id="b8b94-104">Most query expressions perform projections.</span></span> <span data-ttu-id="b8b94-105">このセクション内のクエリ式は、ほとんどが <xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement> に評価されますが、射影の型を制御して別の型のコレクションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="b8b94-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="b8b94-106">このトピックでは、その方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8b94-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8b94-107">例</span><span class="sxs-lookup"><span data-stu-id="b8b94-107">Example</span></span>  
 <span data-ttu-id="b8b94-108">次の例では、`Customer` という新しい型を定義します。</span><span class="sxs-lookup"><span data-stu-id="b8b94-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="b8b94-109">次に、クエリ式の `Customer` 句で新しい `Select` オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="b8b94-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="b8b94-110">これによって、クエリ式の型が <xref:System.Collections.Generic.IEnumerable%601> の `Customer` になります。</span><span class="sxs-lookup"><span data-stu-id="b8b94-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="b8b94-111">この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:顧客と注文 (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md)」。</span><span class="sxs-lookup"><span data-stu-id="b8b94-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Public Class Customer  
    Private customerIDValue As String  
    Public Property CustomerID() As String  
        Get  
            Return customerIDValue  
        End Get  
        Set(ByVal value As String)  
            customerIDValue = value  
        End Set  
    End Property  
  
    Private companyNameValue As String  
    Public Property CompanyName() As String  
        Get  
            Return companyNameValue  
        End Get  
        Set(ByVal value As String)  
            companyNameValue = value  
        End Set  
    End Property  
  
    Private contactNameValue As String  
    Public Property ContactName() As String  
        Get  
            Return contactNameValue  
        End Get  
        Set(ByVal value As String)  
            contactNameValue = value  
        End Set  
    End Property  
  
    Public Sub New(ByVal customerID As String, _  
                   ByVal companyName As String, _  
                   ByVal contactName As String)  
        CustomerIDValue = customerID  
        CompanyNameValue = companyName  
        ContactNameValue = contactName  
    End Sub  
  
    Public Overrides Function ToString() As String  
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)  
    End Function  
End Class  
  
Sub Main()  
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
    Dim custList As IEnumerable(Of Customer) = _  
        From el In custOrd.<Customers>.<Customer> _  
        Select New Customer( _  
            el.@<CustomerID>, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value _  
        )  
    For Each cust In custList  
        Console.WriteLine(cust)  
    Next  
End Sub  
```  
  
 <span data-ttu-id="b8b94-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b8b94-112">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8b94-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8b94-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="b8b94-114">プロジェクションと変換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8b94-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
