---
title: 反復子
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 2789ac66690ebfd472b9bae5ccf08b1bdfaa0922
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628736"
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="da061-102">反復子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da061-102">Iterators (Visual Basic)</span></span>

<span data-ttu-id="da061-103">*反復子*を使用して、リストや配列などのコレクションをステップ実行することができます。</span><span class="sxs-lookup"><span data-stu-id="da061-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="da061-104">iterator メソッドまたは `get` アクセサーは、コレクションに対するカスタム イテレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="da061-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="da061-105">Iterator メソッドは[Yield](../../../visual-basic/language-reference/statements/yield-statement.md)ステートメントを使用して、各要素を1回に1つ返します。</span><span class="sxs-lookup"><span data-stu-id="da061-105">An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="da061-106">`Yield` ステートメントに達すると、コードの現在の場所が記憶されます。</span><span class="sxs-lookup"><span data-stu-id="da061-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="da061-107">次回、iterator 関数が呼び出されると、この位置から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="da061-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="da061-108">For Each を使用して、クライアントコードから反復子を使用します。 [次](../../../visual-basic/language-reference/statements/for-each-next-statement.md)のステートメント、または LINQ クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="da061-108">You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>

<span data-ttu-id="da061-109">次の例では、`For Each` ループの最初の反復子により、最初の `SomeNumbers` ステートメントに達するまで `Yield` iterator メソッドで実行が続行されます。</span><span class="sxs-lookup"><span data-stu-id="da061-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="da061-110">このイテレーションは 3 の値を返し、iterator メソッドの現在の場所が保持されます。</span><span class="sxs-lookup"><span data-stu-id="da061-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="da061-111">ループの次のイテレーションでは、iterator メソッドの実行が中断した場所から続行し、`Yield` ステートメントに達したときに再度停止します。</span><span class="sxs-lookup"><span data-stu-id="da061-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="da061-112">このイテレーションは 5 の値を返し、ここでも iterator メソッドの現在の場所が保持されます。</span><span class="sxs-lookup"><span data-stu-id="da061-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="da061-113">iterator メソッドの最後に達すると、ループが完了します。</span><span class="sxs-lookup"><span data-stu-id="da061-113">The loop completes when the end of the iterator method is reached.</span></span>

```vb
Sub Main()
    For Each number As Integer In SomeNumbers()
        Console.Write(number & " ")
    Next
    ' Output: 3 5 8
    Console.ReadKey()
End Sub

Private Iterator Function SomeNumbers() As System.Collections.IEnumerable
    Yield 3
    Yield 5
    Yield 8
End Function
```

<span data-ttu-id="da061-114">Iterator メソッドまたは `get` アクセサーの戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> となります。</span><span class="sxs-lookup"><span data-stu-id="da061-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="da061-115">`Exit Function` または `Return` ステートメントを使用して、イテレーションを終了できます。</span><span class="sxs-lookup"><span data-stu-id="da061-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>

<span data-ttu-id="da061-116">Visual Basic iterator 関数または `get` アクセサー宣言には、 [iterator](../../../visual-basic/language-reference/modifiers/iterator.md)修飾子が含まれています。</span><span class="sxs-lookup"><span data-stu-id="da061-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>

<span data-ttu-id="da061-117">反復子は、Visual Studio 2012 の Visual Basic で導入されました。</span><span class="sxs-lookup"><span data-stu-id="da061-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>

<span data-ttu-id="da061-118">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="da061-118">**In this topic**</span></span>

