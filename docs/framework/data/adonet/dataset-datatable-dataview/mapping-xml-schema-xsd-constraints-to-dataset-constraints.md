---
title: XML スキーマ (XSD) 制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b44c3193e1b9e2e52e086111eab0ab0b0cae5c97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786075"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="d8194-102">XML スキーマ (XSD) 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="d8194-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="d8194-103">XML スキーマ定義言語 (XSD) を使用すると、定義する要素と属性で制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d8194-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="d8194-104">XML スキーマを <xref:System.Data.DataSet> のリレーショナル スキーマにマップすると、XML スキーマの制約が **DataSet** 内のテーブルと列の適切なリレーショナル制約にマップされます。</span><span class="sxs-lookup"><span data-stu-id="d8194-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="d8194-105">このセクションでは、次の XML スキーマの制約の割り当てについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d8194-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
- <span data-ttu-id="d8194-106">**unique** 要素を使用して指定される一意性制約。</span><span class="sxs-lookup"><span data-stu-id="d8194-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
- <span data-ttu-id="d8194-107">**key** 要素を使用して指定されるキー制約。</span><span class="sxs-lookup"><span data-stu-id="d8194-107">The key constraint specified using the **key** element.</span></span>  
  
- <span data-ttu-id="d8194-108">**keyref** 要素を使用して指定されるキー参照制約。</span><span class="sxs-lookup"><span data-stu-id="d8194-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="d8194-109">要素または属性に対して制約を指定することにより、同じスキーマに基づくあらゆるドキュメントで、その要素の値について特定の制限を適用できます。</span><span class="sxs-lookup"><span data-stu-id="d8194-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="d8194-110">たとえば、スキーマにある **Customer** 要素の **CustomerID** 子要素のキー制約は、**CustomerID** 子要素の値がすべてのドキュメントのインスタンスで一意であり、null 値が許可されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d8194-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="d8194-111">さらに、ドキュメント内のリレーションシップを確立するために、ドキュメント内の要素および属性間に制約を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8194-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="d8194-112">ドキュメント内で制約を指定するためにスキーマ内で key 制約または keyref 制約を使用すると、ドキュメントの要素と属性間にリレーションシップを持つことになります。</span><span class="sxs-lookup"><span data-stu-id="d8194-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="d8194-113">マッピング処理では、これらのスキーマ制約が **DataSet** 内に作成されたテーブルでの適切な制約に変換されます。</span><span class="sxs-lookup"><span data-stu-id="d8194-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8194-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d8194-114">In This Section</span></span>  
 [<span data-ttu-id="d8194-115">XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="d8194-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d8194-116">**DataSet** での一意制約の作成に使用する XML スキーマの要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8194-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="d8194-117">XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="d8194-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d8194-118">**DataSet** でのキー制約 (一意制約では null 値が許可されません) の作成に使用する XML スキーマの要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8194-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="d8194-119">XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="d8194-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d8194-120">**DataSet** でのキー参照 (外部キー) 制約の作成に使用する XML スキーマの要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8194-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d8194-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8194-121">Related Sections</span></span>  
 [<span data-ttu-id="d8194-122">XML スキーマ (XSD) からの DataSet リレーショナル構造の派生</span><span class="sxs-lookup"><span data-stu-id="d8194-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="d8194-123">XSD スキーマから作成された **DataSet** のリレーショナル構造 (スキーマ) について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8194-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="d8194-124">XML スキーマ (XSD) からの DataSet リレーションの生成</span><span class="sxs-lookup"><span data-stu-id="d8194-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="d8194-125">**DataSet** でのテーブル列間のリレーションの生成に使用する XML スキーマの要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8194-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8194-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8194-126">See also</span></span>

- [<span data-ttu-id="d8194-127">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="d8194-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
