---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: a3a82e33d7259ec56ec3e907bc3d4d9f8a01167d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "61668719"
---
# <a name="attributeusage-c"></a><span data-ttu-id="c1c2e-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="c1c2e-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="c1c2e-103">カスタム属性クラスの使用方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="c1c2e-104"><xref:System.AttributeUsageAttribute> は、カスタム属性定義に適用する属性です。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="c1c2e-105">`AttributeUsage` 属性を使用すると、以下を制御できます。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="c1c2e-106">適用できるプログラム要素属性。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="c1c2e-107">使用法を制限しない限り、属性は以下のプログラム要素のいずれかに適用できます。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-107">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="c1c2e-108">アセンブリ (assembly)</span><span class="sxs-lookup"><span data-stu-id="c1c2e-108">assembly</span></span>
  - <span data-ttu-id="c1c2e-109">name</span><span class="sxs-lookup"><span data-stu-id="c1c2e-109">module</span></span>
  - <span data-ttu-id="c1c2e-110">のフィールド</span><span class="sxs-lookup"><span data-stu-id="c1c2e-110">field</span></span>
  - <span data-ttu-id="c1c2e-111">イベント</span><span class="sxs-lookup"><span data-stu-id="c1c2e-111">event</span></span>
  - <span data-ttu-id="c1c2e-112">method</span><span class="sxs-lookup"><span data-stu-id="c1c2e-112">method</span></span>
  - <span data-ttu-id="c1c2e-113">param</span><span class="sxs-lookup"><span data-stu-id="c1c2e-113">param</span></span>
  - <span data-ttu-id="c1c2e-114">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c1c2e-114">property</span></span>
  - <span data-ttu-id="c1c2e-115">return</span><span class="sxs-lookup"><span data-stu-id="c1c2e-115">return</span></span>
  - <span data-ttu-id="c1c2e-116">型</span><span class="sxs-lookup"><span data-stu-id="c1c2e-116">type</span></span>
- <span data-ttu-id="c1c2e-117">1 つのプログラム要素に属性を複数回適用できるかどうか。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="c1c2e-118">属性が派生クラスに継承されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="c1c2e-119">明示的に適用すると、既定の設定は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="c1c2e-120">この例で `NewAttribute` クラスはサポートされている任意のプログラム要素に適用できます。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="c1c2e-121">ただし、各エンティティに適用できるのは 1 回のみです。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="c1c2e-122">基底クラスに適用すると、属性は派生クラスに継承されます。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="c1c2e-123"><xref:System.AttributeUsageAttribute.AllowMultiple> 引数と <xref:System.AttributeUsageAttribute.Inherited> 引数は省略できるので、次のコードは同じ効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="c1c2e-124">最初の <xref:System.AttributeUsageAttribute> 引数は、<xref:System.AttributeTargets> 列挙型の 1 つまたは複数の要素でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="c1c2e-125">次の例のように、複数のターゲット型を OR 演算子で 1 つにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="c1c2e-126">C# 7.3 以降、プロパティ、または自動実装バッキング フィールドに属性を適用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="c1c2e-127">属性に `field` 指定子を指定しない限り、属性はプロパティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="c1c2e-128">その両方の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="c1c2e-129"><xref:System.AttributeUsageAttribute.AllowMultiple> 引数が `true` の場合、次の例のように、結果の属性を 1 つのエンティティに複数回適用できます。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="c1c2e-130">この例では、`MultiUseAttribute` が `AllowMultiple` に設定されているので、`true` を繰り返し適用できます。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="c1c2e-131">示されているどちらの形式でも、複数の属性を適用できます。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="c1c2e-132"><xref:System.AttributeUsageAttribute.Inherited> が `false` の場合、属性は属性クラスから派生したクラスに継承されません。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="c1c2e-133">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="c1c2e-134">この例で、`NonInheritedAttribute` は継承によって `DClass` に適用されません。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1c2e-135">解説</span><span class="sxs-lookup"><span data-stu-id="c1c2e-135">Remarks</span></span>

<span data-ttu-id="c1c2e-136">`AttributeUsage` 属性は、1 回だけ使用できる属性です。同じクラスに複数回適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="c1c2e-137">`AttributeUsage` は <xref:System.AttributeUsageAttribute> の別名です。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="c1c2e-138">詳しくは、「[リフレクションを使用した属性へのアクセス (C#)](accessing-attributes-by-using-reflection.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="c1c2e-139">例</span><span class="sxs-lookup"><span data-stu-id="c1c2e-139">Example</span></span>

<span data-ttu-id="c1c2e-140">次の例を見ると、<xref:System.AttributeUsageAttribute.Inherited> 属性に対する <xref:System.AttributeUsageAttribute.AllowMultiple> 引数と <xref:System.AttributeUsageAttribute> 引数の効果、およびクラスに適用されているカスタム属性の列挙方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="c1c2e-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="c1c2e-141">サンプル出力</span><span class="sxs-lookup"><span data-stu-id="c1c2e-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="c1c2e-142">参照</span><span class="sxs-lookup"><span data-stu-id="c1c2e-142">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="c1c2e-143">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="c1c2e-143">C# Programming Guide</span></span>](../..//index.md)
- [<span data-ttu-id="c1c2e-144">属性</span><span class="sxs-lookup"><span data-stu-id="c1c2e-144">Attributes</span></span>](../../../..//standard/attributes/index.md)
- [<span data-ttu-id="c1c2e-145">リフレクション (C#)</span><span class="sxs-lookup"><span data-stu-id="c1c2e-145">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="c1c2e-146">属性</span><span class="sxs-lookup"><span data-stu-id="c1c2e-146">Attributes</span></span>](index.md)
- [<span data-ttu-id="c1c2e-147">カスタム属性の作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="c1c2e-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="c1c2e-148">リフレクションを使用した属性へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="c1c2e-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
