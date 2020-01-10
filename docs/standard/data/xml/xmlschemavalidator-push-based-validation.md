---
title: XmlSchemaValidator のプッシュ ベースの検証
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: 6a0cc110c2b8bcd97b9f5c16a344db5a63046353
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709804"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="10347-102">XmlSchemaValidator のプッシュ ベースの検証</span><span class="sxs-lookup"><span data-stu-id="10347-102">XmlSchemaValidator Push-Based Validation</span></span>

<span data-ttu-id="10347-103"><xref:System.Xml.Schema.XmlSchemaValidator> は、プッシュ ベース方式で、XML スキーマを基準として XML データを検証する、効率的かつ高性能なしくみを提供します。</span><span class="sxs-lookup"><span data-stu-id="10347-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="10347-104">たとえば、<xref:System.Xml.Schema.XmlSchemaValidator> クラスでは、XML 情報セットを XML ドキュメントにシリアル化してから検証型 XML リーダーを使用してドキュメントを再解析する必要なしに、情報セットをそのまま検証することができます。</span><span class="sxs-lookup"><span data-stu-id="10347-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>

<span data-ttu-id="10347-105"><xref:System.Xml.Schema.XmlSchemaValidator> クラスは、カスタム XML データ ソースに対する検証エンジンの構築や検証型 XML ライターを構築する 1 つの手段とするなど、上級のシナリオで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="10347-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>

<span data-ttu-id="10347-106">次は、<xref:System.Xml.Schema.XmlSchemaValidator> クラスを使用して、`contosoBooks.xml` ファイルを `contosoBooks.xsd` スキーマに対して検証する一例です。</span><span class="sxs-lookup"><span data-stu-id="10347-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="10347-107">この例では、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、`contosoBooks.xml` ファイルを逆シリアル化し、ノードの値を <xref:System.Xml.Schema.XmlSchemaValidator> クラスのメソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="10347-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

> [!NOTE]
> <span data-ttu-id="10347-108">この例は、このトピックの各セクションを通じて使用されます。</span><span class="sxs-lookup"><span data-stu-id="10347-108">This example is used throughout the sections of this topic.</span></span>

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

<span data-ttu-id="10347-109">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="10347-109">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="10347-110">また、`contosoBooks.xsd` ファイルも入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="10347-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://www.contoso.com/books" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="bookstore">
        <xs:complexType>
            <xs:sequence>
                <xs:element maxOccurs="unbounded" name="book">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="title" type="xs:string" />
                            <xs:element name="author">
                                <xs:complexType>
                                    <xs:sequence>
                                        <xs:element minOccurs="0" name="name" type="xs:string" />
                                        <xs:element minOccurs="0" name="first-name" type="xs:string" />
                                        <xs:element minOccurs="0" name="last-name" type="xs:string" />
                                    </xs:sequence>
                                </xs:complexType>
                            </xs:element>
                            <xs:element name="price" type="xs:decimal" />
                        </xs:sequence>
                        <xs:attribute name="genre" type="xs:string" use="required" />
                        <xs:attribute name="publicationdate" type="xs:date" use="required" />
                        <xs:attribute name="ISBN" type="xs:string" use="required" />
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="10347-111">XmlSchemaValidator を使用した XML データの検証</span><span class="sxs-lookup"><span data-stu-id="10347-111">Validating XML Data using XmlSchemaValidator</span></span>

<span data-ttu-id="10347-112">XML 情報セットの検証を開始するには、最初に <xref:System.Xml.Schema.XmlSchemaValidator> コンストラクターを使用して <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> クラスの新しいインスタンスを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10347-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>

<span data-ttu-id="10347-113"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> コンストラクターはパラメーターとして <xref:System.Xml.XmlNameTable> 値の他に、<xref:System.Xml.Schema.XmlSchemaSet>、<xref:System.Xml.XmlNamespaceManager>、および <xref:System.Xml.Schema.XmlSchemaValidationFlags> オブジェクトをパラメーターとして取ります。</span><span class="sxs-lookup"><span data-stu-id="10347-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="10347-114"><xref:System.Xml.XmlNameTable> オブジェクトは、スキーマの名前空間や XML 名前空間などの既知の名前空間文字列を分解するために使用され、単純コンテンツの検証中に、<xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="10347-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="10347-115"><xref:System.Xml.Schema.XmlSchemaSet> オブジェクトには XML 情報セットを検証するために使用される XML スキーマが含まれています。</span><span class="sxs-lookup"><span data-stu-id="10347-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="10347-116"><xref:System.Xml.XmlNamespaceManager> オブジェクトは検証中に遭遇する名前空間を解決するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="10347-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="10347-117"><xref:System.Xml.Schema.XmlSchemaValidationFlags> 値は、検証の特定の機能を無効にするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="10347-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>

<span data-ttu-id="10347-118"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> コンストラクターの詳細については、<xref:System.Xml.Schema.XmlSchemaValidator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="initializing-validation"></a><span data-ttu-id="10347-119">検証の初期化</span><span class="sxs-lookup"><span data-stu-id="10347-119">Initializing Validation</span></span>

