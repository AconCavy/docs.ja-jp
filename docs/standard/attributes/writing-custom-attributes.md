---
title: カスタム属性の記述
ms.date: 07/17/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
ms.openlocfilehash: 6570c6994c0f2e6571361c3eadc73b02a55f1584
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140588"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="68ef4-102">カスタム属性の記述</span><span class="sxs-lookup"><span data-stu-id="68ef4-102">Writing Custom Attributes</span></span>
<span data-ttu-id="68ef4-103">独自のカスタム属性をデザインするために、多くの新しい概念を習得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="68ef4-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="68ef4-104">オブジェクト指向プログラミングに精通してクラスをデザインする方法を理解しているなら、必要な知識をほぼすべて持っています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="68ef4-105">カスタム属性は、基本的には、 <xref:System.Attribute?displayProperty=nameWithType>から直接的に派生したか間接的に派生した従来のクラスです。</span><span class="sxs-lookup"><span data-stu-id="68ef4-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="68ef4-106">従来のクラスと同じように、カスタム属性には、データを格納したり取得したりするメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="68ef4-107">カスタム属性クラスを適切にデザインするための主要な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="68ef4-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="68ef4-108">AttributeUsageAttribute を適用する</span><span class="sxs-lookup"><span data-stu-id="68ef4-108">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="68ef4-109">属性クラスを宣言する</span><span class="sxs-lookup"><span data-stu-id="68ef4-109">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="68ef4-110">コンストラクターを宣言する</span><span class="sxs-lookup"><span data-stu-id="68ef4-110">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="68ef4-111">プロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="68ef4-111">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="68ef4-112">このセクションでは、これらの各手順について説明し、最後に[カスタム属性の例](#custom-attribute-example)について説明します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-112">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="68ef4-113">AttributeUsageAttribute を適用する</span><span class="sxs-lookup"><span data-stu-id="68ef4-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="68ef4-114">カスタム属性宣言は <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> で始まり、属性クラスの主な特性のいくつかを定義します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-114">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="68ef4-115">たとえば、属性が他のクラスによって継承されるかどうかを指定したり、属性を適用する要素を指定したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="68ef4-116">次のコード フラグメントは、<xref:System.AttributeUsageAttribute> の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-116">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="68ef4-117"><xref:System.AttributeUsageAttribute> には、カスタム属性を作成するために重要な 3 つのメンバー([AttributeTargets](#attributetargets-member)、[Inherited](#inherited-property)、[AllowMultiple](#allowmultiple-property)) があります。</span><span class="sxs-lookup"><span data-stu-id="68ef4-117">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="68ef4-118">AttributeTargets メンバー</span><span class="sxs-lookup"><span data-stu-id="68ef4-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="68ef4-119">前の例では、<xref:System.AttributeTargets.All?displayProperty=nameWithType> を指定し、この属性をすべてのプログラム要素に適用できることが示されています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-119">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="68ef4-120">代わりに、属性をクラスにのみ適用できることを示す <xref:System.AttributeTargets.Class?displayProperty=nameWithType> を指定するか、属性をメソッドにのみ適用できることを示す <xref:System.AttributeTargets.Method?displayProperty=nameWithType> を指定できます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-120">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="68ef4-121">この方法で、カスタム属性を使って、説明としてすべてのプログラム要素をマークすることができます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="68ef4-122">また、複数の <xref:System.AttributeTargets> の値を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-122">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="68ef4-123">次のコード フラグメントは、すべてのクラスやメソッドに適用できるカスタム属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="68ef4-124">Inherited プロパティ</span><span class="sxs-lookup"><span data-stu-id="68ef4-124">Inherited Property</span></span>  
 <span data-ttu-id="68ef4-125"><xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> プロパティは、属性が、その属性が適用されたクラスから派生したクラスによって継承可能かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="68ef4-126">このプロパティは、`true` (既定) か `false` フラグのいずれかを使います。</span><span class="sxs-lookup"><span data-stu-id="68ef4-126">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="68ef4-127">次の例では、`MyAttribute` には `true` の既定の <xref:System.AttributeUsageAttribute.Inherited%2A> 値が指定されていますが、`YourAttribute` には `false` の <xref:System.AttributeUsageAttribute.Inherited%2A> 値が指定されています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-127">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="68ef4-128">その後、2 つの属性が基底クラス `MyClass`に適用されます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="68ef4-129">最後に、クラス `YourClass` が基底クラス `MyClass`から継承されます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="68ef4-130">メソッド `MyMethod` は `MyAttribute`を表示しますが、 `YourAttribute`を表示しません。</span><span class="sxs-lookup"><span data-stu-id="68ef4-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="68ef4-131">AllowMultiple プロパティ</span><span class="sxs-lookup"><span data-stu-id="68ef4-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="68ef4-132"><xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> プロパティは、1 つの要素に、属性の複数のインスタンスが存在できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="68ef4-133">`true` に設定されている場合、複数のインスタンスが許可され、`false` (既定) に設定されている場合、1 つのインスタンスのみが許可されます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-133">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="68ef4-134">次の例では、`MyAttribute` には `false` の既定の <xref:System.AttributeUsageAttribute.AllowMultiple%2A> 値が指定されていますが、`YourAttribute` には `true` 値が指定されています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="68ef4-135">これらの属性の複数のインスタンスが適用されると、 `MyAttribute` ではコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="68ef4-136">次のコード例は、 `YourAttribute` の正しい使い方と `MyAttribute`の正しくない使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="68ef4-137"><xref:System.AttributeUsageAttribute.AllowMultiple%2A> プロパティと <xref:System.AttributeUsageAttribute.Inherited%2A> プロパティの両方が `true`に設定されている場合、別のクラスから継承されるクラスは属性を継承し、同じ子クラスに適用される同じ属性の別のインスタンスを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="68ef4-138"><xref:System.AttributeUsageAttribute.AllowMultiple%2A> が `false` に設定されている場合、親クラスのすべての属性の値は、子クラスの同じ属性の新しいインスタンスによって上書きされます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="68ef4-139">属性クラスを宣言する</span><span class="sxs-lookup"><span data-stu-id="68ef4-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="68ef4-140"><xref:System.AttributeUsageAttribute>を適用すると、属性を具体的に定義できるようになります。</span><span class="sxs-lookup"><span data-stu-id="68ef4-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="68ef4-141">属性クラスの宣言は、次のコードに示すように、従来のクラスの宣言に似ています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="68ef4-142">この属性定義は、次の点を示します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-142">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="68ef4-143">属性クラスはパブリック クラスとして宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ef4-143">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="68ef4-144">規則により、属性クラスの名前の終わりに **Attribute**という単語を付けます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="68ef4-145">必須ではありませんが、読みやすさの向上のために、この規定をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="68ef4-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="68ef4-146">属性を適用すると、Attribute という単語を含める必要はなくなります。</span><span class="sxs-lookup"><span data-stu-id="68ef4-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="68ef4-147">すべての属性クラスは、<xref:System.Attribute?displayProperty=nameWithType> から直接的に継承するか間接的に継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ef4-147">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="68ef4-148">Microsoft Visual Basic では、すべてのカスタム属性クラスに <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> 属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="68ef4-148">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="68ef4-149">コンストラクターを宣言する</span><span class="sxs-lookup"><span data-stu-id="68ef4-149">Declaring Constructors</span></span>  
 <span data-ttu-id="68ef4-150">属性は、従来のクラスと同じ方法で、コンストラクターで初期化されます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="68ef4-151">次のコード フラグメントは、一般的な属性のコンストラクターを示しています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="68ef4-152">このパブリック コンストラクターは、パラメーターを使って、メンバー変数と同じ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-152">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="68ef4-153">さまざまな値の組み合わせに対応するように、コンストラクターをオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="68ef4-154">カスタム属性クラスの[プロパティ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120))も定義する場合、属性を初期化する際に、名前付きパラメーターと位置指定パラメーターの組み合わせを使うことができます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-154">If you also define a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="68ef4-155">通常、必須パラメーターすべてを位置指定パラメーター、省略可能なパラメーターすべてを名前付きパラメーターとして定義します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="68ef4-156">この場合、属性は必須パラメーターがないと初期化できません。</span><span class="sxs-lookup"><span data-stu-id="68ef4-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="68ef4-157">その他のすべてのパラメーターは省略できます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-157">All other parameters are optional.</span></span> <span data-ttu-id="68ef4-158">Visual Basic では、属性クラスのコンストラクターで ParamArray 引数を使うべきではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="68ef4-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="68ef4-159">次のコード例は、省略可能なパラメーターと必須パラメーターを使って、前のコンストラクターを使う属性を適用できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="68ef4-160">ここでは、属性には、必須のブール値 1 つと省略可能な文字列のプロパティ 1 つが含まれていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="68ef4-161">プロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="68ef4-161">Declaring Properties</span></span>  
 <span data-ttu-id="68ef4-162">名前付きパラメーターを定義するか、属性によって格納される値を簡単に返すことができるようにする場合、[プロパティ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120))を宣言します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="68ef4-163">属性プロパティは、返されるデータ型の記述を添えて、パブリック エンティティとして宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68ef4-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="68ef4-164">プロパティの値を保持する変数を定義して、その変数を **get** メソッドと **set** メソッドに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="68ef4-165">次のコード例は、属性に単純なプロパティを実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="68ef4-166">カスタム属性の例</span><span class="sxs-lookup"><span data-stu-id="68ef4-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="68ef4-167">このセクションには、前の情報が含まれており、コードのセクションの作成者に関する情報を文書化する単純な属性をデザインする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="68ef4-168">この例の属性は、プログラマの名前とレベル、またコードを確認したかどうかを格納します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="68ef4-169">保存する実際の値を格納するため、3 つのプライベート変数を使います。</span><span class="sxs-lookup"><span data-stu-id="68ef4-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="68ef4-170">各変数は、値を取得して設定するパブリック プロパティで表されます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="68ef4-171">最後に、コンストラクターを 2 つの必須パラメーターを使って定義します。</span><span class="sxs-lookup"><span data-stu-id="68ef4-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="68ef4-172">完全名 `DeveloperAttribute`や省略名 `Developer`を使って、次のいずれかの方法でこの属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="68ef4-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="68ef4-173">最初の例は、必須の名前付きパラメーターのみを使って適用された属性を示し、2 番目の例は、必須パラメーターと省略可能なパラメーターの両方を使って適用された属性を示しています。</span><span class="sxs-lookup"><span data-stu-id="68ef4-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68ef4-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="68ef4-174">See also</span></span>

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="68ef4-175">属性</span><span class="sxs-lookup"><span data-stu-id="68ef4-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
