---
title: 名前空間内の XML に対するクエリを記述する方法 (C#)
description: 名前空間内の XML に対するクエリを記述する方法について説明します。 これらのクエリでは、正しい名前空間を持つ XName オブジェクトを使用する必要があります。
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 64eb9df1cde3b434a11e2e5410aab96993dc0fa1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303180"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="84a94-104">名前空間内の XML に対するクエリを記述する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="84a94-104">How to write queries on XML in namespaces (C#)</span></span>
<span data-ttu-id="84a94-105">名前空間内の XML に対するクエリを記述するには、正しい名前空間を持つ <xref:System.Xml.Linq.XName> オブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84a94-105">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="84a94-106">C# での最も一般的な方法は、URI を含んだ文字列を使用して <xref:System.Xml.Linq.XNamespace> を初期化し、加算演算子オーバーロードを使用して名前空間をローカル名に連結することです。</span><span class="sxs-lookup"><span data-stu-id="84a94-106">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="84a94-107">このトピックの最初に示す一連の例では、既定の名前空間内に XML ツリーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="84a94-107">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="84a94-108">2 つ目の例では、プレフィックスを持つ名前空間で XML ツリーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="84a94-108">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a94-109">例</span><span class="sxs-lookup"><span data-stu-id="84a94-109">Example</span></span>  
 <span data-ttu-id="84a94-110">次の例では、既定の名前空間に含まれる XML ツリーを作成しています。</span><span class="sxs-lookup"><span data-stu-id="84a94-110">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="84a94-111">さらに、要素のコレクションを取得しています。</span><span class="sxs-lookup"><span data-stu-id="84a94-111">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="84a94-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="84a94-112">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="84a94-113">例</span><span class="sxs-lookup"><span data-stu-id="84a94-113">Example</span></span>  
 <span data-ttu-id="84a94-114">C# では、プレフィックスを持つ名前空間を使用する XML ツリーでも、既定の名前空間を持つ XML ツリーでも、クエリを記述する方法は同じです。</span><span class="sxs-lookup"><span data-stu-id="84a94-114">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="84a94-115">次の例では、プレフィックスを持つ名前空間に含まれる XML ツリーを作成しています。</span><span class="sxs-lookup"><span data-stu-id="84a94-115">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="84a94-116">さらに、要素のコレクションを取得しています。</span><span class="sxs-lookup"><span data-stu-id="84a94-116">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="84a94-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="84a94-117">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="84a94-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="84a94-118">See also</span></span>

- [<span data-ttu-id="84a94-119">名前空間の概要 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="84a94-119">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