<span data-ttu-id="10347-120"><xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトの構築後に、<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> オブジェクトの状態の初期化に使用される 2 つのオーバーロードされた <xref:System.Xml.Schema.XmlSchemaValidator> メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="10347-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="10347-121">次が、その 2 つの <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> メソッドです。</span><span class="sxs-lookup"><span data-stu-id="10347-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<span data-ttu-id="10347-122">既定の <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> メソッドは <xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトを開始状態に初期化し、オーバーロードされた <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> メソッドは <xref:System.Xml.Schema.XmlSchemaObject> をパラメーターとして取り、部分検証のために <xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトを開始状態に初期化します。</span><span class="sxs-lookup"><span data-stu-id="10347-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="10347-123">両方の <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> メソッドは、<xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトが構築された直後、または <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A> の呼び出し後のみ呼び出し可能です。</span><span class="sxs-lookup"><span data-stu-id="10347-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>

<span data-ttu-id="10347-124"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> メソッドの例については、最初の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="10347-125"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> メソッドの詳細については、<xref:System.Xml.Schema.XmlSchemaValidator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="partial-validation"></a><span data-ttu-id="10347-126">部分検証</span><span class="sxs-lookup"><span data-stu-id="10347-126">Partial Validation</span></span>

<span data-ttu-id="10347-127"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> をパラメーターとして取る <xref:System.Xml.Schema.XmlSchemaObject> メソッドは、部分検証のために <xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトを開始状態に初期化します。</span><span class="sxs-lookup"><span data-stu-id="10347-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="10347-128">次の例で <xref:System.Xml.Schema.XmlSchemaObject> は、部分検証のために <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> メソッドを使用して初期化されます。</span><span class="sxs-lookup"><span data-stu-id="10347-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="10347-129">`orderNumber` オブジェクトの <xref:System.Xml.XmlQualifiedName> プロパティによって返された <xref:System.Xml.Schema.XmlSchemaObjectTable> コレクション内の <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> によってスキーマ要素を選択することにより、<xref:System.Xml.Schema.XmlSchemaSet> スキーマ要素が渡されます。</span><span class="sxs-lookup"><span data-stu-id="10347-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="10347-130"><xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトは、次にこの特定の要素を検証します。</span><span class="sxs-lookup"><span data-stu-id="10347-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>

```vb
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
schemaSet.Compile()
Dim nameTable As NameTable = New NameTable()
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)

Dim validator As XmlSchemaValidator = New XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None)
validator.Initialize(schemaSet.GlobalElements.Item(New XmlQualifiedName("orderNumber")))

validator.ValidateElement("orderNumber", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateText("123")
validator.ValidateEndElement(Nothing)
```

```csharp
XmlSchemaSet schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
schemaSet.Compile();
NameTable nameTable = new NameTable();
XmlNamespaceManager manager = new XmlNamespaceManager(nameTable);

XmlSchemaValidator validator = new XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
validator.Initialize(schemaSet.GlobalElements[new XmlQualifiedName("orderNumber")]);

validator.ValidateElement("orderNumber", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateText("123");
validator.ValidateEndElement(null);
```

<span data-ttu-id="10347-131">この例は、次の XML スキーマを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="10347-131">The example takes the following XML schema as input.</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

<span data-ttu-id="10347-132"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> メソッドの詳細については、<xref:System.Xml.Schema.XmlSchemaValidator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="adding-additional-schemas"></a><span data-ttu-id="10347-133">追加のスキーマの追加</span><span class="sxs-lookup"><span data-stu-id="10347-133">Adding Additional Schemas</span></span>

<span data-ttu-id="10347-134"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> クラスの <xref:System.Xml.Schema.XmlSchemaValidator> メソッドは、検証中に使用するスキーマ セットに 1 つの XML スキーマを追加するために使用します。</span><span class="sxs-lookup"><span data-stu-id="10347-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="10347-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> メソッドは、XML 情報セットの検証中に、インライン XML スキーマに遭遇した場合の効果をシミュレートするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="10347-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>

> [!NOTE]
> <span data-ttu-id="10347-136"><xref:System.Xml.Schema.XmlSchema> パラメーターの対象名前空間は、<xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトが既に遭遇したすべての要素と属性の名前空間と一致してはなりません。</span><span class="sxs-lookup"><span data-stu-id="10347-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>
>
> <span data-ttu-id="10347-137"><xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> コンストラクターに <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 値がパラメーターとして渡されなかった場合、<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> メソッドは何も行いません。</span><span class="sxs-lookup"><span data-stu-id="10347-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>

<span data-ttu-id="10347-138"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> メソッドの結果は、検証中の現在の XML ノードのコンテキストに依存します。</span><span class="sxs-lookup"><span data-stu-id="10347-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="10347-139">検証コンテキストの詳細については、このトピックの「検証コンテキスト」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="10347-140"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> メソッドの詳細については、<xref:System.Xml.Schema.XmlSchemaValidator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="10347-141">要素、属性、およびコンテンツの検証</span><span class="sxs-lookup"><span data-stu-id="10347-141">Validating Elements, Attributes, and Content</span></span>

