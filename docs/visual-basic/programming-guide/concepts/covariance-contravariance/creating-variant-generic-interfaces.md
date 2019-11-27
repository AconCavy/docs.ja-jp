---
title: バリアント ジェネリック インターフェイスの作成
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 74362b9d9effab028bebb9e9ecf72ac0111366d3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347066"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="9a550-102">バリアントジェネリックインターフェイスの作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a550-102">Creating Variant Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="9a550-103">インターフェイスのジェネリック型パラメーターは、共変または反変として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="9a550-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="9a550-104">"*共変性*" により、インターフェイス メソッドの戻り値の型の派生を、ジェネリック型パラメーターで定義されている型よりも強くすることができます。</span><span class="sxs-lookup"><span data-stu-id="9a550-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="9a550-105">"*反変性*" により、インターフェイス メソッドの引数の型の派生を、ジェネリック パラメーターで指定されている型よりも弱くすることができます。</span><span class="sxs-lookup"><span data-stu-id="9a550-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="9a550-106">共変または反変のジェネリック型パラメーターを持つジェネリック インターフェイスは、"*バリアント*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9a550-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="9a550-107">.NET Framework 4 では、既存のいくつかのジェネリック インターフェイスに対して、変性のサポートが導入されています。</span><span class="sxs-lookup"><span data-stu-id="9a550-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="9a550-108">.NET Framework 内のバリアントインターフェイスの一覧については、「[ジェネリックインターフェイスの分散 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a550-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="9a550-109">バリアント ジェネリック インターフェイスの宣言</span><span class="sxs-lookup"><span data-stu-id="9a550-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="9a550-110">バリアント ジェネリック インターフェイスは、ジェネリック型パラメーターの `in` キーワードと `out` キーワードを使用して宣言できます。</span><span class="sxs-lookup"><span data-stu-id="9a550-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a550-111">Visual Basic の `ByRef` パラメーターをバリアントにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9a550-111">`ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="9a550-112">また、値の型も変性をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9a550-112">Value types also do not support variance.</span></span>

<span data-ttu-id="9a550-113">ジェネリック型パラメーターを共変として宣言するには、`out` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a550-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="9a550-114">共変の型は、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a550-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="9a550-115">型がインターフェイス メソッドの戻り値の型としてのみ使用され、メソッド引数の型として使用されない。</span><span class="sxs-lookup"><span data-stu-id="9a550-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="9a550-116">この例を以下に示します。ここでは、型 `R` が共変として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="9a550-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Function GetSomething() As R
        ' The following statement generates a compiler error.
        ' Sub SetSomething(ByVal sampleArg As R)
    End Interface
    ```

    <span data-ttu-id="9a550-117">この規則には例外が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="9a550-117">There is one exception to this rule.</span></span> <span data-ttu-id="9a550-118">反変の汎用デリゲートをメソッド パラメーターとして使用する場合は、型をデリゲートのジェネリック型パラメーターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a550-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="9a550-119">次の例では、型 `R` によって示します。</span><span class="sxs-lookup"><span data-stu-id="9a550-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="9a550-120">詳細については、「[デリゲートの分散 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) 」および「 [Func と Action 汎用デリゲートの分散の使用 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a550-120">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        Sub DoSomething(ByVal callback As Action(Of R))
    End Interface
    ```

- <span data-ttu-id="9a550-121">型がインターフェイス メソッドのジェネリック制約として使用されない。</span><span class="sxs-lookup"><span data-stu-id="9a550-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="9a550-122">これを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="9a550-122">This is illustrated in the following code.</span></span>

    ```vb
    Interface ICovariant(Of Out R)
        ' The following statement generates a compiler error
        ' because you can use only contravariant or invariant types
        ' in generic constraints.
        ' Sub DoSomething(Of T As R)()
    End Interface
    ```

<span data-ttu-id="9a550-123">ジェネリック型パラメーターを反変として宣言するには、`in` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a550-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="9a550-124">反変の型は、メソッド引数の型としてのみ使用でき、インターフェイス メソッドの戻り値の型として使用できません。</span><span class="sxs-lookup"><span data-stu-id="9a550-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="9a550-125">また、反変の型はジェネリック制約にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a550-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="9a550-126">次のコードでは、反変のインターフェイスを宣言し、そのメソッドの 1 つにジェネリック制約を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9a550-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```vb
Interface IContravariant(Of In A)
    Sub SetSomething(ByVal sampleArg As A)
    Sub DoSomething(Of T As A)()
    ' The following statement generates a compiler error.
    ' Function GetSomething() As A
