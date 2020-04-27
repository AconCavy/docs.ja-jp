---
title: '方法: XslTransform コードを移行する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: 2bc5cbc1b0857a82d3b0a11f05a4eb5756724546
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710844"
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="10a9a-102">方法: XslTransform コードを移行する</span><span class="sxs-lookup"><span data-stu-id="10a9a-102">How to: Migrate Your XslTransform Code</span></span>
<span data-ttu-id="10a9a-103">新しい XSLT クラスは、従来のクラスに非常に近いものとなるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="10a9a-103">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="10a9a-104"><xref:System.Xml.Xsl.XslCompiledTransform> クラスは <xref:System.Xml.Xsl.XslTransform> クラスを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="10a9a-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="10a9a-105">スタイル シートは <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> メソッドを使用してコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="10a9a-105">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="10a9a-106">変換は <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドを使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="10a9a-106">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="10a9a-107">次の手順では、一般的な XSLT タスクを挙げ、<xref:System.Xml.Xsl.XslTransform> クラスと <xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用したコードを比較します。</span><span class="sxs-lookup"><span data-stu-id="10a9a-107">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="10a9a-108">ファイルを変換して URI に出力するには</span><span class="sxs-lookup"><span data-stu-id="10a9a-108">To transform a file and output to a URI</span></span>  
  
- <span data-ttu-id="10a9a-109"><xref:System.Xml.Xsl.XslTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-109">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- <span data-ttu-id="10a9a-110"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-110">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="10a9a-111">スタイル シートをコンパイルして、既定の資格情報でリゾルバーを使用するには</span><span class="sxs-lookup"><span data-stu-id="10a9a-111">To compile a style sheet and use a resolver with default credentials</span></span>  
  
- <span data-ttu-id="10a9a-112"><xref:System.Xml.Xsl.XslTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-112">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- <span data-ttu-id="10a9a-113"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-113">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="10a9a-114">XSLT パラメーターを使用するために必要な処理</span><span class="sxs-lookup"><span data-stu-id="10a9a-114">To use an XSLT parameter</span></span>  
  
- <span data-ttu-id="10a9a-115"><xref:System.Xml.Xsl.XslTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-115">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- <span data-ttu-id="10a9a-116"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-116">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="10a9a-117">XSLT スクリプトを有効にするには</span><span class="sxs-lookup"><span data-stu-id="10a9a-117">To enable XSLT scripting</span></span>  
  
- <span data-ttu-id="10a9a-118"><xref:System.Xml.Xsl.XslTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-118">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- <span data-ttu-id="10a9a-119"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-119">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="10a9a-120">結果を DOM オブジェクトに読み込むには</span><span class="sxs-lookup"><span data-stu-id="10a9a-120">To load the results into a DOM object</span></span>  
  
- <span data-ttu-id="10a9a-121"><xref:System.Xml.Xsl.XslTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-121">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- <span data-ttu-id="10a9a-122"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-122">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="10a9a-123"><xref:System.Xml.Xsl.XslCompiledTransform> クラスには、XSLT 変換結果を <xref:System.Xml.XmlReader> オブジェクトとして返すメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="10a9a-123">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="10a9a-124">しかし、XML ファイルに出力して、その XML ファイルを別のオブジェクトに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="10a9a-124">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="10a9a-125">結果を別のデータ ストアにストリーム出力するには</span><span class="sxs-lookup"><span data-stu-id="10a9a-125">To stream the results into another data store</span></span>  
  
- <span data-ttu-id="10a9a-126"><xref:System.Xml.Xsl.XslTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-126">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- <span data-ttu-id="10a9a-127"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用したコード。</span><span class="sxs-lookup"><span data-stu-id="10a9a-127">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="10a9a-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="10a9a-128">See also</span></span>

- [<span data-ttu-id="10a9a-129">XslTransform クラスからの移行</span><span class="sxs-lookup"><span data-stu-id="10a9a-129">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [<span data-ttu-id="10a9a-130">XslCompiledTransform クラスの使用</span><span class="sxs-lookup"><span data-stu-id="10a9a-130">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
