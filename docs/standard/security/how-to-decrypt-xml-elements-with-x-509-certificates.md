---
title: '方法: X.509 証明書で XML 要素を復号化する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
ms.openlocfilehash: 32a6d95b96bb20571c14c16cc70b944fa3e4032b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277389"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="18051-102">方法: X.509 証明書で XML 要素を復号化する</span><span class="sxs-lookup"><span data-stu-id="18051-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="18051-103"><xref:System.Security.Cryptography.Xml> 名前空間のクラスを使用して、XML ドキュメント内の要素を暗号化および復号化することができます。</span><span class="sxs-lookup"><span data-stu-id="18051-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="18051-104">XML 暗号化は、データが簡単に読み取られる心配なく、暗号化された XML データを交換または保存する標準的な方法です。</span><span class="sxs-lookup"><span data-stu-id="18051-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="18051-105">XML 暗号化標準の詳細については、「」にある XML 暗号化の World Wide Web コンソーシアム (W3C) の仕様を参照してください <https://www.w3.org/TR/xmldsig-core/> 。</span><span class="sxs-lookup"><span data-stu-id="18051-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="18051-106">この例では、「[方法: X.509 証明書を使用して Xml 要素を暗号化](how-to-encrypt-xml-elements-with-x-509-certificates.md)する」で説明されているメソッドを使用して暗号化された xml 要素を復号化します。</span><span class="sxs-lookup"><span data-stu-id="18051-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="18051-107"><> 要素を検索し、要素を復号化して `EncryptedData` から、要素を元のプレーンテキスト XML 要素に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="18051-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="18051-108">この手順のコード例では、現在のユーザー アカウントのローカルの証明書ストアから X.509 証明書を使用して XML 要素を復号化しています。</span><span class="sxs-lookup"><span data-stu-id="18051-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="18051-109">この例では、メソッドを使用し <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> て、x.509 証明書を自動的に取得し、 `EncryptedKey` <> 要素の <> 要素に格納されているセッションキーを復号化し `EncryptedData` ます。</span><span class="sxs-lookup"><span data-stu-id="18051-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="18051-110">次に、<xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドは、自動的にセッション キーを使用して XML 要素を復号化します。</span><span class="sxs-lookup"><span data-stu-id="18051-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="18051-111">この例は、複数のアプリケーションが暗号化されたデータを共有する必要がある状況や、1 つのアプリケーションが、実行する時間の間に暗号化されたデータを保存する必要がある状況に適しています。</span><span class="sxs-lookup"><span data-stu-id="18051-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="18051-112">X.509 キーで XML 要素を復号化するには</span><span class="sxs-lookup"><span data-stu-id="18051-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="18051-113">ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="18051-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="18051-114"><xref:System.Xml.XmlDocument> オブジェクトには、復号化する XML 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="18051-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. <span data-ttu-id="18051-115"><xref:System.Xml.XmlDocument> オブジェクトをコンストラクターに渡して <xref:System.Security.Cryptography.Xml.EncryptedXml> オブジェクトを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="18051-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. <span data-ttu-id="18051-116"><xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> メソッドを使用して XML ドキュメントを復号化します。</span><span class="sxs-lookup"><span data-stu-id="18051-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. <span data-ttu-id="18051-117"><xref:System.Xml.XmlDocument> オブジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="18051-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="18051-118">例</span><span class="sxs-lookup"><span data-stu-id="18051-118">Example</span></span>  
 <span data-ttu-id="18051-119">この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="18051-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="18051-120">また、`"test.xml"` には `"creditcard"` 要素が含まれることも前提としています。</span><span class="sxs-lookup"><span data-stu-id="18051-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="18051-121">次の XML を `test.xml` というファイルに配置し、この例で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="18051-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="18051-122">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="18051-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="18051-123">この例をコンパイルするには、`System.Security.dll` への参照を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="18051-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="18051-124">名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。</span><span class="sxs-lookup"><span data-stu-id="18051-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="18051-125">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="18051-125">.NET Framework Security</span></span>  
 <span data-ttu-id="18051-126">この例で使用される X.509 証明書は、テスト専用です。</span><span class="sxs-lookup"><span data-stu-id="18051-126">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="18051-127">アプリケーションは、信頼された証明機関が生成する X.509 証明書、または Microsoft Windows 証明書サーバーによって生成された証明書を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18051-127">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18051-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="18051-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="18051-129">方法: X.509 証明書で XML 要素を暗号化する</span><span class="sxs-lookup"><span data-stu-id="18051-129">How to: Encrypt XML Elements with X.509 Certificates</span></span>](how-to-encrypt-xml-elements-with-x-509-certificates.md)