End Interface
```

<span data-ttu-id="9a550-127">次のコード例に示すように、同一インターフェイス内の異なる型パラメーターで、共変性と反変性の両方をサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9a550-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```vb
Interface IVariant(Of Out R, In A)
    Function GetSomething() As R
    Sub SetSomething(ByVal sampleArg As A)
    Function GetSetSomething(ByVal sampleArg As A) As R
End Interface
```

<span data-ttu-id="9a550-128">Visual Basic では、デリゲート型を指定せずに、バリアントインターフェイスでイベントを宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="9a550-128">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="9a550-129">また、バリアントインターフェイスは、入れ子になったクラス、列挙型、または構造体を持つことはできませんが、入れ子になったインターフェイスを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="9a550-129">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="9a550-130">これを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="9a550-130">This is illustrated in the following code.</span></span>

```vb
Interface ICovariant(Of Out R)
    ' The following statement generates a compiler error.
    ' Event SampleEvent()
    ' The following statement specifies the delegate type and
    ' does not generate an error.
    Event AnotherEvent As EventHandler

    ' The following statements generate compiler errors,
    ' because a variant interface cannot have
    ' nested enums, classes, or structures.

    'Enum SampleEnum : test : End Enum
    'Class SampleClass : End Class
    'Structure SampleStructure : Dim value As Integer : End Structure

    ' Variant interfaces can have nested interfaces.
    Interface INested : End Interface
End Interface
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="9a550-131">バリアント ジェネリック インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="9a550-131">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="9a550-132">バリアント ジェネリック インターフェイスをクラスに実装する場合は、インバリアント インターフェイスに使用するのと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="9a550-132">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="9a550-133">次のコード例では、共変のインターフェイスをジェネリック クラスに実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9a550-133">The following code example shows how to implement a covariant interface in a generic class.</span></span>

```vb
Interface ICovariant(Of Out R)
    Function GetSomething() As R
End Interface

Class SampleImplementation(Of R)
    Implements ICovariant(Of R)
    Public Function GetSomething() As R _
    Implements ICovariant(Of R).GetSomething
        ' Some code.
    End Function
End Class
```

<span data-ttu-id="9a550-134">バリアント インターフェイスを実装するクラスは不変です。</span><span class="sxs-lookup"><span data-stu-id="9a550-134">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="9a550-135">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9a550-135">For example, consider the following code.</span></span>

```vb
 The interface is covariant.
Dim ibutton As ICovariant(Of Button) =
    New SampleImplementation(Of Button)
Dim iobj As ICovariant(Of Object) = ibutton

' The class is invariant.
Dim button As SampleImplementation(Of Button) =
    New SampleImplementation(Of Button)
' The following statement generates a compiler error
' because classes are invariant.
' Dim obj As SampleImplementation(Of Object) = button
```

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="9a550-136">バリアント ジェネリック インターフェイスの拡張</span><span class="sxs-lookup"><span data-stu-id="9a550-136">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="9a550-137">バリアント ジェネリック インターフェイスを拡張するときは、`in` キーワードと `out` キーワードを使用して、派生インターフェイスで変性をサポートするかどうかを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a550-137">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="9a550-138">コンパイラでは、拡張されているインターフェイスからの変性の推論は行われません。</span><span class="sxs-lookup"><span data-stu-id="9a550-138">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="9a550-139">たとえば、次のようなインターフェイスがあるとします。</span><span class="sxs-lookup"><span data-stu-id="9a550-139">For example, consider the following interfaces.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T)
End Interface

Interface IExtCovariant(Of Out T)
    Inherits ICovariant(Of T)