<span data-ttu-id="10347-142"><xref:System.Xml.Schema.XmlSchemaValidator> クラスは、XML 情報セット中の要素、属性、およびコンテンツを XML スキーマに対して検証するために使用するいくつかのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="10347-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="10347-143">各メソッドに関する説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="10347-143">The following table describes each of these methods.</span></span>

|<span data-ttu-id="10347-144">メソッド</span><span class="sxs-lookup"><span data-stu-id="10347-144">Method</span></span>|<span data-ttu-id="10347-145">説明</span><span class="sxs-lookup"><span data-stu-id="10347-145">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="10347-146">現在のコンテキスト中の要素名を検証します。</span><span class="sxs-lookup"><span data-stu-id="10347-146">Validates the element name in the current context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="10347-147">現在の要素コンテキスト中の属性を検証します。または <xref:System.Xml.Schema.XmlSchemaAttribute> メソッドにパラメーターとして渡された <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> オブジェクトに対して属性を検証します。</span><span class="sxs-lookup"><span data-stu-id="10347-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="10347-148">要素コンテキスト中の必須属性がすべて揃っていることを検証し、要素の子コンテンツを検証するために <xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトを準備します。</span><span class="sxs-lookup"><span data-stu-id="10347-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="10347-149">現在の要素コンテキスト中でテキストが許されるかどうかを検証し、現在の要素に単純コンテンツがある場合は検証のためにテキストを収集します。</span><span class="sxs-lookup"><span data-stu-id="10347-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="10347-150">現在の要素コンテキスト中で空白が許されるかどうかを検証し、現在の要素に単純コンテンツがある場合は検証のために空白を収集します。</span><span class="sxs-lookup"><span data-stu-id="10347-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="10347-151">要素のテキスト コンテンツが、単純コンテンツの要素のデータ型に従って有効なことを検証し、現在の要素のコンテンツが複合コンテンツの要素として完全であることを検証します。</span><span class="sxs-lookup"><span data-stu-id="10347-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="10347-152">現在の要素コンテンツの検証をスキップし、親要素のコンテキストでコンテンツの検証するために <xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトを準備します。</span><span class="sxs-lookup"><span data-stu-id="10347-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="10347-153">検証を終了し、<xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> 検証オプションが設定されている場合は XML ドキュメント全体について ID 制約をチェックします。</span><span class="sxs-lookup"><span data-stu-id="10347-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|

> [!NOTE]
> <span data-ttu-id="10347-154"><xref:System.Xml.Schema.XmlSchemaValidator> クラスには、上の表で定義された各メソッド呼び出しの発生と順序を強制する、定義済みの状態遷移があります。</span><span class="sxs-lookup"><span data-stu-id="10347-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="10347-155"><xref:System.Xml.Schema.XmlSchemaValidator> クラスの状態遷移の詳細は、このトピックの「XmlSchemaValidator の状態遷移」セクションで説明されています。</span><span class="sxs-lookup"><span data-stu-id="10347-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>

<span data-ttu-id="10347-156">XML 情報セット内の要素、属性、およびコンテンツの検証に使用されるメソッドの例については、前のセクションの例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="10347-157">これらのメソッドの詳細については、<xref:System.Xml.Schema.XmlSchemaValidator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="10347-158">XmlValueGetter を使用したコンテンツの検証</span><span class="sxs-lookup"><span data-stu-id="10347-158">Validating Content Using an XmlValueGetter</span></span>

<span data-ttu-id="10347-159"><xref:System.Xml.Schema.XmlValueGetter>`delegate` は、属性、テキスト、または空白のノードの値を、属性、テキスト、または空白ノードの XML スキーマ定義言語 (XSD) 型と互換性のある共通言語ランタイム (CLR) 型として渡すために使用できます。</span><span class="sxs-lookup"><span data-stu-id="10347-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="10347-160"><xref:System.Xml.Schema.XmlValueGetter>`delegate` は、属性、テキスト、または空白のノードの CLR 値が既に使用可能な場合、それを `string` に変換してから検証のために再度解析する手間を省くために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="10347-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>

<span data-ttu-id="10347-161"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>、および <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> メソッドはオーバーロードされ、属性、テキスト、または空白ノードの値を `string` または <xref:System.Xml.Schema.XmlValueGetter>`delegate` として受け入れます。</span><span class="sxs-lookup"><span data-stu-id="10347-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>

<span data-ttu-id="10347-162"><xref:System.Xml.Schema.XmlSchemaValidator> クラスの次のメソッドは、<xref:System.Xml.Schema.XmlValueGetter>`delegate` をパラメーターとして受け入れます。</span><span class="sxs-lookup"><span data-stu-id="10347-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

