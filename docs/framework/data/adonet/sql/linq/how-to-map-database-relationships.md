---
title: '方法: データベース リレーションシップを割り当てる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 2f612877f5e7da6442c242aa0d56d811c0aa7cf8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166457"
---
# <a name="how-to-map-database-relationships"></a><span data-ttu-id="0ca4b-102">方法: データベース リレーションシップを割り当てる</span><span class="sxs-lookup"><span data-stu-id="0ca4b-102">How to: Map Database Relationships</span></span>

<span data-ttu-id="0ca4b-103">データ リレーションシップが常に同じ場合は、これをエンティティ クラス内のプロパティ参照としてエンコードできます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-103">You can encode as property references in your entity class any data relationships that will always be the same.</span></span> <span data-ttu-id="0ca4b-104">たとえば、Northwind サンプル データベースでは、通常は顧客が注文を発注するため、モデルには、顧客と注文のリレーションシップが常に存在します。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-104">In the Northwind sample database, for example, because customers typically place orders, there is always a relationship in the model between customers and their orders.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0ca4b-105">では、そのようなリレーションシップを表すのに役立つ <xref:System.Data.Linq.Mapping.AssociationAttribute> 属性が定義されています。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-105">defines an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute to help represent such relationships.</span></span> <span data-ttu-id="0ca4b-106">この属性を、<xref:System.Data.Linq.EntitySet%601> 型および <xref:System.Data.Linq.EntityRef%601> 型と共に使用することで、データベース内の外部キー リレーションシップが表されます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-106">This attribute is used together with the <xref:System.Data.Linq.EntitySet%601> and <xref:System.Data.Linq.EntityRef%601> types to represent what would be a foreign key relationship in a database.</span></span> <span data-ttu-id="0ca4b-107">詳しくは、「[属性ベースの対応付け](attribute-based-mapping.md)」の関連付け属性のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-107">For more information, see the Association Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ca4b-108">AssociationAttribute プロパティ値と ColumnAttribute Storage プロパティ値では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-108">AssociationAttribute and ColumnAttribute Storage property values are case sensitive.</span></span> <span data-ttu-id="0ca4b-109">たとえば、AssociationAttribute.Storage  プロパティの属性に使用されている値は、コード内の別の場所で使用されている対応するプロパティ名と、大文字と小文字が一致するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-109">For example, ensure that values used in the attribute for the AssociationAttribute.Storage property match the case for the corresponding property names used elsewhere in the code.</span></span> <span data-ttu-id="0ca4b-110">これは、Visual Basic など、通常は大文字と小文字が区別されない言語を含むすべての .NET プログラミング言語に適用されます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-110">This applies to all .NET programming languages, even those which are not typically case sensitive, including Visual Basic.</span></span> <span data-ttu-id="0ca4b-111">Storage プロパティの詳細については、「<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-111">For more information about the Storage property, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="0ca4b-112">ほとんどのリレーションシップは、このトピックの例のように、一対多のリレーションシップです。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-112">Most relationships are one-to-many, as in the example later in this topic.</span></span> <span data-ttu-id="0ca4b-113">次に示すように、一対一および多対多のリレーションシップも表すことができます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-113">You can also represent one-to-one and many-to-many relationships as follows:</span></span>  
  
- <span data-ttu-id="0ca4b-114">一対一: 両側で <xref:System.Data.Linq.EntitySet%601> を指定することによって、この種類のリレーションシップを表します。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-114">One-to-one: Represent this kind of relationship by including <xref:System.Data.Linq.EntitySet%601> on both sides.</span></span>  
  
     <span data-ttu-id="0ca4b-115">たとえば、顧客のセキュリティ コードが `Customer` テーブルにはなく、承認されたユーザーのみがアクセスできるように作成された、`Customer`-`SecurityCode` リレーションシップがその例です。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-115">For example, consider a `Customer`-`SecurityCode` relationship, created so that the customer's security code will not be found in the `Customer` table and can be accessed only by authorized persons.</span></span>  
  
