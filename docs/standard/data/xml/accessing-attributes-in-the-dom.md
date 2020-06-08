---
title: DOM の属性へのアクセス
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
ms.openlocfilehash: a77780621032e2ce59b9db04a179c7086588219b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291644"
---
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="83721-102">DOM の属性へのアクセス</span><span class="sxs-lookup"><span data-stu-id="83721-102">Accessing Attributes in the DOM</span></span>

<span data-ttu-id="83721-103">属性は要素のプロパティであり、要素の子ではありません。</span><span class="sxs-lookup"><span data-stu-id="83721-103">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="83721-104">この区別は、XML ドキュメント オブジェクト モデル (DOM) の兄弟ノード、親ノード、および子ノードの間の移動に使用するメソッドで重要な意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="83721-104">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="83721-105">たとえば、**PreviousSibling** メソッドと **NextSibling** メソッドは、要素から属性への移動や属性間の移動には使われません。</span><span class="sxs-lookup"><span data-stu-id="83721-105">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="83721-106">属性は要素のプロパティであり、要素によって所有されているため、**OwnerElement** プロパティを持ちますが、**parentNode** プロパティはありません。また、移動には専用のメソッドを使います。</span><span class="sxs-lookup"><span data-stu-id="83721-106">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>

<span data-ttu-id="83721-107">現在のノードが要素のとき、その要素に関連付けられている属性があるかどうかを調べるには、**HasAttribute** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="83721-107">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="83721-108">要素に属性がある場合は、各種のメソッドで属性にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="83721-108">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="83721-109">**XmlElement** の **GetAttribute** メソッドと**GetAttributeNode** メソッドを使用して要素から 1 つの属性を取得するか、すべての属性をコレクションとして取得することができます。</span><span class="sxs-lookup"><span data-stu-id="83721-109">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="83721-110">コレクションに対して反復処理を行う必要がある場合は、コレクションを取得すると便利です。</span><span class="sxs-lookup"><span data-stu-id="83721-110">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="83721-111">要素のすべての属性が必要な場合は、要素の **Attributes** プロパティを使用して、すべての属性をコレクションに取得できます。</span><span class="sxs-lookup"><span data-stu-id="83721-111">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>

## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="83721-112">コレクションへのすべての属性の取得</span><span class="sxs-lookup"><span data-stu-id="83721-112">Retrieving All Attributes into a Collection</span></span>

<span data-ttu-id="83721-113">要素ノードのすべての属性をコレクションに取得するには、**XmlElement.Attributes** プロパティを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="83721-113">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="83721-114">**XmlElement.Attributes** プロパティにより、要素のすべての属性を含む XmlAttributeCollection を取得できます。</span><span class="sxs-lookup"><span data-stu-id="83721-114">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="83721-115">**XmlAttributeCollection** クラスは **XmlNamedNode** マップから継承されます。</span><span class="sxs-lookup"><span data-stu-id="83721-115">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="83721-116">このため、コレクションで使用できるメソッドとプロパティには、**ItemOf** プロパティや **Append** メソッドのような **XmlAttributeCollection** クラスに固有のメソッドやプロパティだけでなく、名前付きノード マップで使用できるメソッドとプロパティも含まれます。</span><span class="sxs-lookup"><span data-stu-id="83721-116">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="83721-117">属性コレクション内の各項目は、**XmlAttribute** ノードを表します。</span><span class="sxs-lookup"><span data-stu-id="83721-117">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="83721-118">要素の属性の数を調べるには、**XmlAttributeCollection** を取得し、**Count** プロパティを使用して、そのコレクションに含まれる **XmlAttribute** ノードの数を調べます。</span><span class="sxs-lookup"><span data-stu-id="83721-118">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>

