---
title: throw - C# リファレンス
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 04d3138e3390627355b4b2d4e25c6b00248cec1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398113"
---
# <a name="throw-c-reference"></a><span data-ttu-id="0bbff-102">throw (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0bbff-102">throw (C# Reference)</span></span>

<span data-ttu-id="0bbff-103">プログラムの実行中に例外が発生したことを通知します。</span><span class="sxs-lookup"><span data-stu-id="0bbff-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bbff-104">解説</span><span class="sxs-lookup"><span data-stu-id="0bbff-104">Remarks</span></span>

<span data-ttu-id="0bbff-105">`throw` の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0bbff-105">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="0bbff-106">ここで `e` は <xref:System.Exception?displayProperty=nameWithType> から派生したクラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="0bbff-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0bbff-107">次の例では、`GetNumber` という名前のメソッドに渡された引数が内部配列の有効なインデックスに対応していない場合に、`throw` ステートメントを使用して <xref:System.IndexOutOfRangeException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="0bbff-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="0bbff-108">その後、メソッドの呼び出し元が `try-catch` ブロックまたは `try-catch-finally` ブロックを使用して、スローされた例外を処理します。</span><span class="sxs-lookup"><span data-stu-id="0bbff-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="0bbff-109">次の例では、`GetNumber` メソッドによってスローされた例外を処理します。</span><span class="sxs-lookup"><span data-stu-id="0bbff-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="0bbff-110">例外の再スロー</span><span class="sxs-lookup"><span data-stu-id="0bbff-110">Re-throwing an exception</span></span>

<span data-ttu-id="0bbff-111">`throw` を `catch` ブロックで使用すると、`catch` ブロックで処理された例外を再スローすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0bbff-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="0bbff-112">この場合、`throw` は例外オペランドを使用しません。</span><span class="sxs-lookup"><span data-stu-id="0bbff-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="0bbff-113">これは、メソッドが呼び出し元から他のライブラリ メソッドに引数を渡し、そのライブラリ メソッドが、呼び出し元に渡す必要がある例外をスローするときに最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0bbff-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="0bbff-114">たとえば、次の例では、初期化されていない文字列の最初の文字を取得しようとしたときにスローされた <xref:System.NullReferenceException> を再スローします。</span><span class="sxs-lookup"><span data-stu-id="0bbff-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="0bbff-115">`catch` ブロックで `throw e` 構文を使用すると、呼び出し元に渡す新しい例外をインスタンス化することもできます。</span><span class="sxs-lookup"><span data-stu-id="0bbff-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="0bbff-116">この場合、<xref:System.Exception.StackTrace> プロパティから使用できる、元の例外のスタック トレースが保持されません。</span><span class="sxs-lookup"><span data-stu-id="0bbff-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="0bbff-117">`throw` 式</span><span class="sxs-lookup"><span data-stu-id="0bbff-117">The `throw` expression</span></span>

<span data-ttu-id="0bbff-118">C# 7.0 以降、`throw` は、式およびステートメントとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="0bbff-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="0bbff-119">これにより、以前サポートされていなかったコンテキストでの例外のスローが可能になります。</span><span class="sxs-lookup"><span data-stu-id="0bbff-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="0bbff-120">チェックの内容は次のとおりです</span><span class="sxs-lookup"><span data-stu-id="0bbff-120">These include:</span></span>

- <span data-ttu-id="0bbff-121">[条件演算子](../operators/conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="0bbff-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="0bbff-122">次の例では、`throw` 式を使用して、メソッドに空の文字列配列が渡された場合に <xref:System.ArgumentException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="0bbff-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="0bbff-123">C# 7.0 より前では、このロジックが `if`/`else` ステートメントで使用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bbff-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="0bbff-124">[ull 合体演算子](../operators/null-coalescing-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="0bbff-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="0bbff-125">次の例では、null 合体演算子と共に `throw` 式を使用して、`Name` プロパティに割り当てられた文字列が `null` の場合に例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="0bbff-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="0bbff-126">式形式の[ラムダ](../../programming-guide/statements-expressions-operators/lambda-expressions.md)またはメソッド。</span><span class="sxs-lookup"><span data-stu-id="0bbff-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="0bbff-127">次の例では、<xref:System.DateTime> 値への変換がサポートされていないため <xref:System.InvalidCastException> をスローする、式形式のメソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="0bbff-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="0bbff-128">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="0bbff-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0bbff-129">参照</span><span class="sxs-lookup"><span data-stu-id="0bbff-129">See also</span></span>

- [<span data-ttu-id="0bbff-130">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="0bbff-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0bbff-131">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="0bbff-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0bbff-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="0bbff-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="0bbff-133">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="0bbff-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0bbff-134">方法: 例外を明示的にスローする</span><span class="sxs-lookup"><span data-stu-id="0bbff-134">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
