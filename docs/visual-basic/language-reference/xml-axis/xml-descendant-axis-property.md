---
title: XML Descendant Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400254"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="3da19-102">XML 子孫軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3da19-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="3da19-103"><xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションの子孫にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="3da19-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="3da19-104">構文</span><span class="sxs-lookup"><span data-stu-id="3da19-104">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="3da19-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="3da19-105">Parts</span></span>

<span data-ttu-id="3da19-106">`object` 必須。</span><span class="sxs-lookup"><span data-stu-id="3da19-106">`object` Required.</span></span> <span data-ttu-id="3da19-107"><xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="3da19-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="3da19-108">`...<` 必須。</span><span class="sxs-lookup"><span data-stu-id="3da19-108">`...<` Required.</span></span> <span data-ttu-id="3da19-109">子孫軸プロパティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="3da19-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="3da19-110">`descendant` 必須。</span><span class="sxs-lookup"><span data-stu-id="3da19-110">`descendant` Required.</span></span> <span data-ttu-id="3da19-111">アクセスする子孫ノードの名前です。[`prefix:]name` の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="3da19-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="3da19-112">パーツ</span><span class="sxs-lookup"><span data-stu-id="3da19-112">Part</span></span>|<span data-ttu-id="3da19-113">説明</span><span class="sxs-lookup"><span data-stu-id="3da19-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="3da19-114">任意。</span><span class="sxs-lookup"><span data-stu-id="3da19-114">Optional.</span></span> <span data-ttu-id="3da19-115">子孫ノードの XML 名前空間プレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="3da19-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="3da19-116">`Imports` ステートメントを使用して定義されているグローバル XML 名前空間にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da19-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="3da19-117">必須です。</span><span class="sxs-lookup"><span data-stu-id="3da19-117">Required.</span></span> <span data-ttu-id="3da19-118">子孫ノードのローカル名。</span><span class="sxs-lookup"><span data-stu-id="3da19-118">Local name of the descendant node.</span></span> <span data-ttu-id="3da19-119">「[宣言する XML 要素と属性の名前](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3da19-119">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="3da19-120">`>` 必須。</span><span class="sxs-lookup"><span data-stu-id="3da19-120">`>` Required.</span></span> <span data-ttu-id="3da19-121">子孫軸プロパティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="3da19-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="3da19-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="3da19-122">Return Value</span></span>

<span data-ttu-id="3da19-123"><xref:System.Xml.Linq.XElement> オブジェクトのコレクション。</span><span class="sxs-lookup"><span data-stu-id="3da19-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="3da19-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="3da19-124">Remarks</span></span>

<span data-ttu-id="3da19-125">XML 子孫軸プロパティを使用すると、<xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションから子孫ノードに名前でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3da19-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="3da19-126">返されるコレクションの最初の子孫ノードの値にアクセスするには、XML の `Value` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="3da19-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="3da19-127">詳細については、「[XML Value プロパティ](xml-value-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3da19-127">For more information, see [XML Value Property](xml-value-property.md).</span></span>

<span data-ttu-id="3da19-128">Visual Basic コンパイラによって、子孫軸プロパティが <xref:System.Xml.Linq.XContainer.Descendants%2A> メソッドの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="3da19-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="3da19-129">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="3da19-129">XML Namespaces</span></span>

<span data-ttu-id="3da19-130">子孫軸プロパティの名前では、`Imports` ステートメントでグローバルに宣言されている XML 名前空間のみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3da19-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="3da19-131">XML 要素リテラル内でローカルに宣言されている XML 名前空間は使用できません。</span><span class="sxs-lookup"><span data-stu-id="3da19-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="3da19-132">詳細については、「[Imports ステートメント (XML 名前空間)](../statements/imports-statement-xml-namespace.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3da19-132">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="3da19-133">例</span><span class="sxs-lookup"><span data-stu-id="3da19-133">Example</span></span>

<span data-ttu-id="3da19-134">次の例は、`contacts` オブジェクトから、`name` という名前の最初の子孫ノードの値と、`phone` という名前のすべての子孫ノードの値にアクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3da19-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="3da19-135">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3da19-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="3da19-136">例</span><span class="sxs-lookup"><span data-stu-id="3da19-136">Example</span></span>

<span data-ttu-id="3da19-137">次の例では、`ns` を名前空間プレフィックスとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="3da19-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="3da19-138">その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードの値にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3da19-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="3da19-139">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3da19-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="3da19-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="3da19-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="3da19-141">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="3da19-141">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="3da19-142">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="3da19-142">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="3da19-143">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="3da19-143">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="3da19-144">宣言する XML 要素と属性の名前</span><span class="sxs-lookup"><span data-stu-id="3da19-144">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