End Interface
```

<span data-ttu-id="9a550-140">`Invariant(Of T)` インターフェイスでは、ジェネリック型パラメーター `T` は不変であり、`IExtCovariant (Of Out T)`では、型パラメーターは共変ですが、どちらのインターフェイスも同じインターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="9a550-140">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="9a550-141">これと同じ規則が、反変のジェネリック型パラメーターにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="9a550-141">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="9a550-142">拡張インターフェイスのジェネリック型パラメーター `T` が不変であれば、ジェネリック型パラメーター `T` が共変のインターフェイスと反変のインターフェイスの両方を拡張する 1 つのインターフェイスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9a550-142">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="9a550-143">これを次のコード例に図示します。</span><span class="sxs-lookup"><span data-stu-id="9a550-143">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IContravariant(Of In T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T), IContravariant(Of T)
End Interface
```

<span data-ttu-id="9a550-144">ただし、一方のインターフェイスでジェネリック型パラメーター `T` が共変として宣言されている場合は、それを拡張インターフェイスで反変として宣言することはできません。その逆についても同様です。</span><span class="sxs-lookup"><span data-stu-id="9a550-144">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="9a550-145">これを次のコード例に図示します。</span><span class="sxs-lookup"><span data-stu-id="9a550-145">This is illustrated in the following code example.</span></span>

```vb
Interface ICovariant(Of Out T)
End Interface

' The following statements generate a compiler error.
' Interface ICoContraVariant(Of In T)
'     Inherits ICovariant(Of T)
' End Interface
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="9a550-146">あいまいさの回避</span><span class="sxs-lookup"><span data-stu-id="9a550-146">Avoiding Ambiguity</span></span>

<span data-ttu-id="9a550-147">バリアント ジェネリック インターフェイスの実装時には、変性によってあいまいさが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="9a550-147">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="9a550-148">このような状況は回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a550-148">This should be avoided.</span></span>

<span data-ttu-id="9a550-149">たとえば、同一のバリアント ジェネリック インターフェイスを、異なるジェネリック型パラメーターを使用して 1 つのクラスに明示的に実装すると、あいまいさが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a550-149">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="9a550-150">この場合、コンパイラでエラーは生成されませんが、実行時にどのインターフェイスの実装が選択されるかは明確ではありません。</span><span class="sxs-lookup"><span data-stu-id="9a550-150">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="9a550-151">これにより、コードで特定しにくいバグが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a550-151">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="9a550-152">次のようなコード例があるとします。</span><span class="sxs-lookup"><span data-stu-id="9a550-152">Consider the following code example.</span></span>

> [!NOTE]
> <span data-ttu-id="9a550-153">`Option Strict Off`を使用すると、あいまいなインターフェイス実装がある場合に、Visual Basic によってコンパイラの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9a550-153">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="9a550-154">`Option Strict On`では、Visual Basic によってコンパイラエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9a550-154">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>

```vb
' Simple class hierarchy.
Class Animal
End Class

Class Cat
    Inherits Animal
End Class

Class Dog
    Inherits Animal
End Class

' This class introduces ambiguity
' because IEnumerable(Of Out T) is covariant.
Class Pets
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)

    Public Function GetEnumerator() As IEnumerator(Of Cat) _
        Implements IEnumerable(Of Cat).GetEnumerator
        Console.WriteLine("Cat")
        ' Some code.
    End Function

    Public Function GetEnumerator1() As IEnumerator(Of Dog) _
        Implements IEnumerable(Of Dog).GetEnumerator
        Console.WriteLine("Dog")
        ' Some code.
    End Function

    Public Function GetEnumerator2() As IEnumerator _
        Implements IEnumerable.GetEnumerator
        ' Some code.
    End Function
End Class

Sub Main()
    Dim pets As IEnumerable(Of Animal) = New Pets()
    pets.GetEnumerator()
End Sub
```

<span data-ttu-id="9a550-155">この例では、`pets.GetEnumerator` メソッドで `Cat` と `Dog` がどのように選択されるかが明らかではありません。</span><span class="sxs-lookup"><span data-stu-id="9a550-155">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="9a550-156">そのため、コードで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a550-156">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a550-157">参照</span><span class="sxs-lookup"><span data-stu-id="9a550-157">See also</span></span>

- [<span data-ttu-id="9a550-158">ジェネリック インターフェイスの分散 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a550-158">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="9a550-159">Func および Action 汎用デリゲートでの分散の使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a550-159">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