- [<span data-ttu-id="da061-119">単純な反復子</span><span class="sxs-lookup"><span data-stu-id="da061-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)

- [<span data-ttu-id="da061-120">コレクション クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="da061-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)

- [<span data-ttu-id="da061-121">Try ブロック</span><span class="sxs-lookup"><span data-stu-id="da061-121">Try Blocks</span></span>](#BKMK_TryBlocks)

- [<span data-ttu-id="da061-122">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="da061-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)

- [<span data-ttu-id="da061-123">ジェネリック リストと共に反復子を使用する</span><span class="sxs-lookup"><span data-stu-id="da061-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)

- [<span data-ttu-id="da061-124">構文情報</span><span class="sxs-lookup"><span data-stu-id="da061-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)

- [<span data-ttu-id="da061-125">技術的な実装</span><span class="sxs-lookup"><span data-stu-id="da061-125">Technical Implementation</span></span>](#BKMK_Technical)

- [<span data-ttu-id="da061-126">反復子の使用</span><span class="sxs-lookup"><span data-stu-id="da061-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)

> [!NOTE]
> <span data-ttu-id="da061-127">単純な反復子の例を除く、トピック内のすべての例では、`System.Collections` および `System.Collections.Generic` 名前空間の[Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ステートメントをインクルードします。</span><span class="sxs-lookup"><span data-stu-id="da061-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="BKMK_SimpleIterator"></a> <span data-ttu-id="da061-128">単純な反復子</span><span class="sxs-lookup"><span data-stu-id="da061-128">Simple Iterator</span></span>

<span data-ttu-id="da061-129">次の例では、For... の内部に1つの `Yield` ステートメントがあります。 [次](../../../visual-basic/language-reference/statements/for-next-statement.md)のループ。</span><span class="sxs-lookup"><span data-stu-id="da061-129">The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="da061-130">`Main` では、`For Each` ステートメント本文の各イテレーションで iterator 関数が呼び出され、これが次の `Yield` ステートメントに続行されます。</span><span class="sxs-lookup"><span data-stu-id="da061-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>

```vb
Sub Main()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    ' Output: 6 8 10 12 14 16 18
    Console.ReadKey()
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As System.Collections.Generic.IEnumerable(Of Integer)

    ' Yield even numbers in the range.
    For number As Integer = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="BKMK_CollectionClass"></a> <span data-ttu-id="da061-131">コレクション クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="da061-131">Creating a Collection Class</span></span>

<span data-ttu-id="da061-132">次の例の `DaysOfTheWeek` クラスは、<xref:System.Collections.IEnumerable> メソッドを必要とする <xref:System.Collections.IEnumerable.GetEnumerator%2A> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="da061-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="da061-133">コンパイラは、`GetEnumerator` を返す <xref:System.Collections.IEnumerator> メソッドを暗黙的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="da061-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="da061-134">`GetEnumerator` メソッドは、`Yield` ステートメントを使用して各文字列を1つずつ返し、`Iterator` 修飾子は関数宣言に含まれています。</span><span class="sxs-lookup"><span data-stu-id="da061-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>

```vb
Sub Main()
    Dim days As New DaysOfTheWeek()
    For Each day As String In days
        Console.Write(day & " ")
    Next
    ' Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey()
End Sub

Private Class DaysOfTheWeek
    Implements IEnumerable

    Public days =
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        ' Yield each day of the week.
        For i As Integer = 0 To days.Length - 1
            Yield days(i)
        Next
    End Function
End Class
```

<span data-ttu-id="da061-135">次の例では、動物のコレクションを含む `Zoo` クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="da061-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="da061-136">クラス インスタンス (`For Each`) を参照する `theZoo` ステートメントでは、`GetEnumerator` メソッドが暗黙的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="da061-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="da061-137">`For Each` および `Birds` プロパティを参照する `Mammals` ステートメントでは、`AnimalsForType` という名前の iterator メソッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="da061-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

```vb
Sub Main()
    Dim theZoo As New Zoo()

    theZoo.AddMammal("Whale")
    theZoo.AddMammal("Rhinoceros")
    theZoo.AddBird("Penguin")
    theZoo.AddBird("Warbler")

    For Each name As String In theZoo
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros Penguin Warbler

    For Each name As String In theZoo.Birds
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Penguin Warbler

    For Each name As String In theZoo.Mammals
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros

    Console.ReadKey()
End Sub

Public Class Zoo
    Implements IEnumerable

    ' Private members.
    Private animals As New List(Of Animal)

    ' Public methods.
    Public Sub AddMammal(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})
    End Sub

    Public Sub AddBird(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})
    End Sub

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        For Each theAnimal As Animal In animals
            Yield theAnimal.Name
        Next
    End Function

    ' Public members.
    Public ReadOnly Property Mammals As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Mammal)
        End Get
    End Property

    Public ReadOnly Property Birds As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Bird)
        End Get
    End Property

    ' Private methods.
    Private Iterator Function AnimalsForType( _
    ByVal type As Animal.TypeEnum) As IEnumerable
        For Each theAnimal As Animal In animals
            If (theAnimal.Type = type) Then
                Yield theAnimal.Name
            End If
        Next
    End Function

    ' Private class.
    Private Class Animal
        Public Enum TypeEnum
            Bird
            Mammal
        End Enum

        Public Property Name As String
        Public Property Type As TypeEnum
    End Class
End Class
```

## <a name="BKMK_TryBlocks"></a><span data-ttu-id="da061-138">Try ブロック</span><span class="sxs-lookup"><span data-stu-id="da061-138">Try Blocks</span></span>

<span data-ttu-id="da061-139">Visual Basic では、Try の `Try` ブロックで `Yield` ステートメントを使用できます.. [.キャッチ...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="da061-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="da061-140">`Yield` ステートメントを持つ `Try` ブロックは `Catch` ブロックを持つことができ、`Finally` ブロックを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="da061-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>

<span data-ttu-id="da061-141">次の例では、iterator 関数に `Try`、`Catch`、および `Finally` ブロックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="da061-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="da061-142">反復子関数の `Finally` ブロックは、`For Each` のイテレーションが完了する前に実行されます。</span><span class="sxs-lookup"><span data-stu-id="da061-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>

```vb
Sub Main()
    For Each number As Integer In Test()
        Console.WriteLine(number)
    Next
    Console.WriteLine("For Each is done.")

    ' Output:
    '  3
    '  4
    '  Something happened. Yields are done.
    '  Finally is called.
    '  For Each is done.
    Console.ReadKey()
End Sub

Private Iterator Function Test() As IEnumerable(Of Integer)
    Try
        Yield 3
        Yield 4
        Throw New Exception("Something happened. Yields are done.")
        Yield 5
        Yield 6
    Catch ex As Exception
        Console.WriteLine(ex.Message)
    Finally
        Console.WriteLine("Finally is called.")
    End Try
End Function
```

<span data-ttu-id="da061-143">`Yield` ステートメントを `Catch` ブロックまたは `Finally` ブロックの内部に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="da061-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="da061-144">`For Each` 本体 (iterator メソッドではなく) が例外をスローした場合、iterator 関数の `Catch` ブロックは実行されませんが、iterator 関数の `Finally` ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="da061-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="da061-145">Iterator 関数内の `Catch` ブロックは、iterator 関数内で発生した例外のみをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="da061-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="BKMK_AnonymousMethods"></a><span data-ttu-id="da061-146">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="da061-146">Anonymous Methods</span></span>

<span data-ttu-id="da061-147">Visual Basic では、匿名関数を反復子関数にすることができます。</span><span class="sxs-lookup"><span data-stu-id="da061-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="da061-148">これを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="da061-148">The following example illustrates this.</span></span>

```vb
Dim iterateSequence = Iterator Function() _
                      As IEnumerable(Of Integer)
                          Yield 1
                          Yield 2
                      End Function

For Each number As Integer In iterateSequence()
    Console.Write(number & " ")
Next
' Output: 1 2
Console.ReadKey()
```

<span data-ttu-id="da061-149">次の例では、引数を検証する非反復子メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="da061-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="da061-150">メソッドは、コレクション要素を記述する匿名反復子の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="da061-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>

```vb
Sub Main()
    For Each number As Integer In GetSequence(5, 10)
        Console.Write(number & " ")
    Next
    ' Output: 5 6 7 8 9 10
    Console.ReadKey()
End Sub

Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _
As IEnumerable
    ' Validate the arguments.
    If low < 1 Then
        Throw New ArgumentException("low is too low")
    End If
    If high > 140 Then
        Throw New ArgumentException("high is too high")
    End If

    ' Return an anonymous iterator function.
    Dim iterateSequence = Iterator Function() As IEnumerable
                              For index = low To high
                                  Yield index
                              Next
                          End Function
    Return iterateSequence()
End Function
```

<span data-ttu-id="da061-151">反復子関数の内部で検証が行われた場合、`For Each` 本体の最初の反復が開始されるまで検証を実行できません。</span><span class="sxs-lookup"><span data-stu-id="da061-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>

## <a name="BKMK_GenericList"></a> <span data-ttu-id="da061-152">ジェネリック リストと共に反復子を使用する</span><span class="sxs-lookup"><span data-stu-id="da061-152">Using Iterators with a Generic List</span></span>

<span data-ttu-id="da061-153">次の例の `Stack(Of T)` ジェネリック クラスは、<xref:System.Collections.Generic.IEnumerable%601> ジェネリック インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="da061-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="da061-154">`Push` メソッドでは、`T` 型の配列に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="da061-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="da061-155"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドは、`Yield` ステートメントを使って配列値を返します。</span><span class="sxs-lookup"><span data-stu-id="da061-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>

<span data-ttu-id="da061-156">ジェネリック メソッド <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> だけでなく、非ジェネリック メソッド <xref:System.Collections.IEnumerable.GetEnumerator%2A> も実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da061-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="da061-157">これは、<xref:System.Collections.Generic.IEnumerable%601> が <xref:System.Collections.IEnumerable> から継承するためです。</span><span class="sxs-lookup"><span data-stu-id="da061-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="da061-158">非ジェネリック実装は、ジェネリック実装に従います。</span><span class="sxs-lookup"><span data-stu-id="da061-158">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="da061-159">例では名前付き反復子を使用して、同じデータ コレクションでのさまざまな反復処理をサポートします。</span><span class="sxs-lookup"><span data-stu-id="da061-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="da061-160">この場合の名前付き反復子は、`TopToBottom` プロパティと `BottomToTop` プロパティ、および `TopN` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="da061-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="da061-161">`BottomToTop` プロパティの宣言には、`Iterator` キーワードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="da061-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>

```vb
Sub Main()
    Dim theStack As New Stack(Of Integer)

    ' Add items to the stack.
    For number As Integer = 0 To 9
        theStack.Push(number)
    Next

    ' Retrieve items from the stack.
    ' For Each is allowed because theStack implements
    ' IEnumerable(Of Integer).
    For Each number As Integer In theStack
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    ' For Each is allowed, because theStack.TopToBottom
    ' returns IEnumerable(Of Integer).
    For Each number As Integer In theStack.TopToBottom
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    For Each number As Integer In theStack.BottomToTop
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 0 1 2 3 4 5 6 7 8 9

    For Each number As Integer In theStack.TopN(7)
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3

    Console.ReadKey()
End Sub

Public Class Stack(Of T)
    Implements IEnumerable(Of T)

    Private values As T() = New T(99) {}
    Private top As Integer = 0

    Public Sub Push(ByVal t As T)
        values(top) = t
        top = top + 1
    End Sub

    Public Function Pop() As T
        top = top - 1
        Return values(top)
    End Function

    ' This function implements the GetEnumerator method. It allows
    ' an instance of the class to be used in a For Each statement.
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _
        Implements IEnumerable(Of T).GetEnumerator

        For index As Integer = top - 1 To 0 Step -1
            Yield values(index)
        Next
    End Function

    Public Iterator Function GetEnumerator1() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        Yield GetEnumerator()
    End Function

    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)
        Get
            Return Me
        End Get
    End Property

    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)
        Get
            For index As Integer = 0 To top - 1
                Yield values(index)
            Next
        End Get
    End Property

    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _
        As IEnumerable(Of T)

        ' Return less than itemsFromTop if necessary.
        Dim startIndex As Integer =
            If(itemsFromTop >= top, 0, top - itemsFromTop)

        For index As Integer = top - 1 To startIndex Step -1
            Yield values(index)
        Next
    End Function
End Class
```

## <a name="BKMK_SyntaxInformation"></a> <span data-ttu-id="da061-162">構文情報</span><span class="sxs-lookup"><span data-stu-id="da061-162">Syntax Information</span></span>

<span data-ttu-id="da061-163">反復子は、メソッドまたは `get` アクセサーとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="da061-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="da061-164">反復子を、イベント、インスタンス コンストラクター、静的コンストラクター、静的デストラクターで指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="da061-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>

<span data-ttu-id="da061-165">`Yield` ステートメント内の式の型から反復子の戻り値の型への暗黙的な変換が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da061-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>

<span data-ttu-id="da061-166">Visual Basic では、iterator メソッドに `ByRef` パラメーターを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="da061-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>

<span data-ttu-id="da061-167">Visual Basic では、"Yield" は予約語ではなく、`Iterator` メソッドまたは `get` アクセサーで使用される場合にのみ特別な意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="da061-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>

## <a name="BKMK_Technical"></a> <span data-ttu-id="da061-168">技術的な実装</span><span class="sxs-lookup"><span data-stu-id="da061-168">Technical Implementation</span></span>

<span data-ttu-id="da061-169">メソッドとして反復子を記述しても、コンパイラが入れ子のクラス (つまり、事実上、ステート マシン) に変換します。</span><span class="sxs-lookup"><span data-stu-id="da061-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="da061-170">このクラスは、クライアント コードで `For Each...Next` ループが続く限り、反復子の位置を追跡します。</span><span class="sxs-lookup"><span data-stu-id="da061-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>

<span data-ttu-id="da061-171">コンパイラの動作を確認するには、Ildasm.exe ツールを使用して、iterator メソッドに対して生成される Microsoft 中間言語コードを表示します。</span><span class="sxs-lookup"><span data-stu-id="da061-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>

<span data-ttu-id="da061-172">[クラス](../../language-reference/statements/class-statement.md)または[構造体](../../language-reference/statements/structure-statement.md)の反復子を作成する場合、<xref:System.Collections.IEnumerator> インターフェイス全体を実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="da061-172">When you create an iterator for a [class](../../language-reference/statements/class-statement.md) or [struct](../../language-reference/statements/structure-statement.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="da061-173">コンパイラは、反復子を検出すると、`Current` または `MoveNext` インターフェイスの `Dispose`、<xref:System.Collections.IEnumerator>、および <xref:System.Collections.Generic.IEnumerator%601> メソッドを自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="da061-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="da061-174">`For Each…Next` ループの連続する反復ごとに (または `IEnumerator.MoveNext` を直接呼び出すと)、前の `Yield` ステートメントの後で次の反復子コード本体が再開されます。</span><span class="sxs-lookup"><span data-stu-id="da061-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="da061-175">次に、反復子本体の末尾に到達するか、`Exit Function` または `Return` ステートメントが検出されるまで、次の `Yield` ステートメントに進みます。</span><span class="sxs-lookup"><span data-stu-id="da061-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>

<span data-ttu-id="da061-176">反復子は、<xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> メソッドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="da061-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="da061-177">反復処理を最初から再度行う場合は、新しい反復子を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da061-177">To re-iterate from the start, you must obtain a new iterator.</span></span>

<span data-ttu-id="da061-178">詳細については、 [Visual Basic 言語の仕様](../../../visual-basic/reference/language-specification/index.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da061-178">For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>

## <a name="BKMK_UseOfIterators"></a> <span data-ttu-id="da061-179">反復子の使用</span><span class="sxs-lookup"><span data-stu-id="da061-179">Use of Iterators</span></span>

<span data-ttu-id="da061-180">反復子を使用すると、複雑なコードを使用して一覧シーケンスを設定する必要がある場合に、`For Each` ループの単純さを維持することができます。</span><span class="sxs-lookup"><span data-stu-id="da061-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="da061-181">これは次のような場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="da061-181">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="da061-182">最初の `For Each` ループ イテレーションの後に一覧シーケンスを変更する。</span><span class="sxs-lookup"><span data-stu-id="da061-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>

- <span data-ttu-id="da061-183">最初の `For Each` ループ イテレーションの前に大きい一覧が完全に読み込まれないようにする。</span><span class="sxs-lookup"><span data-stu-id="da061-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="da061-184">例として、ページ フェッチでのテーブル行のバッチの読み込みなどがあります。</span><span class="sxs-lookup"><span data-stu-id="da061-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="da061-185">また、別の例として、<xref:System.IO.DirectoryInfo.EnumerateFiles%2A> メソッドでの .NET Framework 内の反復子の実装があります。</span><span class="sxs-lookup"><span data-stu-id="da061-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="da061-186">反復子に一覧の作成をカプセル化する。</span><span class="sxs-lookup"><span data-stu-id="da061-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="da061-187">iterator メソッドでは、一覧を作成してから、ループで各結果を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="da061-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="da061-188">参照</span><span class="sxs-lookup"><span data-stu-id="da061-188">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="da061-189">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="da061-189">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="da061-190">Yield ステートメント</span><span class="sxs-lookup"><span data-stu-id="da061-190">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
- [<span data-ttu-id="da061-191">Iterator</span><span class="sxs-lookup"><span data-stu-id="da061-191">Iterator</span></span>](../../../visual-basic/language-reference/modifiers/iterator.md)
