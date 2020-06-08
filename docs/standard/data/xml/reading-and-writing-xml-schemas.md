---
title: XML スキーマの読み取りと書き込み
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: bf1078d52f5e9056da6b28acc8dd2fc257eb3636
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291254"
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="729a9-102">XML スキーマの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="729a9-102">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="729a9-103">スキーマ オブジェクト モデル (SOM) API を使用すると、ファイルまたは他のソースから XML スキーマ定義言語 (XSD) スキーマを読み取ったり、書き込んだりできます。また、W3C (World Wide Web Consortium) 勧告『XML Schema』で定義された構造に割り当てられた <xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間のクラスを使用してメモリ内に XML スキーマを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="729a9-103">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="729a9-104">XML スキーマの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="729a9-104">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="729a9-105"><xref:System.Xml.Schema.XmlSchema> クラスでは、<xref:System.Xml.Schema.XmlSchema.Read%2A> メソッドおよび <xref:System.Xml.Schema.XmlSchema.Write%2A> メソッドを利用して XML スキーマの読み取りと書き込みを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="729a9-105">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="729a9-106"><xref:System.Xml.Schema.XmlSchema.Read%2A> メソッドは XML スキーマを表す <xref:System.Xml.Schema.XmlSchema> オブジェクトを返し、オプションの <xref:System.Xml.Schema.ValidationEventHandler> をパラメーターとして受け取って XML スキーマの読み取り時に発生するスキーマ検証に関する警告とエラーを処理します。</span><span class="sxs-lookup"><span data-stu-id="729a9-106">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="729a9-107"><xref:System.Xml.Schema.XmlSchema.Write%2A> メソッドは <xref:System.IO.Stream>、<xref:System.IO.TextWriter> および <xref:System.Xml.XmlWriter> オブジェクトに XML スキーマを書き込んで、オプションで <xref:System.Xml.XmlNamespaceManager> オブジェクトをパラメーターとして受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="729a9-107">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="729a9-108"><xref:System.Xml.XmlNamespaceManager> は、XML スキーマ内で検出される名前空間の処理に使用されます。</span><span class="sxs-lookup"><span data-stu-id="729a9-108">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="729a9-109"><xref:System.Xml.XmlNamespaceManager> クラスの詳細については、「[XML ドキュメントでの名前空間の管理](managing-namespaces-in-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="729a9-109">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="729a9-110">次のコード サンプルでは、XML スキーマのファイルからの読み込みとファイルへの書き込みを説明します。</span><span class="sxs-lookup"><span data-stu-id="729a9-110">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="729a9-111">このコード サンプルは、`example.xsd`<xref:System.Xml.Schema.XmlSchema> メソッドを使用して `static` オブジェクトに <xref:System.Xml.Schema.XmlSchema.Read%2A> ファイルを読み込み、その後、このファイルをコンソールに出力して新しい `new.xsd` ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="729a9-111">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="729a9-112">また、このコード サンプルでは、<xref:System.Xml.Schema.ValidationEventHandler>`static` メソッドに <xref:System.Xml.Schema.XmlSchema.Read%2A> をパラメーターとして指定して、XML スキーマを読み込む際に検出されるスキーマ検証時の警告やエラーの処理を行います。</span><span class="sxs-lookup"><span data-stu-id="729a9-112">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="729a9-113"><xref:System.Xml.Schema.ValidationEventHandler> を指定しないと (`null`)、警告やエラーは報告されません。</span><span class="sxs-lookup"><span data-stu-id="729a9-113">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="729a9-114">この例は、入力として `example.xsd` を使用します。</span><span class="sxs-lookup"><span data-stu-id="729a9-114">The example takes the `example.xsd` as input.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="729a9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="729a9-115">See also</span></span>

- [<span data-ttu-id="729a9-116">XML スキーマ オブジェクト モデルの概要</span><span class="sxs-lookup"><span data-stu-id="729a9-116">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="729a9-117">XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="729a9-117">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="729a9-118">XML スキーマの走査</span><span class="sxs-lookup"><span data-stu-id="729a9-118">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="729a9-119">XML スキーマの編集</span><span class="sxs-lookup"><span data-stu-id="729a9-119">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="729a9-120">XML スキーマのインクルードまたはインポート</span><span class="sxs-lookup"><span data-stu-id="729a9-120">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="729a9-121">スキーマをコンパイルするための XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="729a9-121">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="729a9-122">スキーマのコンパイル後の情報セット</span><span class="sxs-lookup"><span data-stu-id="729a9-122">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
- [<span data-ttu-id="729a9-123">XML ドキュメントでの名前空間の管理</span><span class="sxs-lookup"><span data-stu-id="729a9-123">Managing Namespaces in an XML Document</span></span>](managing-namespaces-in-an-xml-document.md)
