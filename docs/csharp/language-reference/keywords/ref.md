---
title: ref キーワード - C# リファレンス
ms.date: 03/19/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 8d04f888befae2cad815c88a0d27bd836f458c63
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523776"
---
# <a name="ref-c-reference"></a><span data-ttu-id="a6c35-102">ref (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a6c35-102">ref (C# Reference)</span></span>

<span data-ttu-id="a6c35-103">`ref` キーワードは、参照渡しで渡される値を示します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="a6c35-104">このキーワードは、4 つの異なるコンテキストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="a6c35-105">メソッド シグネチャとメソッドの呼び出しで、参照によってメソッドに引数を渡します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="a6c35-106">詳細については、「[参照渡しで引数を渡す](#passing-an-argument-by-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6c35-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="a6c35-107">メソッド シグネチャで、参照渡しで呼び出し元に値を返します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="a6c35-108">詳細については、[参照戻り値](#reference-return-values)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6c35-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="a6c35-109">メンバーの本文で、参照戻り値が、呼び出し元によって変更される参照としてローカルに格納されること、または、通常はローカル変数が参照渡しによって別の値にアクセスすることを示します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="a6c35-110">詳細については、「[ref ローカル変数](#ref-locals)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6c35-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="a6c35-111">`struct` の宣言で、`ref struct` または `readonly ref struct` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="a6c35-112">詳細については、「[ref 構造体型](#ref-struct-types)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6c35-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="a6c35-113">参照渡しで引数を渡す</span><span class="sxs-lookup"><span data-stu-id="a6c35-113">Passing an argument by reference</span></span>

<span data-ttu-id="a6c35-114">メソッドのパラメーター リストで使用した場合、`ref` キーワードは、引数を値ではなく、参照によって渡すことを示します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="a6c35-115">`ref` キーワードは、仮パラメーターを引数 (変数にする必要があります) の別名にします。</span><span class="sxs-lookup"><span data-stu-id="a6c35-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="a6c35-116">つまり、パラメーターに対するすべての操作は引数に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="a6c35-117">たとえば、呼び出し元がローカル変数の式、または配列要素のアクセス式を渡し、呼び出されたメソッドが ref パラメーターが参照するオブジェクトを置き換える場合、メソッドから戻ったとき、呼び出し元のローカル変数または配列要素では新しいオブジェクトが参照されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="a6c35-118">参照渡しの概念と参照型の概念を混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="a6c35-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="a6c35-119">2 つの概念は同じではありません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-119">The two concepts are not the same.</span></span> <span data-ttu-id="a6c35-120">メソッドのパラメーターは、値型か参照型かどうかに関係なく、`ref` によって変更できます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="a6c35-121">参照渡しで渡される場合、値型はボックス化されません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="a6c35-122">`ref` パラメーターを使用するには、メソッド定義と呼び出し元のメソッドの両方が、次の例に示すように `ref` キーワードを明示的に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6c35-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="a6c35-123">`ref` または `in` パラメーターに渡す引数は、渡す前に初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6c35-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="a6c35-124">これは、引数を渡す前に明示的に初期化する必要がない [out](out-parameter-modifier.md) パラメーターとは異なります。</span><span class="sxs-lookup"><span data-stu-id="a6c35-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="a6c35-125">クラスのメンバーは、`ref`、`in`、または `out` のみが異なるシグネチャを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="a6c35-126">1 つの型の 2 つのメンバー間の唯一の違いが、1 つには `ref` パラメーターが存在し、もう 1 つには `out` または `in` パラメーターが存在することである場合、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="a6c35-127">たとえば、次のコードはコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="a6c35-128">ただし、次の例に示すように、1 つのメソッドに `ref`、`in` または `out` パラメーターがあり、もう 1 つのメソッドに値パラメーターがある場合、メソッドをオーバーロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="a6c35-129">非表示やオーバーライドなど、シグネチャの一致が必要な他の状況では、`in`、`ref`、`out` はシグネチャの一部であり、互いに一致しません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="a6c35-130">プロパティは変数ではありません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-130">Properties are not variables.</span></span> <span data-ttu-id="a6c35-131">プロパティはメソッドであり、`ref` パラメーターに渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="a6c35-132">次の種類のメソッドには、`ref`、`in`、`out` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="a6c35-133">[async](async.md) 修飾子を使用して定義した Async メソッド。</span><span class="sxs-lookup"><span data-stu-id="a6c35-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="a6c35-134">[yield return](yield.md) または `yield break` ステートメントを含む Iterator メソッド。</span><span class="sxs-lookup"><span data-stu-id="a6c35-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="a6c35-135">さらに、[拡張メソッド](../../programming-guide/classes-and-structs/extension-methods.md)には次の制約があります。</span><span class="sxs-lookup"><span data-stu-id="a6c35-135">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="a6c35-136">拡張メソッドの最初の引数では、`out` キーワードを使用できません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-136">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="a6c35-137">拡張メソッドの最初の引数が構造体ではない場合、または構造体として制約されていないジェネリック型である場合、その引数で `ref` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-137">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="a6c35-138">最初の引数が構造体である場合を除き、`in` キーワードは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-138">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="a6c35-139">ジェネリック型では、構造体として制約されている場合であっても、`in` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-139">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="a6c35-140">参照渡しで引数を渡す:使用例</span><span class="sxs-lookup"><span data-stu-id="a6c35-140">Passing an argument by reference: An example</span></span>

<span data-ttu-id="a6c35-141">前の例は、参照によって値型を渡す例でした。</span><span class="sxs-lookup"><span data-stu-id="a6c35-141">The previous examples pass value types by reference.</span></span> <span data-ttu-id="a6c35-142">`ref` キーワードを使用して、参照渡しで参照型を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-142">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="a6c35-143">参照型を参照渡しで渡すと、呼び出されたメソッドは、参照パラメーターが呼び出し元で参照するオブジェクトに置換できます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-143">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="a6c35-144">オブジェクトの格納場所は、参照パラメーターの値としてメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-144">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="a6c35-145">パラメーターの格納場所の値を変更する場合は (新しいオブジェクトをポイント)、呼び出し元が参照する格納場所を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-145">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="a6c35-146">次の例では、参照型のインスタンスを `ref` パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-146">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="a6c35-147">参照型を値渡しまたは参照渡しで渡す方法の詳細については、「[参照型パラメーターの引き渡し](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6c35-147">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="a6c35-148">参照戻り値</span><span class="sxs-lookup"><span data-stu-id="a6c35-148">Reference return values</span></span>

<span data-ttu-id="a6c35-149">参照戻り値 (または ref 戻り値) は、メソッドから呼び出し元に参照渡しで返される値です。</span><span class="sxs-lookup"><span data-stu-id="a6c35-149">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="a6c35-150">つまり、呼び出し元はメソッドによって返される値を変更することができ、メソッドを格納するオブジェクトの状態にその変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-150">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="a6c35-151">参照戻り値は `ref` キーワードを使用して以下に定義されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-151">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="a6c35-152">メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="a6c35-152">In the method signature.</span></span> <span data-ttu-id="a6c35-153">たとえば、次のメソッド シグネチャは、`GetCurrentPrice` メソッドが参照渡しで <xref:System.Decimal> 値を返すことを示しています。</span><span class="sxs-lookup"><span data-stu-id="a6c35-153">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="a6c35-154">メソッドの `return` ステートメントで返される変数と `return` トークンの間。</span><span class="sxs-lookup"><span data-stu-id="a6c35-154">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="a6c35-155">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-155">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="a6c35-156">呼び出し元がオブジェクトの状態を変更するには、[ref ローカル変数](#ref-locals)として明示的に定義した変数に参照戻り値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6c35-156">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="a6c35-157">呼び出されたメソッドによって、戻り値が `ref readonly` として宣言されて参照渡しで値が返されることもあり、返された値が呼び出し元のコードで変更できないように強制されることもあります。</span><span class="sxs-lookup"><span data-stu-id="a6c35-157">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="a6c35-158">呼び出し元のメソッドでは、ローカルの [ref readonly](#ref-readonly-locals) 変数に値を格納することで、返された値のコピーを回避できます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-158">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="a6c35-159">例については、「[ref 戻り値と ref ローカル変数の使用例](#a-ref-returns-and-ref-locals-example)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6c35-159">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="a6c35-160">ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="a6c35-160">Ref locals</span></span>

<span data-ttu-id="a6c35-161">ref ローカル変数は、`return ref` を使用して返された値を参照するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-161">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="a6c35-162">ref ローカル変数は、初期化して ref 戻り値以外の値にすることができません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-162">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="a6c35-163">言い換えると、初期化の右側は参照にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6c35-163">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="a6c35-164">ref ローカル変数の値に変更を加えると、参照渡しの値を返すメソッドのオブジェクトの状態に反映されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-164">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="a6c35-165">ref ローカル変数を定義するには、変数宣言の前と、参照渡しで値を返すメソッドの呼び出しの直前に、`ref` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-165">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="a6c35-166">たとえば、次のステートメントは、`GetEstimatedValue` という名前のメソッドによって返される ref ローカル変数を定義しています。</span><span class="sxs-lookup"><span data-stu-id="a6c35-166">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="a6c35-167">同じ方法で、参照渡しの値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-167">You can access a value by reference in the same way.</span></span> <span data-ttu-id="a6c35-168">場合によっては、参照渡しの値へのアクセスによって負荷がかかる可能性があるコピー操作が回避され、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a6c35-168">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="a6c35-169">たとえば、次のステートメントは、値の参照に使用される ref ローカル値をどのように定義できるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="a6c35-169">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="a6c35-170">どちらの例も、`ref` キーワードは両方の位置で使用する必要があります。そうしないと、コンパイラ エラー CS8172 "値を使用して参照渡し変数を初期化することはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-170">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="a6c35-171">C#7.3 以降、`foreach` ステートメントの反復変数を ref ローカルまたは ref readonly ローカル変数にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-171">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="a6c35-172">詳細については、[foreach ステートメント](foreach-in.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6c35-172">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="a6c35-173">また、C# 7.3 以降では、[ref 代入演算子](../operators/assignment-operator.md#ref-assignment-operator)を使用して、ref ローカルまたは ref readonly ローカル変数を再割り当てできます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-173">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="a6c35-174">ref readonly ローカル</span><span class="sxs-lookup"><span data-stu-id="a6c35-174">Ref readonly locals</span></span>

<span data-ttu-id="a6c35-175">ref readonly ローカルは、その署名に `ref readonly` があり、`return ref` を使用するメソッドまたはプロパティにより返される値の参照に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-175">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="a6c35-176">`ref readonly` 変数は `ref` ローカル変数のプロパティと `readonly` 変数の組み合わせです。それに割り当てられたストレージのエイリアスであり、変更できません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-176">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="a6c35-177">ref 戻り値と ref ローカル変数の使用例</span><span class="sxs-lookup"><span data-stu-id="a6c35-177">A ref returns and ref locals example</span></span>

<span data-ttu-id="a6c35-178">次の例は、`Title` と `Author` という 2 つの <xref:System.String> フィールドを持つ `Book` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="a6c35-178">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="a6c35-179">また、`Book` オブジェクトのプライベート配列を含む `BookCollection` クラスも定義しています。</span><span class="sxs-lookup"><span data-stu-id="a6c35-179">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="a6c35-180">個々のブック オブジェクトは、`GetBookByTitle` メソッドを呼び出すことによって参照渡しで返されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-180">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="a6c35-181">呼び出し元が `GetBookByTitle` によって返される値を ref ローカル変数として格納する場合、呼び出し元が戻り値に加えた変更が `BookCollection` オブジェクトに反映されます。次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6c35-181">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="a6c35-182">ref 構造体型</span><span class="sxs-lookup"><span data-stu-id="a6c35-182">Ref struct types</span></span>

<span data-ttu-id="a6c35-183">`ref` 修飾子を `struct` 宣言に追加すると、その型のインスタンスにはスタック割り当てが必須になるように定義されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-183">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="a6c35-184">言い換えると、そのような型のインスタンスを別のクラスのメンバーとしてヒープ上で作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-184">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="a6c35-185">この機能の第一の動機は <xref:System.Span%601> と関連構造でした。</span><span class="sxs-lookup"><span data-stu-id="a6c35-185">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="a6c35-186">スタック割り当て変数として `ref struct` 型を維持する目的の下、すべての `ref struct` 型にコンパイラが適用する規則がいくつか導入されます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-186">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="a6c35-187">`ref struct` はボックス化できません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-187">You can't box a `ref struct`.</span></span> <span data-ttu-id="a6c35-188">`object` 型、`dynamic` 型、またはあらゆるインターフェイス型の変数には、`ref struct` 型を割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-188">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="a6c35-189">`ref struct` 型では、インターフェイスを実装できません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-189">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="a6c35-190">クラスまたは通常構造体のフィールド メンバーとして `ref struct` を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-190">You can't declare a `ref struct` as a field member of a class or a normal struct.</span></span> <span data-ttu-id="a6c35-191">これには、コンパイラで生成されたバッキング フィールドを作成する、自動実装プロパティの宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-191">This includes declaring an auto-implemented property, which creates a compiler generated backing field.</span></span>
- <span data-ttu-id="a6c35-192">非同期メソッドでは、`ref struct` 型のローカル変数を宣言できません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-192">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="a6c35-193"><xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601>、`Task` のような型を返す同期メソッドで宣言できます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-193">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="a6c35-194">反復子で `ref struct` ローカル変数を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-194">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="a6c35-195">ラムダ式またはローカル関数で `ref struct` 変数をキャプチャすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a6c35-195">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="a6c35-196">これらの制約によって、誤って、マネージド ヒープに昇格させるような方法で `ref struct` を使用することが確実になくなります。</span><span class="sxs-lookup"><span data-stu-id="a6c35-196">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="a6c35-197">修飾子を組み合わせ、構造体を `readonly ref` として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-197">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="a6c35-198">`readonly ref struct` では、`ref struct` 宣言と `readonly struct` 宣言の利点と制限が組み合わされます。</span><span class="sxs-lookup"><span data-stu-id="a6c35-198">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a6c35-199">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="a6c35-199">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a6c35-200">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6c35-200">See also</span></span>

- [<span data-ttu-id="a6c35-201">安全で効率的なコードを記述する</span><span class="sxs-lookup"><span data-stu-id="a6c35-201">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="a6c35-202">ref 戻り値と ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="a6c35-202">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="a6c35-203">ref 条件式</span><span class="sxs-lookup"><span data-stu-id="a6c35-203">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="a6c35-204">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="a6c35-204">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="a6c35-205">メソッド パラメーター</span><span class="sxs-lookup"><span data-stu-id="a6c35-205">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="a6c35-206">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="a6c35-206">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a6c35-207">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a6c35-207">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a6c35-208">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="a6c35-208">C# Keywords</span></span>](index.md)