- <span data-ttu-id="0ca4b-116">多対多: 多対多リレーションシップでは、リンク テーブル ("*結合*" テーブルともいいます) の主キーは、多くの場合、他の 2 つのテーブルの外部キーが結合して作成されます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-116">Many-to-many: In many-to-many relationships, the primary key of the link table (also named the *junction* table) is often formed by a composite of the foreign keys from the other two tables.</span></span>  
  
     <span data-ttu-id="0ca4b-117">たとえば、リンク テーブル `Employee` を使用して作成される -`Project``EmployeeProject` という多対多リレーションシップがあるとします。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-117">For example, consider an `Employee`-`Project` many-to-many relationship formed by using link table `EmployeeProject`.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0ca4b-118">では、このようなリレーションシップを、`Employee`、`Project`、および `EmployeeProject` という 3 つのクラスを使用してモデル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-118">requires that such a relationship be modeled by using three classes: `Employee`, `Project`, and `EmployeeProject`.</span></span> <span data-ttu-id="0ca4b-119">この場合、`Employee` と `Project` の間のリレーションシップを変更すると、主キーの `EmployeeProject` の更新が必要であるように見える可能性がありす。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-119">In this case, changing the relationship between an `Employee` and a `Project` can appear to require an update of the primary key `EmployeeProject`.</span></span> <span data-ttu-id="0ca4b-120">ただし、この状態は、既存の `EmployeeProject` の削除、および新しい `EmployeeProject` の作成として適切にモデル化されます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-120">However, this situation is best modeled as deleting an existing `EmployeeProject` and the creating a new `EmployeeProject`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0ca4b-121">リレーショナル データベース内のリレーションシップは、通常、他のテーブルの主キーを参照する外部キー値としてモデル化されます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-121">Relationships in relational databases are typically modeled as foreign key values that refer to primary keys in other tables.</span></span> <span data-ttu-id="0ca4b-122">それらの間を移動するには、リレーショナル "*結合*" 演算を使用して、2 つのテーブルを明示的に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-122">To navigate between them you explicitly associate the two tables by using a relational *join* operation.</span></span>  
    >
    >  <span data-ttu-id="0ca4b-123">これに対し、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 内のオブジェクトは、"*ドット*" 表記を使用してナビゲートするプロパティ参照または参照のコレクションを使用して、互いを参照します。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-123">Objects in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], on the other hand, refer to each other by using property references or collections of references that you navigate by using *dot* notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ca4b-124">例</span><span class="sxs-lookup"><span data-stu-id="0ca4b-124">Example</span></span>  

 <span data-ttu-id="0ca4b-125">次の一対多の例では、`Customer` クラスは、顧客とその注文のリレーションシップを宣言するプロパティを持ちます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-125">In the following one-to-many example, the `Customer` class has a property that declares the relationship between customers and their orders.</span></span>  <span data-ttu-id="0ca4b-126">`Orders` プロパティは <xref:System.Data.Linq.EntitySet%601> 型です。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-126">The `Orders` property is of type <xref:System.Data.Linq.EntitySet%601>.</span></span> <span data-ttu-id="0ca4b-127">この型は、このリレーションシップが一対多 (1 人の顧客対多くの注文) であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-127">This type signifies that this relationship is one-to-many (one customer to many orders).</span></span> <span data-ttu-id="0ca4b-128"><xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> プロパティを使用して、この関連付けを実現する方法を記述します。つまり、これと比較する、関連クラス内のプロパティの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-128">The <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> property is used to describe how this association is accomplished, namely, by specifying the name of the property in the related class to be compared with this one.</span></span> <span data-ttu-id="0ca4b-129">この例では、データベース "*結合*" でその列の値が比較されるときに、`CustomerID` プロパティが比較されます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-129">In this example, the `CustomerID` property is compared, just as a database *join* would compare that column value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ca4b-130">Visual Studio を使用している場合は、オブジェクト リレーショナル デザイナーを使用して、クラス間の関連付けを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-130">If you are using Visual Studio, you can use the Object Relational Designer to create an association between classes.</span></span>  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="0ca4b-131">例</span><span class="sxs-lookup"><span data-stu-id="0ca4b-131">Example</span></span>  

 <span data-ttu-id="0ca4b-132">逆の場合も可能です。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-132">You can also reverse the situation.</span></span> <span data-ttu-id="0ca4b-133">`Customer` クラスを使用して顧客と注文の関連付けを記述するのではなく、`Order` クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-133">Instead of using the `Customer` class to describe the association between customers and orders, you can use the `Order` class.</span></span> <span data-ttu-id="0ca4b-134">`Order` クラスは、<xref:System.Data.Linq.EntityRef%601> 型を使用して、次のコード例に示すように、顧客へのリレーションシップを記述できます。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-134">The `Order` class uses the <xref:System.Data.Linq.EntityRef%601> type to describe the relationship back to the customer, as in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ca4b-135"><xref:System.Data.Linq.EntityRef%601> クラスでは、"*遅延読み込み*" がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-135">The <xref:System.Data.Linq.EntityRef%601> class supports *deferred loading*.</span></span> <span data-ttu-id="0ca4b-136">詳細については、「[遅延読み込みと即時読み込み](deferred-versus-immediate-loading.md)」を "*参照してください*"。</span><span class="sxs-lookup"><span data-stu-id="0ca4b-136">For more information, *see* [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="0ca4b-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ca4b-137">See also</span></span>

- [<span data-ttu-id="0ca4b-138">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="0ca4b-138">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="0ca4b-139">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="0ca4b-139">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