<span data-ttu-id="10347-163">次は、最初の <xref:System.Xml.Schema.XmlValueGetter> クラスの例から取られた `delegate`<xref:System.Xml.Schema.XmlSchemaValidator> の例です。</span><span class="sxs-lookup"><span data-stu-id="10347-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="10347-164"><xref:System.Xml.Schema.XmlValueGetter>`delegate` は属性の値を <xref:System.DateTime> オブジェクトとして返します。</span><span class="sxs-lookup"><span data-stu-id="10347-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="10347-165"><xref:System.DateTime> から返された <xref:System.Xml.Schema.XmlValueGetter> オブジェクトを検証するために、<xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトは、最初にそれを属性のデータ型の ValueType (ValueType は XSD 型に対する既定の CLR の割り当て) に変換し、次に変換された値のファセットをチェックします。</span><span class="sxs-lookup"><span data-stu-id="10347-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>

```vb
Shared dateTimeGetterContent As Object

Shared Function DateTimeGetterHandle() As Object
    Return dateTimeGetterContent
End Function

Shared Function DateTimeGetter(dateTime As DateTime) As XmlValueGetter
    dateTimeGetterContent = dateTime
    Return New XmlValueGetter(AddressOf DateTimeGetterHandle)
End Function
```

```csharp
static object dateTimeGetterContent;

static object DateTimeGetterHandle()
{
    return dateTimeGetterContent;
}

static XmlValueGetter DateTimeGetter(DateTime dateTime)
{
    dateTimeGetterContent = dateTime;
    return new XmlValueGetter(dateTimeGetterHandle);
}
```

<span data-ttu-id="10347-166"><xref:System.Xml.Schema.XmlValueGetter>`delegate` の例については、最初の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="10347-167"><xref:System.Xml.Schema.XmlValueGetter>`delegate` の詳細については、<xref:System.Xml.Schema.XmlValueGetter> および <xref:System.Xml.Schema.XmlSchemaValidator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="post-schema-validation-information"></a><span data-ttu-id="10347-168">スキーマの検証後の情報</span><span class="sxs-lookup"><span data-stu-id="10347-168">Post-Schema-Validation-Information</span></span>

<span data-ttu-id="10347-169"><xref:System.Xml.Schema.XmlSchemaInfo> クラスは <xref:System.Xml.Schema.XmlSchemaValidator> クラスによって検証された 1 つの XML ノードのスキーマ検証後情報のいくつかを表します。</span><span class="sxs-lookup"><span data-stu-id="10347-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="10347-170"><xref:System.Xml.Schema.XmlSchemaValidator> クラスの種々のメソッドは <xref:System.Xml.Schema.XmlSchemaInfo> オブジェクトをオプションの (`null`) `out` パラメーターとして受け入れます。</span><span class="sxs-lookup"><span data-stu-id="10347-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>

<span data-ttu-id="10347-171">検証が成功した後、<xref:System.Xml.Schema.XmlSchemaInfo> オブジェクトには検証の結果が設定されています。</span><span class="sxs-lookup"><span data-stu-id="10347-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="10347-172">たとえば、<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> メソッドを使用した検証の成功時には、<xref:System.Xml.Schema.XmlSchemaInfo> オブジェクトの (指定した場合) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>、<xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>、<xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>、および <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> プロパティに検証結果が設定されています。</span><span class="sxs-lookup"><span data-stu-id="10347-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>

<span data-ttu-id="10347-173">次の <xref:System.Xml.Schema.XmlSchemaValidator> クラスのメソッドは、<xref:System.Xml.Schema.XmlSchemaInfo> オブジェクトを Out パラメーターとして受け入れます。</span><span class="sxs-lookup"><span data-stu-id="10347-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<span data-ttu-id="10347-174"><xref:System.Xml.Schema.XmlSchemaInfo> クラスの完全な例については、最初の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="10347-175"><xref:System.Xml.Schema.XmlSchemaInfo> クラスに関する詳細については、<xref:System.Xml.Schema.XmlSchemaInfo> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="10347-176">期待されるパーティクル、属性、および未指定の既定の属性の取得</span><span class="sxs-lookup"><span data-stu-id="10347-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>

<span data-ttu-id="10347-177"><xref:System.Xml.Schema.XmlSchemaValidator> クラスは、現在の検証コンテキスト中で期待されるパーティクル、属性、および未指定の既定の属性を取得するための <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>、および <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="10347-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>

#### <a name="retrieving-expected-particles"></a><span data-ttu-id="10347-178">期待されるパーティクルの取得</span><span class="sxs-lookup"><span data-stu-id="10347-178">Retrieving Expected Particles</span></span>

<span data-ttu-id="10347-179"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドは、現在の要素コンテキストで期待されるパーティクルを含む <xref:System.Xml.Schema.XmlSchemaParticle> オブジェクトの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="10347-180"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドが返せる有効なパーティクルは、<xref:System.Xml.Schema.XmlSchemaElement> クラスと <xref:System.Xml.Schema.XmlSchemaAny> クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="10347-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>

