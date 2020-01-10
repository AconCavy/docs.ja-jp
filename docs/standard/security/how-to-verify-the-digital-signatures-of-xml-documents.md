---
title: '方法: XML ドキュメントのデジタル署名を検証する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: 5d562c23d3b0fd7eda5dc273932ada77709641a1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706007"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="9615f-102">方法: XML ドキュメントのデジタル署名を検証する</span><span class="sxs-lookup"><span data-stu-id="9615f-102">How to: Verify the Digital Signatures of XML Documents</span></span>
<span data-ttu-id="9615f-103"><xref:System.Security.Cryptography.Xml> 名前空間にあるクラスを使用すると、デジタル署名で署名された XML データを検証できます。</span><span class="sxs-lookup"><span data-stu-id="9615f-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span> <span data-ttu-id="9615f-104">XML デジタル署名 (XMLDSIG) を使用すると、データが署名後に変更されなかったことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="9615f-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span> <span data-ttu-id="9615f-105">XMLDSIG 標準の詳細についてにある World Wide Web Consortium (W3C) 仕様を参照して <https://www.w3.org/TR/xmldsig-core/> です。</span><span class="sxs-lookup"><span data-stu-id="9615f-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at <https://www.w3.org/TR/xmldsig-core/>.</span></span>
  
 <span data-ttu-id="9615f-106">この手順のコード例では、<`Signature`> 要素に含まれている XML デジタル署名を検証する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9615f-106">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="9615f-107">この例では、キー コンテナーから RSA 公開キーを取得してから、キーを使用して署名を確認します。</span><span class="sxs-lookup"><span data-stu-id="9615f-107">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
 <span data-ttu-id="9615f-108">この手法を使用して検証できるデジタル署名を作成する方法については、「[方法: デジタル署名で XML ドキュメントに署名](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9615f-108">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="9615f-109">XML ドキュメントのデジタル署名を検証するには</span><span class="sxs-lookup"><span data-stu-id="9615f-109">To verify the digital signature of an XML document</span></span>  
  
1. <span data-ttu-id="9615f-110">ドキュメントを検証するには、署名に使用した非対称キーと同じ非対称キーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9615f-110">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="9615f-111"><xref:System.Security.Cryptography.CspParameters> オブジェクトを作成し、署名に使用したキー コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9615f-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="9615f-112"><xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスを使用して公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="9615f-112">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="9615f-113"><xref:System.Security.Cryptography.CspParameters> オブジェクトを <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスのコンストラクターに渡すと、キー コンテナーからキーが名前順で自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="9615f-113">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="9615f-114">ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9615f-114">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="9615f-115"><xref:System.Xml.XmlDocument> オブジェクトには、確認対象の署名済みの XML ドキュメントが含まています。</span><span class="sxs-lookup"><span data-stu-id="9615f-115">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="9615f-116"><xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトを新規作成し、それに <xref:System.Xml.XmlDocument> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="9615f-116">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="9615f-117">`signature`> 要素を検索し、新しい <xref:System.Xml.XmlNodeList> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9615f-117">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="9615f-118">最初の <`signature`> 要素の XML を <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="9615f-118">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="9615f-119"><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> メソッドと RSA の公開キーを使用して署名を確認します。</span><span class="sxs-lookup"><span data-stu-id="9615f-119">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="9615f-120">このメソッドは、成功または失敗を示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="9615f-120">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="9615f-121">使用例</span><span class="sxs-lookup"><span data-stu-id="9615f-121">Example</span></span>  
 <span data-ttu-id="9615f-122">この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="9615f-122">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="9615f-123">「[方法: デジタル署名で XML ドキュメントに署名](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)する」で説明されている方法を使用して、`"test.xml"` ファイルに署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9615f-123">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9615f-124">コードのコンパイル方法</span><span class="sxs-lookup"><span data-stu-id="9615f-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="9615f-125">この例をコンパイルするには、`System.Security.dll` への参照を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9615f-125">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="9615f-126">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="9615f-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9615f-127">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9615f-127">.NET Framework Security</span></span>  
 <span data-ttu-id="9615f-128">非対称キー ペアの秘密キーをプレーンテキストで保存または転送しないでください。</span><span class="sxs-lookup"><span data-stu-id="9615f-128">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="9615f-129">対称暗号化キーと非対称暗号化キーの詳細については、[暗号化と復号化キーを生成する](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9615f-129">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="9615f-130">秘密キーをソース コードに直接埋め込まないでください。</span><span class="sxs-lookup"><span data-stu-id="9615f-130">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="9615f-131">埋め込まれたキーは、アセンブリを[Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)またはメモ帳などのテキスト エディターで開くことで、簡単に読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="9615f-131">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9615f-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="9615f-132">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="9615f-133">方法: デジタル署名で XML ドキュメントに署名する</span><span class="sxs-lookup"><span data-stu-id="9615f-133">How to: Sign XML Documents with Digital Signatures</span></span>](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
