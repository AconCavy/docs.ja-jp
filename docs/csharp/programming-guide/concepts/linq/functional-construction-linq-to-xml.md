---
title: 関数型構築 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635757"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="b032d-102">関数型構築 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b032d-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="b032d-103">には、"*関数型構築*" と呼ばれる強力な XML 要素作成機能があります。</span><span class="sxs-lookup"><span data-stu-id="b032d-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="b032d-104">関数型構築は、単一のステートメントで XML ツリーを作成するための機能です。</span><span class="sxs-lookup"><span data-stu-id="b032d-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="b032d-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] プログラミング インターフェイスには、関数型構築を利用するためのいくつかの重要な機能があります。</span><span class="sxs-lookup"><span data-stu-id="b032d-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="b032d-106"><xref:System.Xml.Linq.XElement> コンストラクターは、さまざまな種類のコンテンツ引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b032d-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="b032d-107">たとえば、このコンストラクターに、子要素になる別の <xref:System.Xml.Linq.XElement> オブジェクトや、</span><span class="sxs-lookup"><span data-stu-id="b032d-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="b032d-108">要素の属性になる <xref:System.Xml.Linq.XAttribute> オブジェクトを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b032d-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="b032d-109">また、文字列に変換され、要素のテキスト コンテンツになる他の任意の種類のオブジェクトを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="b032d-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="b032d-110"><xref:System.Xml.Linq.XElement> コンストラクターは、`params` 型の <xref:System.Object> 配列を受け取ります。そのため、任意の数のオブジェクトを配列に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b032d-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="b032d-111">これにより、複雑なコンテンツを持つ要素を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b032d-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="b032d-112">オブジェクトが <xref:System.Collections.Generic.IEnumerable%601> を実装している場合、オブジェクト内のコレクションが列挙され、コレクション内のすべての項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b032d-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="b032d-113">コレクションに <xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XAttribute> オブジェクトが含まれている場合、コレクション内の各項目が個別に追加されます。</span><span class="sxs-lookup"><span data-stu-id="b032d-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="b032d-114">これは重要な機能といえます。その理由は、この機能により、LINQ クエリの結果をコンストラクターに渡すことができるためです。</span><span class="sxs-lookup"><span data-stu-id="b032d-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="b032d-115">これらの機能により、XML ツリーを作成するコードを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="b032d-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="b032d-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b032d-116">The following is an example:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="b032d-117">また、これらの機能により、XML ツリーを作成するときに、LINQ クエリの結果を使用するコードを記述することができます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b032d-117">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="b032d-118">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b032d-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  