---
title: C# 型の既定値 - C# リファレンス
description: bool、char、int、float、double などの C# 型の既定値について説明します。
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625866"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="fc837-103">C# 型の既定値 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="fc837-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="fc837-104">次の表では、C# の型の既定値を示します。</span><span class="sxs-lookup"><span data-stu-id="fc837-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="fc837-105">[種類]</span><span class="sxs-lookup"><span data-stu-id="fc837-105">Type</span></span>|<span data-ttu-id="fc837-106">既定値</span><span class="sxs-lookup"><span data-stu-id="fc837-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="fc837-107">すべての参照型</span><span class="sxs-lookup"><span data-stu-id="fc837-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="fc837-108">任意の[組み込み整数数値型](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="fc837-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="fc837-109">0 (ゼロ)</span><span class="sxs-lookup"><span data-stu-id="fc837-109">0 (zero)</span></span>|
|<span data-ttu-id="fc837-110">任意の[組み込み浮動小数点数値型](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="fc837-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="fc837-111">0 (ゼロ)</span><span class="sxs-lookup"><span data-stu-id="fc837-111">0 (zero)</span></span>|
|[<span data-ttu-id="fc837-112">bool</span><span class="sxs-lookup"><span data-stu-id="fc837-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="fc837-113">char</span><span class="sxs-lookup"><span data-stu-id="fc837-113">char</span></span>](char.md)|<span data-ttu-id="fc837-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="fc837-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="fc837-115">enum</span><span class="sxs-lookup"><span data-stu-id="fc837-115">enum</span></span>](enum.md)|<span data-ttu-id="fc837-116">式 `(E)0` によって生成される値。`E` は列挙型識別子です。</span><span class="sxs-lookup"><span data-stu-id="fc837-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="fc837-117">struct</span><span class="sxs-lookup"><span data-stu-id="fc837-117">struct</span></span>](struct.md)|<span data-ttu-id="fc837-118">すべての値型フィールドが既定値に設定され、すべての参照型フィールドが `null` に設定された値。</span><span class="sxs-lookup"><span data-stu-id="fc837-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="fc837-119">任意の [null 許容値型](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="fc837-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="fc837-120"><xref:System.Nullable%601.HasValue%2A> プロパティが `false` で、<xref:System.Nullable%601.Value%2A> プロパティが未定義のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="fc837-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="fc837-121">その規定値は、null 許容値型の "*null*" 値とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="fc837-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="fc837-122">次の例に示すように、型の既定値を生成するには [default 演算子](../operators/default.md)を使います。</span><span class="sxs-lookup"><span data-stu-id="fc837-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="fc837-123">C# 7.1 以降、[`default` リテラル](../operators/default.md#default-literal)を使用して、その型の既定値に変数を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="fc837-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="fc837-124">値の型については、次の例が示すように、暗黙的なパラメーターなしのコンストラクターによっても、型の既定値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fc837-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="fc837-125">実行時に、<xref:System.Type?displayProperty=nameWithType> インスタンスが値の型を表している場合は、<xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> メソッドを使用して、パラメーターなしのコンストラクターを呼び出して、型の既定値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="fc837-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fc837-126">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="fc837-126">C# language specification</span></span>

<span data-ttu-id="fc837-127">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc837-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="fc837-128">既定値</span><span class="sxs-lookup"><span data-stu-id="fc837-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="fc837-129">既定のコンストラクター</span><span class="sxs-lookup"><span data-stu-id="fc837-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="fc837-130">参照</span><span class="sxs-lookup"><span data-stu-id="fc837-130">See also</span></span>

- [<span data-ttu-id="fc837-131">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="fc837-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fc837-132">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="fc837-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)