<span data-ttu-id="10347-181">コンテンツ モデルのコンポジターが `xs:sequence` の場合、シーケンス中の次のパーティクルのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="10347-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="10347-182">コンテンツ モデルのコンポジターが `xs:all` または `xs:choice` の場合、現在の要素コンテキストに続くことができる有効なパーティクルすべてが返されます。</span><span class="sxs-lookup"><span data-stu-id="10347-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="10347-183"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドが <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> メソッドの呼び出し直後に呼ばれると、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドはすべてのグローバル要素を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>

<span data-ttu-id="10347-184">たとえば、XSD (XML スキーマ定義言語) スキーマと続く XML ドキュメントで、`book` 要素の検証後、`book` 要素は現在の要素コンテキストになります。</span><span class="sxs-lookup"><span data-stu-id="10347-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="10347-185"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドは、<xref:System.Xml.Schema.XmlSchemaElement> 要素を表す単一の `title` オブジェクトを含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="10347-186">検証コンテキストが `title` 要素の場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドは空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="10347-187"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドが `title` 要素の検証後で `description` 要素の検証前に呼び出されると、このメソッドは <xref:System.Xml.Schema.XmlSchemaElement> 要素を表す単一の `description` オブジェクトを含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="10347-188"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドが `description` 要素の検証後に呼び出されると、メソッドはワイルドカードを表す単一の <xref:System.Xml.Schema.XmlSchemaAny> オブジェクトを含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>

```vb
Dim reader As XmlReader =  XmlReader.Create("input.xml")

Dim schemaSet As New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
Dim manager As New XmlNamespaceManager(reader.NameTable)

Dim validator As New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)
validator.Initialize()

validator.ValidateElement("book", "", Nothing)

validator.ValidateEndOfAttributes(Nothing)
For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next

validator.ValidateElement("title", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next
validator.ValidateEndElement(Nothing)

For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next

validator.ValidateElement("description", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateEndElement(Nothing)

For Each particle As XmlSchemaParticle In validator.GetExpectedParticles()
    Console.WriteLine(particle.GetType())
Next

validator.ValidateElement("namespace", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateEndElement(Nothing)

validator.ValidateEndElement(Nothing)
```

```csharp
XmlReader reader = XmlReader.Create("input.xml");

var schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
var manager = new XmlNamespaceManager(reader.NameTable);

var validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
validator.Initialize();

validator.ValidateElement("book", "", null);

validator.ValidateEndOfAttributes(null);
foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}

validator.ValidateElement("title", "", null);
validator.ValidateEndOfAttributes(null);
foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}
validator.ValidateEndElement(null);

foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}

validator.ValidateElement("description", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateEndElement(null);

foreach (XmlSchemaParticle particle in validator.GetExpectedParticles())
{
    Console.WriteLine(particle.GetType());
}

validator.ValidateElement("namespace", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateEndElement(null);

validator.ValidateEndElement(null);
```

 <span data-ttu-id="10347-189">この例では、次の XML を入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="10347-189">The example takes the following XML as input:</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">
  <xs:element name="book">
    <xs:sequence>
      <xs:element name="title" type="xs:string" />
      <xs:element name="description" type="xs:string" />
      <xs:any processContent="lax" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:element>
