---
title: '方法: XML スキーマ定義ツールを使用してクラスと XML スキーマ ドキュメントを生成する'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 4c6996e2279693cf96c826741869d72007cf81cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249553"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="c6b52-102">方法: XML スキーマ定義ツールを使用してクラスと XML スキーマ ドキュメントを生成する</span><span class="sxs-lookup"><span data-stu-id="c6b52-102">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="c6b52-103">XML スキーマ定義ツール (Xsd.exe) を使用して、クラスを説明する XML スキーマを生成したり、XML スキーマで定義されるクラスを生成したりできます。</span><span class="sxs-lookup"><span data-stu-id="c6b52-103">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="c6b52-104">次の手順では、これらの操作の実行方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c6b52-104">The following procedures show how to perform these operations.</span></span>  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="c6b52-105">特定のスキーマに準拠するクラスを生成するには</span><span class="sxs-lookup"><span data-stu-id="c6b52-105">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="c6b52-106">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c6b52-106">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="c6b52-107">XML スキーマ定義ツールに XML スキーマを引数として渡します。XML スキーマ定義ツールは、次のように XML スキーマに正確に一致するクラスのセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="c6b52-107">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="c6b52-108">ツールは、2001 年 3 月 16 日付けの World Wide Web Consortium XML 仕様を参照するスキーマのみを処理できます。</span><span class="sxs-lookup"><span data-stu-id="c6b52-108">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="c6b52-109">つまり、XML スキーマ名前空間は、次の例http://www.w3.org/2001/XMLSchemaに示すように " " にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6b52-109">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="c6b52-110">必要に応じて、クラスのメソッド、プロパティ、またはフィールドを変更します。</span><span class="sxs-lookup"><span data-stu-id="c6b52-110">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="c6b52-111">属性によるクラスの変更の詳細については、「[属性を使用した XML シリアル化の制御](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)」と「[エンコード済み SOAP シリアル化を制御する属性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6b52-111">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="c6b52-112">クラスのインスタンスがシリアル化されるときに生成される XML ストリームのスキーマを調べることは、さまざまな場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c6b52-112">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="c6b52-113">たとえば、他のユーザーが使用できるようにスキーマを公開したり、準拠しようとしているスキーマと自分のスキーマを比較したりできます。</span><span class="sxs-lookup"><span data-stu-id="c6b52-113">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="c6b52-114">クラスのセットから XML スキーマ ドキュメントを生成するには</span><span class="sxs-lookup"><span data-stu-id="c6b52-114">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="c6b52-115">クラスを DLL にコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c6b52-115">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="c6b52-116">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c6b52-116">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="c6b52-117">次の例に示すように、DLL を引数として Xsd.exe に渡します。</span><span class="sxs-lookup"><span data-stu-id="c6b52-117">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="c6b52-118">スキーマが、"schema0.xsd" という名前から順に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="c6b52-118">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b52-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6b52-119">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="c6b52-120">XML スキーマ定義ツールと XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="c6b52-120">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="c6b52-121">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="c6b52-121">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="c6b52-122">XML Schema Definition Tool (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="c6b52-122">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="c6b52-123">方法: オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="c6b52-123">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="c6b52-124">方法: オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="c6b52-124">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
