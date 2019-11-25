---
title: LINQ to Objects
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: ef7d6fe232a788ab77661e9c5f313a80df4779b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354311"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="94fda-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94fda-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="94fda-103">"LINQ to Objects" という用語は、[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) や [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) などの中間 LINQ プロバイダーまたは API を使用せずに、LINQ クエリを任意の <xref:System.Collections.IEnumerable> コレクションまたは <xref:System.Collections.Generic.IEnumerable%601> コレクションと直接組み合わせて使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="94fda-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="94fda-104">LINQ を使用して、<xref:System.Collections.Generic.List%601>、<xref:System.Array>、<xref:System.Collections.Generic.Dictionary%602> などの任意の列挙可能なコレクションを照会できます。</span><span class="sxs-lookup"><span data-stu-id="94fda-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="94fda-105">このコレクションは、ユーザー定義のコレクションでも、.NET Framework API から返されたコレクションでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="94fda-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="94fda-106">本質的に、LINQ to Objects は、コレクションを扱うための新しい方法です。</span><span class="sxs-lookup"><span data-stu-id="94fda-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="94fda-107">従来の方法では、複雑な `For Each` ループを記述して、コレクションからデータを取得する方法を指定する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="94fda-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="94fda-108">LINQ を使用する場合は、何を取得するかを表す宣言コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="94fda-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="94fda-109">また、LINQ クエリには、従来の `For Each` ループと比べて、次の 3 つの重要な利点があります。</span><span class="sxs-lookup"><span data-stu-id="94fda-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="94fda-110">簡潔で読みやすい (特に複数の条件をフィルター処理する場合)。</span><span class="sxs-lookup"><span data-stu-id="94fda-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="94fda-111">強力なフィルター処理、並べ替え、およびグループ化機能を最小限のアプリケーション コードで実現できる。</span><span class="sxs-lookup"><span data-stu-id="94fda-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="94fda-112">ほとんど、またはまったく変更せずに、他のデータ ソースに移植できる。</span><span class="sxs-lookup"><span data-stu-id="94fda-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="94fda-113">通常、データに対して実行する操作が複雑なほど、従来の反復処理手法の代わりに LINQ を使用する利便性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="94fda-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="94fda-114">このセクションでは、いくつか例を挙げながら、LINQ を使った方法を具体的に説明します。</span><span class="sxs-lookup"><span data-stu-id="94fda-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="94fda-115">ただし、すべてを網羅したものではありません。</span><span class="sxs-lookup"><span data-stu-id="94fda-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94fda-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="94fda-116">In This Section</span></span>  
 [<span data-ttu-id="94fda-117">LINQ and Strings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94fda-117">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="94fda-118">LINQ を使用して、文字列および文字列のコレクションの照会と変換を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="94fda-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="94fda-119">これらの基本原則を具体的に示すトピックへのリンクも含まれます。</span><span class="sxs-lookup"><span data-stu-id="94fda-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="94fda-120">LINQ and Reflection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94fda-120">LINQ and Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="94fda-121">LINQ でリフレクションを使用する方法を示すサンプルへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="94fda-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="94fda-122">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94fda-122">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="94fda-123">LINQ を使用して、ファイル システムとやり取りする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="94fda-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="94fda-124">これらの概念を具体的に示すトピックへのリンクも含まれます。</span><span class="sxs-lookup"><span data-stu-id="94fda-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="94fda-125">How to: Query an ArrayList with LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94fda-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="94fda-126">C# で ArrayList を照会する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="94fda-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="94fda-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94fda-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="94fda-128"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスに拡張メソッドを追加して、LINQ クエリに使用できるメソッド セットを拡張する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="94fda-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="94fda-129">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94fda-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="94fda-130">LINQ について説明しているトピックへのリンクと、クエリを実行するコードの例を示します。</span><span class="sxs-lookup"><span data-stu-id="94fda-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
