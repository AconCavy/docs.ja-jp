---
title: メンバー アクセス演算子 - C# リファレンス
description: 型のメンバーにアクセスするために使用できる C# 演算子について説明します。
ms.date: 09/18/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: ba2a8cd4995b9baab2071d3fb3c7980e45565692
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039000"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="22bbe-103">メンバー アクセス演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="22bbe-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="22bbe-104">型のメンバーにアクセスするときは、次の演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-104">You can use the following operators when you access a type member:</span></span>

- <span data-ttu-id="22bbe-105">[`.` (メンバー アクセス) ](#member-access-operator-): 名前空間または型のメンバーにアクセスします</span><span class="sxs-lookup"><span data-stu-id="22bbe-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="22bbe-106">[`[]` (配列要素またはインデクサー アクセス) ](#indexer-operator-): 配列要素または型のインデクサーにアクセスします</span><span class="sxs-lookup"><span data-stu-id="22bbe-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="22bbe-107">[`?.` および `?[]` (null 条件演算子)](#null-conditional-operators--and-): オペランドが null でない場合にのみ、メンバーまたは要素へのアクセス操作を実行します</span><span class="sxs-lookup"><span data-stu-id="22bbe-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="22bbe-108">[`()` (呼び出し)](#invocation-operator-): アクセスしたメソッドを呼び出すか、デリゲートを呼び出します</span><span class="sxs-lookup"><span data-stu-id="22bbe-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="22bbe-109">[`^` (末尾からのインデックス)](#index-from-end-operator-): 要素の位置がシーケンスの末尾からであることを示します</span><span class="sxs-lookup"><span data-stu-id="22bbe-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="22bbe-110">[`..` (範囲)](#range-operator-): シーケンス要素の範囲を取得するために使用できるインデックスの範囲を指定します</span><span class="sxs-lookup"><span data-stu-id="22bbe-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="22bbe-111">メンバー アクセス演算子 .</span><span class="sxs-lookup"><span data-stu-id="22bbe-111">Member access operator .</span></span>

<span data-ttu-id="22bbe-112">以下の例に示すように、名前空間のメンバーまたは型にアクセスするために `.` トークンを使います。</span><span class="sxs-lookup"><span data-stu-id="22bbe-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="22bbe-113">次の [`using` ディレクティブ](../keywords/using-directive.md)の例に示すように、`.` を使って、名前空間内の入れ子になった名前空間にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="22bbe-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="22bbe-114">次のコードに示すように、`.` を使って "*修飾名*" を作成して名前空間内の型にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="22bbe-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="22bbe-115">[`using` ディレクティブ](../keywords/using-directive.md)を使い、必要に応じて修飾名を利用します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="22bbe-116">次のコードに示すように、`.` を使って、[型のメンバー](../../programming-guide/classes-and-structs/index.md#members) (静的および非静的) にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="22bbe-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="22bbe-117">また、`.` を使って[拡張メソッド](../../programming-guide/classes-and-structs/extension-methods.md)にアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="22bbe-118">インデクサー演算子 []</span><span class="sxs-lookup"><span data-stu-id="22bbe-118">Indexer operator []</span></span>

<span data-ttu-id="22bbe-119">通常、角かっこ `[]` は、配列、インデクサー、またはポインター要素へのアクセスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="22bbe-120">配列へのアクセス</span><span class="sxs-lookup"><span data-stu-id="22bbe-120">Array access</span></span>

<span data-ttu-id="22bbe-121">次の例は、配列要素へのアクセス方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="22bbe-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="22bbe-122">配列インデックスが配列の対応するディメンションの範囲に含まれない場合、<xref:System.IndexOutOfRangeException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="22bbe-123">前述の例が示すように、配列型の宣言と配列インスタンスのインスタンス化にも角かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="22bbe-124">配列の詳細については、「[配列](../../programming-guide/arrays/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22bbe-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="22bbe-125">インデクサーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="22bbe-125">Indexer access</span></span>

<span data-ttu-id="22bbe-126">次の例では、インデクサーへのアクセスを示すために .NET <xref:System.Collections.Generic.Dictionary%602> 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="22bbe-127">インデクサーを使用すると、配列のインデックス作成と同様の方法でユーザー定義型のインスタンスのインデックスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="22bbe-128">整数である必要がある配列インデックスとは異なり、任意の型を持つインデクサー パラメーターを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="22bbe-129">インデクサーの詳細については、「[インデクサー](../../programming-guide/indexers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22bbe-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="22bbe-130">[] の他の使用方法</span><span class="sxs-lookup"><span data-stu-id="22bbe-130">Other usages of []</span></span>

<span data-ttu-id="22bbe-131">ポインター要素へのアクセスの詳細については、[ポインターに関連する演算子](pointer-related-operators.md)に関する記事の「[ポインター要素アクセス演算子 []](pointer-related-operators.md#pointer-element-access-operator-)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22bbe-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="22bbe-132">角かっこは、[属性](../../programming-guide/concepts/attributes/index.md)を指定するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="22bbe-133">Null 条件演算子 ?.</span><span class="sxs-lookup"><span data-stu-id="22bbe-133">Null-conditional operators ?.</span></span> <span data-ttu-id="22bbe-134">および ?[]</span><span class="sxs-lookup"><span data-stu-id="22bbe-134">and ?[]</span></span>

<span data-ttu-id="22bbe-135">C# 6 以降で使用できる Null 条件付き演算子は、そのオペランドが null 以外と評価された場合にのみ、オペランドにメンバー アクセス操作 (`?.`) または要素アクセス操作 (`?[]`) を適用します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-135">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="22bbe-136">オペランドが `null` と評価された場合、演算子を適用した結果は `null` です。</span><span class="sxs-lookup"><span data-stu-id="22bbe-136">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="22bbe-137">Null 条件メンバー アクセス演算子 `?.` は Elvis 演算子とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-137">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="22bbe-138">Null 条件演算子はショートサーキットです。</span><span class="sxs-lookup"><span data-stu-id="22bbe-138">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="22bbe-139">つまり、条件付きのメンバーまたは要素アクセス操作のチェーン内にある 1 つの操作から `null` が返された場合、残りのチェーンは実行されません。</span><span class="sxs-lookup"><span data-stu-id="22bbe-139">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="22bbe-140">次の例では、`A` が `null` と評価されると `B` は評価されず、`A` または `B` が `null` と評価されると `C` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="22bbe-140">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="22bbe-141">`?.` および `?[]` 演算子の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-141">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="22bbe-142">前の例では、null 条件演算の結果が `null` の場合に評価する代替の式を指定するために、[null 合体演算子 `??`](null-coalescing-operator.md) も使用しています。</span><span class="sxs-lookup"><span data-stu-id="22bbe-142">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="22bbe-143">スレッドセーフなデリゲートの呼び出し</span><span class="sxs-lookup"><span data-stu-id="22bbe-143">Thread-safe delegate invocation</span></span>

<span data-ttu-id="22bbe-144">次のコードに示すように、`?.` 演算子を使用してデリゲートが null 以外かどうかを確認し、それをスレッドセーフな方法で呼び出します (たとえば、[イベントを発生させる](../../../standard/events/how-to-raise-and-consume-events.md)場合)。</span><span class="sxs-lookup"><span data-stu-id="22bbe-144">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="22bbe-145">このコードは、C# 5 以前で使用する次のコードと同等です。</span><span class="sxs-lookup"><span data-stu-id="22bbe-145">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="22bbe-146">呼び出し演算子 ()</span><span class="sxs-lookup"><span data-stu-id="22bbe-146">Invocation operator ()</span></span>

<span data-ttu-id="22bbe-147">かっこ `()` は、[メソッド](../../programming-guide/classes-and-structs/methods.md)を呼び出すとき、または[デリゲート](../../programming-guide/delegates/index.md)を呼び出すときに使用します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-147">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="22bbe-148">メソッドを呼び出す方法 (引数を指定した場合と指定しない場合) とデリゲートを呼び出す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-148">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="22bbe-149">かっこは、[`new`](new-operator.md) 演算子を使用して[コンストラクター](../../programming-guide/classes-and-structs/constructors.md)を呼び出すときにも使用します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-149">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="22bbe-150">() の他の使用方法</span><span class="sxs-lookup"><span data-stu-id="22bbe-150">Other usages of ()</span></span>

<span data-ttu-id="22bbe-151">式に含まれる演算を評価する順序を調整する場合にもかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-151">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="22bbe-152">詳細については、[C# 演算子](index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22bbe-152">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="22bbe-153">明示的な型変換を実行する[キャスト式](type-testing-and-cast.md#cast-operator-)でも、かっこが使われます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-153">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="22bbe-154">末尾からのインデックス演算子 ^</span><span class="sxs-lookup"><span data-stu-id="22bbe-154">Index from end operator ^</span></span>

<span data-ttu-id="22bbe-155">`^` 演算子は C# 8.0 以降で使用することができ、要素の位置がシーケンスの末尾からであることを示します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-155">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="22bbe-156">長さが `length` のシーケンスの場合、`^n` は、シーケンスの先頭からのオフセットが `length - n` である要素を指します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-156">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="22bbe-157">たとえば、`^1` は、シーケンスの最後の要素を指し、`^length` は、シーケンスの最初の要素を指します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-157">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="22bbe-158">前の例で示すように、式 `^e` は <xref:System.Index?displayProperty=nameWithType> 型です。</span><span class="sxs-lookup"><span data-stu-id="22bbe-158">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="22bbe-159">式 `^e`で、`e` の結果は `int` に暗黙に変換される必要があります。</span><span class="sxs-lookup"><span data-stu-id="22bbe-159">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="22bbe-160">さらに、`^` 演算子を[範囲演算子 ](#range-operator-) と組み合わせて使用してインデックスの範囲を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-160">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="22bbe-161">詳細については、「[インデックスと範囲](../../tutorials/ranges-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22bbe-161">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="22bbe-162">範囲演算子 ..</span><span class="sxs-lookup"><span data-stu-id="22bbe-162">Range operator ..</span></span>

<span data-ttu-id="22bbe-163">`..` 演算子は C# 8.0 以降で使用することができ、インデックスの範囲の先頭と末尾をオペランドとして指定します。</span><span class="sxs-lookup"><span data-stu-id="22bbe-163">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="22bbe-164">左側のオペランドは "*包含的*" で、範囲の先頭を含みます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-164">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="22bbe-165">右側のオペランドは "*排他的*" で、範囲の末尾を含みません。</span><span class="sxs-lookup"><span data-stu-id="22bbe-165">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="22bbe-166">次の例で示すように、どちらのオペランドであっても、シーケンスの先頭または末尾からのインデックスとすることができます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-166">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="22bbe-167">前の例で示すように、式 `a..b` は <xref:System.Range?displayProperty=nameWithType> 型です。</span><span class="sxs-lookup"><span data-stu-id="22bbe-167">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="22bbe-168">式 `a..b` で、`a` および `b` の結果は暗黙に `int` または <xref:System.Index> に変換される必要があります。</span><span class="sxs-lookup"><span data-stu-id="22bbe-168">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="22bbe-169">`..` 演算子のオペランドのいずれかを省略して、変更可能な範囲を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-169">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="22bbe-170">`a..` は `a..^0` と同じです。</span><span class="sxs-lookup"><span data-stu-id="22bbe-170">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="22bbe-171">`..b` は `0..b` と同じです。</span><span class="sxs-lookup"><span data-stu-id="22bbe-171">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="22bbe-172">`..` は `0..^0` と同じです。</span><span class="sxs-lookup"><span data-stu-id="22bbe-172">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="22bbe-173">詳細については、「[インデックスと範囲](../../tutorials/ranges-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22bbe-173">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="22bbe-174">演算子のオーバーロード可/不可</span><span class="sxs-lookup"><span data-stu-id="22bbe-174">Operator overloadability</span></span>

<span data-ttu-id="22bbe-175">`.`、`()`、`^`、および `..` の各演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="22bbe-175">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="22bbe-176">`[]` 演算子も、オーバーロードできない演算子と見なされます。</span><span class="sxs-lookup"><span data-stu-id="22bbe-176">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="22bbe-177">ユーザー定義型を使用したインデックス作成をサポートするには、[インデクサー](../../programming-guide/indexers/index.md)を使用してください。</span><span class="sxs-lookup"><span data-stu-id="22bbe-177">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="22bbe-178">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="22bbe-178">C# language specification</span></span>

<span data-ttu-id="22bbe-179">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22bbe-179">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="22bbe-180">メンバー アクセス</span><span class="sxs-lookup"><span data-stu-id="22bbe-180">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="22bbe-181">要素アクセス</span><span class="sxs-lookup"><span data-stu-id="22bbe-181">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="22bbe-182">NULL 条件演算子</span><span class="sxs-lookup"><span data-stu-id="22bbe-182">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="22bbe-183">呼び出し式</span><span class="sxs-lookup"><span data-stu-id="22bbe-183">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="22bbe-184">インデックスと範囲について詳しくは、[機能提案メモ](~/_csharplang/proposals/csharp-8.0/ranges.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22bbe-184">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="22bbe-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="22bbe-185">See also</span></span>

- [<span data-ttu-id="22bbe-186">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="22bbe-186">C# reference</span></span>](../index.md)
- [<span data-ttu-id="22bbe-187">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="22bbe-187">C# operators</span></span>](index.md)
- [<span data-ttu-id="22bbe-188">?? (Null 合体演算子)</span><span class="sxs-lookup"><span data-stu-id="22bbe-188">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="22bbe-189">:: 演算子</span><span class="sxs-lookup"><span data-stu-id="22bbe-189">:: operator</span></span>](namespace-alias-qualifier.md)
