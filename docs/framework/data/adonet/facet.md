---
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 0157105290a297eff2c1bf799a2065872082e40e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735638"
---
# <a name="facet"></a><span data-ttu-id="d498c-102">facet</span><span class="sxs-lookup"><span data-stu-id="d498c-102">facet</span></span>
<span data-ttu-id="d498c-103">"*ファセット*" は、プリミティブ型のプロパティ定義の詳細を追加するために使用します。</span><span class="sxs-lookup"><span data-stu-id="d498c-103">A *facet* is used to add detail to a primitive type property definition.</span></span> <span data-ttu-id="d498c-104">[プロパティ](property.md)定義には、プロパティの型の情報が含まれますが、多くの場合、より詳しい情報が必要になります。</span><span class="sxs-lookup"><span data-stu-id="d498c-104">A [property](property.md) definition contains information about the property type, but often more detail is necessary.</span></span> <span data-ttu-id="d498c-105">たとえば、概念モデルのエンティティ型に、値を null に設定できない `String` 型のプロパティが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d498c-105">For example, an entity type in a conceptual model might have a property of type `String` whose value cannot be set to null.</span></span> <span data-ttu-id="d498c-106">ファセットにより、このレベルの詳細を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d498c-106">Facets allow you to specify this level of detail.</span></span>  
  
 <span data-ttu-id="d498c-107">下の表は、EDM でサポートされるファセットについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="d498c-107">The table below describes the facets that are supported in the EDM.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d498c-108">ファセットの正確な値と動作は、EDM の実装を使用するランタイム環境によって決まります。</span><span class="sxs-lookup"><span data-stu-id="d498c-108">The exact values and behaviors of facets are determined by the run-time environment that uses an EDM implementation.</span></span>  
  
|<span data-ttu-id="d498c-109">ファセット</span><span class="sxs-lookup"><span data-stu-id="d498c-109">Facet</span></span>|<span data-ttu-id="d498c-110">説明</span><span class="sxs-lookup"><span data-stu-id="d498c-110">Description</span></span>|<span data-ttu-id="d498c-111">対象</span><span class="sxs-lookup"><span data-stu-id="d498c-111">Applies to</span></span>|  
|-----------|-----------------|----------------|  
|`Collation`|<span data-ttu-id="d498c-112">プロパティの値に対して比較と順序付け操作を行うときに使用する照合シーケンス (または並べ替え順序) を指定します。</span><span class="sxs-lookup"><span data-stu-id="d498c-112">Specifies the collating sequence (or sorting sequence) to be used when performing comparison and ordering operations on values of the property.</span></span>|`String`|  
|`ConcurrencyMode`|<span data-ttu-id="d498c-113">プロパティの値をオプティミスティック コンカレンシー チェックに使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="d498c-113">Indicates that the value of the property should be used for optimistic concurrency checks.</span></span>|<span data-ttu-id="d498c-114">すべてのプリミティブ型のプロパティ</span><span class="sxs-lookup"><span data-stu-id="d498c-114">All primitive type properties</span></span>|  
|`Default`|<span data-ttu-id="d498c-115">インスタンス化で値が指定されない場合のプロパティの既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="d498c-115">Specifies the default value of the property if no value is supplied upon instantiation.</span></span>|<span data-ttu-id="d498c-116">すべてのプリミティブ型のプロパティ</span><span class="sxs-lookup"><span data-stu-id="d498c-116">All primitive type properties</span></span>|  
|`FixedLength`|<span data-ttu-id="d498c-117">プロパティ値の長さを可変とすることができるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d498c-117">Specifies whether the length of the property value can vary.</span></span>|<span data-ttu-id="d498c-118">`Binary`、`String`</span><span class="sxs-lookup"><span data-stu-id="d498c-118">`Binary`, `String`</span></span>|  
|`MaxLength`|<span data-ttu-id="d498c-119">プロパティ値の最大長を指定します。</span><span class="sxs-lookup"><span data-stu-id="d498c-119">Specifies the maximum length of the property value.</span></span>|<span data-ttu-id="d498c-120">`Binary`、`String`</span><span class="sxs-lookup"><span data-stu-id="d498c-120">`Binary`, `String`</span></span>|  
|`Nullable`|<span data-ttu-id="d498c-121">プロパティに null 値を指定できるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d498c-121">Specifies whether the property can have a null value.</span></span>|<span data-ttu-id="d498c-122">すべてのプリミティブ型のプロパティ</span><span class="sxs-lookup"><span data-stu-id="d498c-122">All primitive type properties</span></span>|  
|`Precision`|<span data-ttu-id="d498c-123">`Decimal` 型のプロパティには、プロパティ値の桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d498c-123">For properties of type `Decimal`, specifies the number of digits a property value can have.</span></span> <span data-ttu-id="d498c-124">`Time` 型、`DateTime` 型、および `DateTimeOffset` 型のプロパティには、プロパティ値の秒の小数点以下の有効桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d498c-124">For properties of type `Time`, `DateTime`, and `DateTimeOffset`, specifies the number of digits for the fractional part of seconds of the property value.</span></span>|<span data-ttu-id="d498c-125">`DateTime`、`DateTimeOffset`、`Decimal`、`Time`</span><span class="sxs-lookup"><span data-stu-id="d498c-125">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span></span>|  
|`Scale`|<span data-ttu-id="d498c-126">プロパティ値の小数点の右側の桁数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d498c-126">Specifies the number of digits to the right of the decimal point for the property value.</span></span>|<span data-ttu-id="d498c-127">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="d498c-127">Decimal</span></span>|  
|`Unicode`|<span data-ttu-id="d498c-128">プロパティ値を Unicode として保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d498c-128">Indicates whether the property value is stored as Unicode.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="d498c-129">例</span><span class="sxs-lookup"><span data-stu-id="d498c-129">Example</span></span>  
 <span data-ttu-id="d498c-130">[ADO.NET Entity Framework](./ef/index.md) では、概念スキーマ定義言語 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="d498c-130">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="d498c-131">次の CSDL は `Book` エンティティ型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="d498c-131">The following CSDL defines a `Book` entity type.</span></span> <span data-ttu-id="d498c-132">ファセットは XML 属性として実装されています。</span><span class="sxs-lookup"><span data-stu-id="d498c-132">Note that facets are implemented as XML attributes.</span></span> <span data-ttu-id="d498c-133">ファセット値は、プロパティ値を null に設定できないことと、`Scale` プロパティの `Precision` と `Revision` がそれぞれ 29 に設定されることを示します。</span><span class="sxs-lookup"><span data-stu-id="d498c-133">The facet values indicate that no property can be set to null, and that the `Scale` and `Precision` of the `Revision` property are each set to 29.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="d498c-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="d498c-134">See also</span></span>

- [<span data-ttu-id="d498c-135">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="d498c-135">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="d498c-136">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="d498c-136">Entity Data Model</span></span>](entity-data-model.md)