</xs:schema>
```

<span data-ttu-id="10347-190">この例では、入力として次の XSD スキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="10347-190">The example takes the following XSD schema as input:</span></span>

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <span data-ttu-id="10347-191"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> クラスの <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>、および <xref:System.Xml.Schema.XmlSchemaValidator> メソッドの結果は、検証中の現在のコンテキストに依存します。</span><span class="sxs-lookup"><span data-stu-id="10347-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="10347-192">詳細については、このトピックの「検証コンテキスト」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-192">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="10347-193"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドの例については、最初の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="10347-194"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドの詳細については、<xref:System.Xml.Schema.XmlSchemaValidator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="10347-195">期待される属性の取得</span><span class="sxs-lookup"><span data-stu-id="10347-195">Retrieving Expected Attributes</span></span>

<span data-ttu-id="10347-196"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> メソッドは、現在の要素コンテキストで期待される属性を含む <xref:System.Xml.Schema.XmlSchemaAttribute> オブジェクトの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>

<span data-ttu-id="10347-197">たとえば最初の例で、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> メソッドは `book` 要素のすべての属性を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="10347-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>

<span data-ttu-id="10347-198"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> メソッドを <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> メソッドの直後に呼び出すと、その XML ドキュメントで使用可能なすべての属性が返されます。</span><span class="sxs-lookup"><span data-stu-id="10347-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="10347-199">ただし、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> メソッドを <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> メソッドの 1 回以上の呼び出し後に呼び出すと、現在の要素でまだ検証されていない属性が返されます。</span><span class="sxs-lookup"><span data-stu-id="10347-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="10347-200"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> クラスの <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>、および <xref:System.Xml.Schema.XmlSchemaValidator> メソッドの結果は、検証中の現在のコンテキストに依存します。</span><span class="sxs-lookup"><span data-stu-id="10347-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="10347-201">詳細については、このトピックの「検証コンテキスト」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-201">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="10347-202"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> メソッドの例については、最初の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="10347-203"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> メソッドの詳細については、<xref:System.Xml.Schema.XmlSchemaValidator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="10347-204">未指定の既定の属性の取得</span><span class="sxs-lookup"><span data-stu-id="10347-204">Retrieving Unspecified Default Attributes</span></span>

<span data-ttu-id="10347-205"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> メソッドは、要素コンテキスト中でこれまでに <xref:System.Collections.ArrayList> メソッドを使用して検証されていない既定値を持つ属性の <xref:System.Xml.Schema.XmlSchemaAttribute> オブジェクトを指定された <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="10347-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="10347-206"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> メソッドは、要素コンテキスト中の各属性について <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> メソッドを呼び出した後で呼び出します。</span><span class="sxs-lookup"><span data-stu-id="10347-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="10347-207"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> メソッドは、検証中の XML ドキュメントに挿入される既定の属性を決定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="10347-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>

<span data-ttu-id="10347-208"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> メソッドの詳細については、<xref:System.Xml.Schema.XmlSchemaValidator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="handling-schema-validation-events"></a><span data-ttu-id="10347-209">スキーマ検証イベントの処理</span><span class="sxs-lookup"><span data-stu-id="10347-209">Handling Schema Validation Events</span></span>

<span data-ttu-id="10347-210">検証中に発生したスキーマ検証の警告とエラーは、<xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> クラスの <xref:System.Xml.Schema.XmlSchemaValidator> イベントで取り扱われます。</span><span class="sxs-lookup"><span data-stu-id="10347-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

<span data-ttu-id="10347-211">スキーマ検証の警告は、<xref:System.Xml.Schema.XmlSeverityType> 値が <xref:System.Xml.Schema.XmlSeverityType.Warning> であり、スキーマ検証エラーは、<xref:System.Xml.Schema.XmlSeverityType> 値が <xref:System.Xml.Schema.XmlSeverityType.Error> です。</span><span class="sxs-lookup"><span data-stu-id="10347-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="10347-212"><xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> が何も割り当てられていない場合、すべてのスキーマ検証エラーについて <xref:System.Xml.Schema.XmlSchemaValidationException> が <xref:System.Xml.Schema.XmlSeverityType> 値 <xref:System.Xml.Schema.XmlSeverityType.Error> でスローされます。</span><span class="sxs-lookup"><span data-stu-id="10347-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="10347-213">ただし、<xref:System.Xml.Schema.XmlSchemaValidationException> 値が <xref:System.Xml.Schema.XmlSeverityType> であるスキーマ検証警告については、<xref:System.Xml.Schema.XmlSeverityType.Warning> はスローされません。</span><span class="sxs-lookup"><span data-stu-id="10347-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>

<span data-ttu-id="10347-214">次は最初の例から取られたもので、スキーマ検証中に発見したスキーマ検証警告とエラーを受け取る <xref:System.Xml.Schema.ValidationEventHandler> の一例です。</span><span class="sxs-lookup"><span data-stu-id="10347-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>

```vb
Shared Sub SchemaValidationEventHandler(sender As Object, e As ValidationEventArgs)

    Select Case e.Severity
        Case XmlSeverityType.Error
            Console.WriteLine(vbCrLf & "Error: {0}", e.Message)
            Exit Sub
        Case XmlSeverityType.Warning
            Console.WriteLine(vbCrLf & "Warning: {0}", e.Message)
            Exit Sub
    End Select