<span data-ttu-id="83721-119">属性コレクションを取得し、**Count** メソッドをループ インデックスとして使用して、コレクションに対して反復処理を行うコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="83721-119">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="83721-120">このコードは、その後、コレクションから属性を 1 つ取得して、その値を表示します。</span><span class="sxs-lookup"><span data-stu-id="83721-120">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As XmlDocument = New XmlDocument()
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _
               "<title>The Handmaid's Tale</title>" & _
               "<price>14.95</price>" & _
               "</book>")

        ' Move to an element.
        Dim myElement As XmlElement = doc.DocumentElement

        ' Create an attribute collection from the element.
        Dim attrColl As XmlAttributeCollection = myElement.Attributes

        ' Show the collection by iterating over it.
        Console.WriteLine("Display all the attributes in the collection...")
        Dim i As Integer
        For i = 0 To attrColl.Count - 1
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)
            Console.Write("{0}", attrColl.ItemOf(i).Value)
            Console.WriteLine()
        Next

        ' Retrieve a single attribute from the collection; specifically, the
        ' attribute with the name "misc".
        Dim attr As XmlAttribute = attrColl("misc")

        ' Retrieve the value from that attribute.
        Dim miscValue As String = attr.InnerXml

        Console.WriteLine("Display the attribute information.")
        Console.WriteLine(miscValue)

    End Sub
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{

    public static void Main()
    {
        XmlDocument doc = new XmlDocument();
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +
                      "<title>The Handmaid's Tale</title>" +
                      "<price>14.95</price>" +
                      "</book>");

        // Move to an element.
        XmlElement myElement = doc.DocumentElement;

        // Create an attribute collection from the element.
        XmlAttributeCollection attrColl = myElement.Attributes;

        // Show the collection by iterating over it.
        Console.WriteLine("Display all the attributes in the collection...");
        for (int i = 0; i < attrColl.Count; i++)
        {
            Console.Write("{0} = ", attrColl[i].Name);
            Console.Write("{0}", attrColl[i].Value);
            Console.WriteLine();
        }

        // Retrieve a single attribute from the collection; specifically, the
        // attribute with the name "misc".
        XmlAttribute attr = attrColl["misc"];

        // Retrieve the value from that attribute.
        String miscValue = attr.InnerXml;

        Console.WriteLine("Display the attribute information.");
        Console.WriteLine(miscValue);

    }
}
```

<span data-ttu-id="83721-121">この例を実行すると、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83721-121">This example displays the following output:</span></span>

<span data-ttu-id="83721-122">**出力**</span><span class="sxs-lookup"><span data-stu-id="83721-122">**Output**</span></span>

<span data-ttu-id="83721-123">コレクション内のすべての属性を表示します。</span><span class="sxs-lookup"><span data-stu-id="83721-123">Display all the attributes in the collection.</span></span>

```console
genre = novel
ISBN = 1-861001-57-5
misc = sale item
Display the attribute information.
sale item
```

<span data-ttu-id="83721-124">属性コレクションの情報は、名前またはインデックス番号によって取得できます。</span><span class="sxs-lookup"><span data-stu-id="83721-124">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="83721-125">上の例では、名前を指定してデータを取得しています。</span><span class="sxs-lookup"><span data-stu-id="83721-125">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="83721-126">次の例では、インデックス番号を指定してデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="83721-126">The next example shows how to retrieve data by index number.</span></span>

<span data-ttu-id="83721-127">**XmlAttributeCollection** はコレクションであり、名前またはインデックスを使って反復処理ができるため、次の例では、ゼロベースのインデックスを使用してコレクションの最初の属性を選択しています。入力には、**baseuri.xml** というファイルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="83721-127">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>

### <a name="input"></a><span data-ttu-id="83721-128">入力</span><span class="sxs-lookup"><span data-stu-id="83721-128">Input</span></span>

```xml
<!-- XML fragment -->
<book genre="novel">
  <title>Pride And Prejudice</title>
</book>
```

```vb
Option Explicit On
Option Strict On

Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()
        ' Create the XmlDocument.
        Dim doc As New XmlDocument()
        doc.Load("http://localhost/baseuri.xml")

        ' Display information on the attribute node. The value
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)
        Console.WriteLine("The value of the attribute:  {0}", attr.InnerText)
    End Sub 'Main
End Class 'Sample
```

```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{
  public static void Main()
  {
    // Create the XmlDocument.
    XmlDocument doc = new XmlDocument();

    doc.Load("http://localhost/baseuri.xml");

    // Display information on the attribute node. The value
    // returned for BaseURI is 'http://localhost/baseuri.xml'.
    XmlAttribute attr = doc.DocumentElement.Attributes[0];
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);
    Console.WriteLine("The value of the attribute:  {0}", attr.InnerText);
  }
}
```

## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="83721-129">個別の属性ノードの取得</span><span class="sxs-lookup"><span data-stu-id="83721-129">Retrieving an Individual Attribute Node</span></span>

<span data-ttu-id="83721-130">要素から属性ノードを 1 つ取得するには、<xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="83721-130">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="83721-131">このメソッドは、**XmlAttribute** 型のオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="83721-131">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="83721-132">**XmlAttribute** の取得後は、<xref:System.Xml.XmlAttribute?displayProperty=nameWithType> クラスのすべてのメソッドとプロパティを使用できます。たとえば、**OwnerElement** で、どの要素に所属しているかを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="83721-132">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As XmlDocument = New XmlDocument()
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _
               "<title>The Handmaid's Tale</title>" & _
               "<price>14.95</price>" & _
               "</book>")

        ' Move to an element.
        Dim root As XmlElement
        root = doc.DocumentElement

        ' Get an attribute.
        Dim attr As XmlAttribute
        attr = root.GetAttributeNode("ISBN")

        ' Display the value of the attribute.
        Dim attrValue As String
        attrValue = attr.InnerXml
        Console.WriteLine(attrValue)

    End Sub
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;

 public class Sample
 {
      public static void Main()
      {
    XmlDocument doc = new XmlDocument();
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +
                   "<title>The Handmaid's Tale</title>" +
                   "<price>14.95</price>" +
                   "</book>");

    // Move to an element.
     XmlElement root = doc.DocumentElement;

    // Get an attribute.
     XmlAttribute attr = root.GetAttributeNode("ISBN");

    // Display the value of the attribute.
     String attrValue = attr.InnerXml;
     Console.WriteLine(attrValue);

    }
}
```

<span data-ttu-id="83721-133">前の例で示したように、属性コレクションから 1 つの属性ノードを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="83721-133">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="83721-134">インデックス番号を指定して、XML ドキュメント ツリーのルートから 1 つの属性を取得する処理を 1 行で記述したコード サンプルを次に示します。**DocumentElement** プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="83721-134">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>

```csharp
XmlAttribute attr = doc.DocumentElement.Attributes[0];
```

## <a name="see-also"></a><span data-ttu-id="83721-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="83721-135">See also</span></span>

- [<span data-ttu-id="83721-136">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="83721-136">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
