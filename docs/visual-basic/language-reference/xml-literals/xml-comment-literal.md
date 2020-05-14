---
title: XML コメント リテラル
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 8d9db66aabe344bd5c8f9a92ac8618b7bc1abb43
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349396"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="3ac79-102">XML コメント リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ac79-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="3ac79-103"><xref:System.Xml.Linq.XComment> オブジェクトを表すリテラル。</span><span class="sxs-lookup"><span data-stu-id="3ac79-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ac79-104">構文</span><span class="sxs-lookup"><span data-stu-id="3ac79-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="3ac79-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="3ac79-105">Parts</span></span>  
  
|<span data-ttu-id="3ac79-106">用語</span><span class="sxs-lookup"><span data-stu-id="3ac79-106">Term</span></span>|<span data-ttu-id="3ac79-107">定義</span><span class="sxs-lookup"><span data-stu-id="3ac79-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="3ac79-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="3ac79-108">Required.</span></span> <span data-ttu-id="3ac79-109">XML コメントの先頭を表します。</span><span class="sxs-lookup"><span data-stu-id="3ac79-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="3ac79-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="3ac79-110">Required.</span></span> <span data-ttu-id="3ac79-111">XML コメントに表示されるテキスト。</span><span class="sxs-lookup"><span data-stu-id="3ac79-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="3ac79-112">連続する 2 つのハイフン (--) を含めたり、終了タグに隣接するハイフンを末尾に使用したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3ac79-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="3ac79-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="3ac79-113">Required.</span></span> <span data-ttu-id="3ac79-114">XML コメントの末尾を表します。</span><span class="sxs-lookup"><span data-stu-id="3ac79-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="3ac79-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="3ac79-115">Return Value</span></span>  
 <span data-ttu-id="3ac79-116"><xref:System.Xml.Linq.XComment> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3ac79-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ac79-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="3ac79-117">Remarks</span></span>  
 <span data-ttu-id="3ac79-118">XML コメント リテラルにはドキュメントのコンテンツではなく、ドキュメントに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ac79-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="3ac79-119">XML コメント セクションの末尾には "-->" シーケンスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3ac79-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="3ac79-120">これは以下を意味します。</span><span class="sxs-lookup"><span data-stu-id="3ac79-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="3ac79-121">埋め込み式の区切り記号は有効な XML コメント コンテンツであるため、XML コメント リテラルでは埋め込み式を使用できません。</span><span class="sxs-lookup"><span data-stu-id="3ac79-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="3ac79-122">`content` には値 "-->" を含めることができないため、XML コメント セクションを入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3ac79-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="3ac79-123">XML コメント リテラルは、変数に代入するか、XML 要素リテラルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3ac79-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ac79-124">XML リテラルは、行連結文字を使用せずに、複数行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="3ac79-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="3ac79-125">この機能を使用すると、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="3ac79-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="3ac79-126">XML コメント リテラルは、Visual Basic コンパイラによって、<xref:System.Xml.Linq.XComment.%23ctor%2A> コンストラクターへの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="3ac79-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ac79-127">例</span><span class="sxs-lookup"><span data-stu-id="3ac79-127">Example</span></span>  
 <span data-ttu-id="3ac79-128">次の例では、"This is a comment" というテキストを含む XML コメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ac79-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="3ac79-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ac79-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="3ac79-130">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="3ac79-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="3ac79-131">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="3ac79-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="3ac79-132">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="3ac79-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
