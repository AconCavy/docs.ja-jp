---
title: '方法: XML ドキュメントのデジタル署名を検証する'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSA class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: b9b2dc6a558d1fd6acd2922a7c8ad82ce8776c26
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557048"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="69c7e-102">方法: XML ドキュメントのデジタル署名を検証する</span><span class="sxs-lookup"><span data-stu-id="69c7e-102">How to: Verify the Digital Signatures of XML Documents</span></span>

<span data-ttu-id="69c7e-103"><xref:System.Security.Cryptography.Xml> 名前空間にあるクラスを使用すると、デジタル署名で署名された XML データを検証できます。</span><span class="sxs-lookup"><span data-stu-id="69c7e-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span> <span data-ttu-id="69c7e-104">XML デジタル署名 (XMLDSIG) を使用すると、データが署名後に変更されなかったことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="69c7e-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span> <span data-ttu-id="69c7e-105">XMLDSIG 標準の詳細については、「」の World Wide Web コンソーシアム (W3C) の仕様を参照してください <https://www.w3.org/TR/xmldsig-core/> 。</span><span class="sxs-lookup"><span data-stu-id="69c7e-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at <https://www.w3.org/TR/xmldsig-core/>.</span></span>
  
> [!NOTE]
> <span data-ttu-id="69c7e-106">この記事のコードは、Windows に適用されます。</span><span class="sxs-lookup"><span data-stu-id="69c7e-106">The code in this article applies to Windows.</span></span>

<span data-ttu-id="69c7e-107">この手順のコード例では、<> 要素に含まれている XML デジタル署名を検証する方法を示し `Signature` ます。</span><span class="sxs-lookup"><span data-stu-id="69c7e-107">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="69c7e-108">この例では、キー コンテナーから RSA 公開キーを取得してから、キーを使用して署名を確認します。</span><span class="sxs-lookup"><span data-stu-id="69c7e-108">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
<span data-ttu-id="69c7e-109">この手法を使用して検証できるデジタル署名を作成する方法については、「[方法: デジタル署名で XML ドキュメントに署名](how-to-sign-xml-documents-with-digital-signatures.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69c7e-109">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="69c7e-110">XML ドキュメントのデジタル署名を検証するには</span><span class="sxs-lookup"><span data-stu-id="69c7e-110">To verify the digital signature of an XML document</span></span>  
  
1. <span data-ttu-id="69c7e-111">ドキュメントを検証するには、署名に使用した非対称キーと同じ非対称キーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69c7e-111">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="69c7e-112"><xref:System.Security.Cryptography.CspParameters> オブジェクトを作成し、署名に使用したキー コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="69c7e-112">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="69c7e-113"><xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスを使用して公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="69c7e-113">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="69c7e-114"><xref:System.Security.Cryptography.CspParameters> オブジェクトを <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスのコンストラクターに渡すと、キー コンテナーからキーが名前順で自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="69c7e-114">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="69c7e-115">ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="69c7e-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="69c7e-116"><xref:System.Xml.XmlDocument> オブジェクトには、確認対象の署名済みの XML ドキュメントが含まています。</span><span class="sxs-lookup"><span data-stu-id="69c7e-116">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="69c7e-117"><xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトを新規作成し、それに <xref:System.Xml.XmlDocument> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="69c7e-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="69c7e-118"><`signature`> 要素を検索し、新しいオブジェクトを作成し <xref:System.Xml.XmlNodeList> ます。</span><span class="sxs-lookup"><span data-stu-id="69c7e-118">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="69c7e-119">最初の <> 要素の XML を `signature` オブジェクトに読み込み <xref:System.Security.Cryptography.Xml.SignedXml> ます。</span><span class="sxs-lookup"><span data-stu-id="69c7e-119">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="69c7e-120"><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> メソッドと RSA の公開キーを使用して署名を確認します。</span><span class="sxs-lookup"><span data-stu-id="69c7e-120">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="69c7e-121">このメソッドは、成功または失敗を示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="69c7e-121">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="69c7e-122">例</span><span class="sxs-lookup"><span data-stu-id="69c7e-122">Example</span></span>

<span data-ttu-id="69c7e-123">この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="69c7e-123">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="69c7e-124">`"test.xml"`「[方法: デジタル署名で XML ドキュメントに署名](how-to-sign-xml-documents-with-digital-signatures.md)する」で説明されている方法を使用して、ファイルに署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69c7e-124">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
[!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
[!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="69c7e-125">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="69c7e-125">Compiling the Code</span></span>  
  
- <span data-ttu-id="69c7e-126">.NET Framework を対象とするプロジェクトでは、への参照を含め `System.Security.dll` ます。</span><span class="sxs-lookup"><span data-stu-id="69c7e-126">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="69c7e-127">.NET Core または .NET 5 を対象とするプロジェクトでは、NuGet パッケージ[System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="69c7e-127">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="69c7e-128">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="69c7e-128">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="69c7e-129">.NET セキュリティ</span><span class="sxs-lookup"><span data-stu-id="69c7e-129">.NET Security</span></span>

<span data-ttu-id="69c7e-130">非対称キー ペアの秘密キーをプレーンテキストで保存または転送しないでください。</span><span class="sxs-lookup"><span data-stu-id="69c7e-130">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="69c7e-131">対称暗号化キーと非対称暗号化キーの詳細については、「[暗号化と復号化のためのキーの生成](generating-keys-for-encryption-and-decryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69c7e-131">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="69c7e-132">秘密キーをソース コードに直接埋め込まないでください。</span><span class="sxs-lookup"><span data-stu-id="69c7e-132">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="69c7e-133">埋め込みキーは、 [Ildasm.exe (IL 逆アセンブラー)](../../framework/tools/ildasm-exe-il-disassembler.md)を使用するか、メモ帳などのテキストエディターでアセンブリを開くことで、アセンブリから簡単に読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="69c7e-133">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c7e-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="69c7e-134">See also</span></span>

- [<span data-ttu-id="69c7e-135">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="69c7e-135">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="69c7e-136">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="69c7e-136">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="69c7e-137">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="69c7e-137">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="69c7e-138">方法: デジタル署名で XML ドキュメントに署名する</span><span class="sxs-lookup"><span data-stu-id="69c7e-138">How to: Sign XML Documents with Digital Signatures</span></span>](how-to-sign-xml-documents-with-digital-signatures.md)
- [<span data-ttu-id="69c7e-139">データ保護の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="69c7e-139">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