End Sub
```

```csharp
static void SchemaValidationEventHandler(object sender, ValidationEventArgs e)
{
    switch (e.Severity)
    {
        case XmlSeverityType.Error:
            Console.WriteLine("\nError: {0}", e.Message);
            break;
        case XmlSeverityType.Warning:
            Console.WriteLine("\nWarning: {0}", e.Message);
            break;
    }
}
```

<span data-ttu-id="10347-215"><xref:System.Xml.Schema.ValidationEventHandler> の完全な例については、最初の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="10347-216">詳細については、<xref:System.Xml.Schema.XmlSchemaInfo> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10347-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="10347-217">XmlSchemaValidator の状態遷移</span><span class="sxs-lookup"><span data-stu-id="10347-217">XmlSchemaValidator State Transition</span></span>

<span data-ttu-id="10347-218"><xref:System.Xml.Schema.XmlSchemaValidator> クラスには、XML 情報セット内の要素、属性、およびコンテンツを検証するために、各メソッド呼び出しの発生と順序を強制する定義済みの状態遷移があります。</span><span class="sxs-lookup"><span data-stu-id="10347-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>

<span data-ttu-id="10347-219">次の表では、<xref:System.Xml.Schema.XmlSchemaValidator> クラスの状態遷移と、各状態で可能なメソッド呼び出しとその順序について説明します。</span><span class="sxs-lookup"><span data-stu-id="10347-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>

|<span data-ttu-id="10347-220">状態</span><span class="sxs-lookup"><span data-stu-id="10347-220">State</span></span>|<span data-ttu-id="10347-221">切り替え効果</span><span class="sxs-lookup"><span data-stu-id="10347-221">Transition</span></span>|
|-----------|----------------|
|<span data-ttu-id="10347-222">[検証]</span><span class="sxs-lookup"><span data-stu-id="10347-222">Validate</span></span>|<span data-ttu-id="10347-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="10347-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|
|<span data-ttu-id="10347-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="10347-224">TopLevel</span></span>|<span data-ttu-id="10347-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span><span class="sxs-lookup"><span data-stu-id="10347-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|
|<span data-ttu-id="10347-226">要素</span><span class="sxs-lookup"><span data-stu-id="10347-226">Element</span></span>|<span data-ttu-id="10347-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> コンテンツ\*)?</span><span class="sxs-lookup"><span data-stu-id="10347-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="10347-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="10347-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="10347-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="10347-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="10347-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> コンテンツ\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="10347-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|
|<span data-ttu-id="10347-231">Content</span><span class="sxs-lookup"><span data-stu-id="10347-231">Content</span></span>|<span data-ttu-id="10347-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span><span class="sxs-lookup"><span data-stu-id="10347-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|

> [!NOTE]
> <span data-ttu-id="10347-233"><xref:System.InvalidOperationException> オブジェクトの現在の状態に従って、メソッドの呼び出しが正しい順序で行われないと、上表の各メソッドによって <xref:System.Xml.Schema.XmlSchemaValidator> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="10347-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>

<span data-ttu-id="10347-234">上の状態遷移表では、<xref:System.Xml.Schema.XmlSchemaValidator> クラスの状態遷移の各状態で呼び出せるメソッドと他の状態を説明するために、記号が使われています。</span><span class="sxs-lookup"><span data-stu-id="10347-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="10347-235">使用される記号は、ドキュメント型定義 (DTD) の XML 標準リファレンスで見られる記号と同一です。</span><span class="sxs-lookup"><span data-stu-id="10347-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>

<span data-ttu-id="10347-236">次の表は、上の状態遷移表で見られる記号が <xref:System.Xml.Schema.XmlSchemaValidator> クラスの状態遷移中の各状態について、呼び出せるメソッドと状態にどう影響を与えるかを説明するものです。</span><span class="sxs-lookup"><span data-stu-id="10347-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

|<span data-ttu-id="10347-237">[記号]</span><span class="sxs-lookup"><span data-stu-id="10347-237">Symbol</span></span>|<span data-ttu-id="10347-238">説明</span><span class="sxs-lookup"><span data-stu-id="10347-238">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="10347-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="10347-239">&#124;</span></span>|<span data-ttu-id="10347-240">メソッドと状態 (縦棒の前後の項目) のいずれかを呼び出し可能です。</span><span class="sxs-lookup"><span data-stu-id="10347-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|
|<span data-ttu-id="10347-241">ですか。</span><span class="sxs-lookup"><span data-stu-id="10347-241">?</span></span>|<span data-ttu-id="10347-242">疑問符の前のメソッドか状態はオプションです。呼び出す場合は 1 回しか呼べません。</span><span class="sxs-lookup"><span data-stu-id="10347-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|
|*|<span data-ttu-id="10347-243">\* 記号の前のメソッドか状態はオプションです。複数回の呼び出しが可能です。</span><span class="sxs-lookup"><span data-stu-id="10347-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|

## <a name="validation-context"></a><span data-ttu-id="10347-244">検証コンテキスト</span><span class="sxs-lookup"><span data-stu-id="10347-244">Validation Context</span></span>

<span data-ttu-id="10347-245">XML 情報セット内の要素、属性、コンテンツの検証に使用される <xref:System.Xml.Schema.XmlSchemaValidator> クラスのメソッドは、<xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトの検証コンテキストを変更します。</span><span class="sxs-lookup"><span data-stu-id="10347-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="10347-246">たとえば、<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> メソッドは、現在の要素コンテンツの検証をスキップし、親要素のコンテキスト中のコンテンツを検証するために <xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトを準備します。これは、現在の要素のすべての子要素の検証をスキップして <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> メソッドを呼ぶのと同じです。</span><span class="sxs-lookup"><span data-stu-id="10347-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>

<span data-ttu-id="10347-247"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> クラスの <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>、および <xref:System.Xml.Schema.XmlSchemaValidator> メソッドの結果は、検証中の現在のコンテキストに依存します。</span><span class="sxs-lookup"><span data-stu-id="10347-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>

<span data-ttu-id="10347-248">次の表では、XML 情報セット内の要素、属性、およびコンテンツの検証に使用する <xref:System.Xml.Schema.XmlSchemaValidator> クラスのメソッドの 1 つを呼び出した後で、これらのメソッドを呼び出した場合の結果について説明します。</span><span class="sxs-lookup"><span data-stu-id="10347-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>

|<span data-ttu-id="10347-249">メソッド</span><span class="sxs-lookup"><span data-stu-id="10347-249">Method</span></span>|<span data-ttu-id="10347-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="10347-250">GetExpectedParticles</span></span>|<span data-ttu-id="10347-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="10347-251">GetExpectedAttributes</span></span>|<span data-ttu-id="10347-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="10347-252">AddSchema</span></span>|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="10347-253">既定の <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> メソッドが呼び出されると、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> はすべてのグローバル要素を含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="10347-254">1 つの要素の部分検証を初期化するために、<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> をパラメーターとして取るオーバーロードされた <xref:System.Xml.Schema.XmlSchemaObject> メソッドが呼び出された場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> は、<xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトが初期化された対象の要素だけを返します。</span><span class="sxs-lookup"><span data-stu-id="10347-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="10347-255">既定の <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> メソッドが呼び出されると、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> は空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="10347-256">1 つの属性の部分検証を初期化するために <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> をパラメーターとして取るオーバーロードの <xref:System.Xml.Schema.XmlSchemaObject> メソッドが呼び出された場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> は、<xref:System.Xml.Schema.XmlSchemaValidator> オブジェクトが初期化された対象の属性だけを返します。</span><span class="sxs-lookup"><span data-stu-id="10347-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="10347-257">プリプロセス エラーがない場合は、スキーマを <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトの <xref:System.Xml.Schema.XmlSchemaValidator> に追加します。</span><span class="sxs-lookup"><span data-stu-id="10347-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="10347-258">コンテキスト要素が有効な場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> はコンテキスト要素の子として期待される一連の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="10347-259">コンテキスト要素が無効な場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> は空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="10347-260">コンテキスト要素が有効で、これまで <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> の呼び出しが行われていない場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> はコンテキスト要素上に定義されたすべての属性のリストを返します。</span><span class="sxs-lookup"><span data-stu-id="10347-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="10347-261">いくつかの属性が既に検証されている場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> は残りの検証すべき属性のリストを返します。</span><span class="sxs-lookup"><span data-stu-id="10347-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="10347-262">コンテキスト要素が無効な場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> は空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="10347-263">上と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-263">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="10347-264">コンテキスト属性が最上位の属性である場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> は空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="10347-265">それ以外の場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> は、コンテキスト要素の最初の子として期待される一連の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="10347-266">コンテキスト属性が最上位の属性である場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> は空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="10347-267">それ以外の場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> は検証する残りの属性のリストを返します。</span><span class="sxs-lookup"><span data-stu-id="10347-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="10347-268">上と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-268">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="10347-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> は、コンテキスト要素の最初の子として期待される一連の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="10347-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> は、コンテキスト要素についてまだ検証されていない必須の属性とオプションの属性の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="10347-271">上と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-271">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="10347-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> は、コンテキスト要素の最初の子として期待される一連の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="10347-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> は空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="10347-274">上と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-274">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="10347-275">コンテキスト要素の contentType が Mixed の場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> は、次の位置で期待される一連の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="10347-276">コンテキスト要素の contentType が TextOnly または Empty の場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> は空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="10347-277">コンテキスト要素の contentType が ElementOnly の場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> は、検証エラーが既に発生しているものを除いて、次の位置で期待される一連の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="10347-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> はコンテキスト要素の検証されていない属性リストを返します。</span><span class="sxs-lookup"><span data-stu-id="10347-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="10347-279">上と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-279">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="10347-280">コンテキストの空白が最上位の空白である場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> は空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="10347-281">それ以外の場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> メソッドの動作は <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> の場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="10347-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="10347-282">コンテキストの空白が最上位の空白である場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> は空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="10347-283">それ以外の場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> メソッドの動作は <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> の場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="10347-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="10347-284">上と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-284">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="10347-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> はコンテキスト要素以降に期待される一連の要素を返します (兄弟の可能性)。</span><span class="sxs-lookup"><span data-stu-id="10347-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="10347-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> はコンテキスト要素の検証されていない属性リストを返します。</span><span class="sxs-lookup"><span data-stu-id="10347-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="10347-287">コンテキスト要素に親がない場合、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> は空のリストを返します (コンテキスト要素が、<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> を呼び出した対象である現在の要素の親)。</span><span class="sxs-lookup"><span data-stu-id="10347-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="10347-288">上と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-288">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="10347-289"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="10347-290"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="10347-291">上と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-291">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="10347-292">空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-292">Returns an empty array.</span></span>|<span data-ttu-id="10347-293">空の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="10347-293">Returns an empty array.</span></span>|<span data-ttu-id="10347-294">上と同じ。</span><span class="sxs-lookup"><span data-stu-id="10347-294">Same as above.</span></span>|

> [!NOTE]
> <span data-ttu-id="10347-295"><xref:System.Xml.Schema.XmlSchemaValidator> クラスの各種プロパティで返される値は、上の表のどのメソッドを呼び出しても変わることはありません。</span><span class="sxs-lookup"><span data-stu-id="10347-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>

## <a name="see-also"></a><span data-ttu-id="10347-296">関連項目</span><span class="sxs-lookup"><span data-stu-id="10347-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
