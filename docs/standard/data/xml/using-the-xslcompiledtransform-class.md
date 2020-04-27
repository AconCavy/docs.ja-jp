---
title: XslCompiledTransform クラスの使用
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 6fc29b523e59590138cb7ca4db1b0da1bfee99c8
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937941"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="96a6f-102">XslCompiledTransform クラスの使用</span><span class="sxs-lookup"><span data-stu-id="96a6f-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="96a6f-103"><xref:System.Xml.Xsl.XslCompiledTransform> クラスは Microsoft .NET Framework XSLT プロセッサです。</span><span class="sxs-lookup"><span data-stu-id="96a6f-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="96a6f-104">このクラスは、スタイル シートをコンパイルし、XSLT 変換を実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="96a6f-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96a6f-105">全体的なパフォーマンスは <xref:System.Xml.Xsl.XslCompiledTransform> クラスの方が <xref:System.Xml.Xsl.XslTransform> クラスより優れていますが、<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> クラスの <xref:System.Xml.Xsl.XslCompiledTransform> メソッドが変換で初めて呼び出されたときは、<xref:System.Xml.Xsl.XslTransform.Load%2A> クラスの <xref:System.Xml.Xsl.XslTransform> メソッドよりパフォーマンスが劣る場合があります。</span><span class="sxs-lookup"><span data-stu-id="96a6f-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="96a6f-106">これは、XSLT ファイルを読み込む前にコンパイルする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="96a6f-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="96a6f-107">詳細については、ブログ記事「[XslCompiledTransform Slower than XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)」(XslCompiledTransform は XslTransform よりも遅いか?) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96a6f-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96a6f-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="96a6f-108">In This Section</span></span>  
 [<span data-ttu-id="96a6f-109">XslCompiledTransform クラスへの入力</span><span class="sxs-lookup"><span data-stu-id="96a6f-109">Inputs to the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="96a6f-110">使用可能な XSLT 入力オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="96a6f-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="96a6f-111">XslCompiledTransform クラスの出力オプション</span><span class="sxs-lookup"><span data-stu-id="96a6f-111">Output Options on the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="96a6f-112">使用可能な XSLT 出力オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="96a6f-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="96a6f-113">XSLT 処理中の外部リソースの解決</span><span class="sxs-lookup"><span data-stu-id="96a6f-113">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="96a6f-114">外部リソースを解決するための <xref:System.Xml.XmlResolver> クラスの使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="96a6f-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="96a6f-115">XSLT スタイル シートの拡張</span><span class="sxs-lookup"><span data-stu-id="96a6f-115">Extending XSLT Style Sheets</span></span>](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 <span data-ttu-id="96a6f-116">XSLT の拡張機能のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="96a6f-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="96a6f-117">XSLT エラーの解決</span><span class="sxs-lookup"><span data-stu-id="96a6f-117">Recoverable XSLT Errors</span></span>](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|<span data-ttu-id="96a6f-118">W3C (World Wide Web Consortium) 勧告『XSLT 1.0』で許可されている随意動作を示し、<xref:System.Xml.Xsl.XslCompiledTransform> クラスによるこれらの動作の処理方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="96a6f-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="96a6f-119">方法: ノード フラグメントを変換する</span><span class="sxs-lookup"><span data-stu-id="96a6f-119">How to: Transform a Node Fragment</span></span>](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|<span data-ttu-id="96a6f-120">ノード フラグメントの変換方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="96a6f-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="96a6f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="96a6f-121">Related Sections</span></span>  
 [<span data-ttu-id="96a6f-122">XslTransform クラスからの移行</span><span class="sxs-lookup"><span data-stu-id="96a6f-122">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="96a6f-123"><xref:System.Xml.Xsl.XslTransform> クラスからコードを移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="96a6f-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96a6f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="96a6f-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
