---
title: LINQ クエリのカスタム メソッドを追加する方法 (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: e3f8ba8810d06a2e79093e6022ad6e79f3599468
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447031"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="195e4-102">LINQ クエリのカスタム メソッドを追加する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="195e4-102">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="195e4-103"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスに拡張メソッドを追加することで、LINQ クエリに使用できるメソッド セットを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="195e4-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="195e4-104">たとえば一連の値から単一の値を求めるために、平均値や最大値を求める標準的な演算に加えて、独自の集計メソッドを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="195e4-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="195e4-105">また、一連の値を受け取って別の一連の値を返す特定のデータ変換やカスタム フィルターの働きを持ったメソッドを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="195e4-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="195e4-106">このようなメソッドには、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A>、<xref:System.Linq.Enumerable.Reverse%2A> があります。</span><span class="sxs-lookup"><span data-stu-id="195e4-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="195e4-107"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスを拡張すると、列挙可能なコレクションにカスタム メソッドを適用できます。</span><span class="sxs-lookup"><span data-stu-id="195e4-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="195e4-108">詳細については、「[拡張メソッド](../../classes-and-structs/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="195e4-108">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="195e4-109">集計メソッドの追加</span><span class="sxs-lookup"><span data-stu-id="195e4-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="195e4-110">集計メソッドは、一連の値から単一の値を計算するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="195e4-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="195e4-111">LINQ は、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Max%2A> などの集計メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="195e4-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="195e4-112"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスに拡張メソッドを追加することで、独自の集計メソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="195e4-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="195e4-113">次のコード例は、`double` 型の一連の数値から中央値を求める `Median` という拡張メソッドの作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="195e4-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        var countOfElementsInTheSet = source?.Count() ?? 0;

        if (countOfElementsInTheSet == 0)
        {
            throw new InvalidOperationException("Cannot compute median for a null or empty set.");
        }

        var sortedList = (from number in source
                         orderby number
                         select number).ToList();

        int itemIndex = countOfElementsInTheSet / 2;

        if (countOfElementsInTheSet % 2 == 0)
        {
            // Even number of items.
            return (sortedList[itemIndex] + sortedList[itemIndex - 1]) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList[itemIndex];
        }
    }
}
```

<span data-ttu-id="195e4-114">この拡張メソッドは、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスにある他の集計メソッドを呼び出すときと同じように、列挙可能な任意のコレクションに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="195e4-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="195e4-115">`double` 型の配列に対して `Median` メソッドを使用する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="195e4-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
*/
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="195e4-116">さまざまな型を受け取るために集計メソッドをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="195e4-116">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="195e4-117">集計メソッドでさまざまな型を受け取るように、集計メソッドをオーバーロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="195e4-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="195e4-118">その標準的な方法として、型ごとにオーバーロードを作成します。</span><span class="sxs-lookup"><span data-stu-id="195e4-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="195e4-119">または、ジェネリック型を受け取り、デリゲートを使って特定の型に変換するオーバーロードを作成する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="195e4-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="195e4-120">その両方の方法を組み合わせることもできます。</span><span class="sxs-lookup"><span data-stu-id="195e4-120">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="195e4-121">型ごとにオーバーロードを作成するには</span><span class="sxs-lookup"><span data-stu-id="195e4-121">To create an overload for each type</span></span>

<span data-ttu-id="195e4-122">サポート予定の型ごとに固有のオーバーロードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="195e4-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="195e4-123">次のコード例では、`integer` 型の `Median` メソッドのオーバーロードを示します。</span><span class="sxs-lookup"><span data-stu-id="195e4-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="195e4-124">これで、次のコードに示すように、`integer` 型と `double` 型の両方に対して、`Median` のオーバーロードを呼び出すことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="195e4-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
int[] numbers2 = { 1, 2, 3, 4, 5 };

var query2 = numbers2.Median();

Console.WriteLine("int: Median = " + query2);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
 Integer: Median = 3
*/
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="195e4-125">ジェネリック オーバーロードを作成するには</span><span class="sxs-lookup"><span data-stu-id="195e4-125">To create a generic overload</span></span>

<span data-ttu-id="195e4-126">一連のジェネリック オブジェクトを受け取るオーバーロードを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="195e4-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="195e4-127">このオーバーロードは、デリゲートをパラメーターとして受け取り、ジェネリック型の一連のオブジェクトを特定の型に変換します。</span><span class="sxs-lookup"><span data-stu-id="195e4-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="195e4-128">次のコードは、<xref:System.Func%602> デリゲートをパラメーターとして受け取る `Median` メソッドのオーバーロードを示しています。</span><span class="sxs-lookup"><span data-stu-id="195e4-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="195e4-129">このデリゲートは、ジェネリック型 T のオブジェクトを受け取り、`double` 型のオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="195e4-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="195e4-130">これで、任意の型の一連のオブジェクトに対して `Median` メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="195e4-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="195e4-131">型に固有のメソッド オーバーロードがない場合は、デリゲート パラメーターを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="195e4-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="195e4-132">この目的で、C# ではラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="195e4-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="195e4-133">また、Visual Basic に限り、メソッド呼び出しの代わりに `Aggregate` 句または `Group By` 句を使用した場合、その句のスコープにある任意の値または式を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="195e4-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="195e4-134">次のコード例では、整数の配列と文字列の配列に対して `Median` メソッドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="195e4-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="195e4-135">文字列の場合は、配列に格納されている文字列の長さの中央値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="195e4-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="195e4-136">この例は、それぞれのケースについて、`Median` メソッドに <xref:System.Func%602> デリゲート パラメーターを渡す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="195e4-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```csharp
int[] numbers3 = { 1, 2, 3, 4, 5 };

/*
  You can use the num=>num lambda expression as a parameter for the Median method
  so that the compiler will implicitly convert its value to double.
  If there is no implicit conversion, the compiler will display an error message.
*/

var query3 = numbers3.Median(num => num);

Console.WriteLine("int: Median = " + query3);

string[] numbers4 = { "one", "two", "three", "four", "five" };

// With the generic overload, you can also use numeric properties of objects.

var query4 = numbers4.Median(str => str.Length);

Console.WriteLine("String: Median = " + query4);

/*
 This code produces the following output:

 Integer: Median = 3
 String: Median = 4
*/
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="195e4-137">コレクションを返すメソッドを追加する</span><span class="sxs-lookup"><span data-stu-id="195e4-137">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="195e4-138"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスは、一連の値を返すカスタム クエリ メソッドを追加することで拡張できます。</span><span class="sxs-lookup"><span data-stu-id="195e4-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="195e4-139">その場合、メソッドで型 <xref:System.Collections.Generic.IEnumerable%601> のコレクションを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="195e4-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="195e4-140">このようなメソッドを使用すると、一連の値にフィルターまたはデータ変換を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="195e4-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="195e4-141">次の例では、コレクション内の最初の要素から 1 つおきに要素を返す `AlternateElements` という名前の拡張メソッドを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="195e4-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```csharp
// Extension method for the IEnumerable<T> interface.
// The method returns every other element of a sequence.

public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)
{
    List<T> list = new List<T>();

    int i = 0;

    foreach (var element in source)
    {
        if (i % 2 == 0)
        {
            list.Add(element);
        }

        i++;
    }

    return list;
}
```

<span data-ttu-id="195e4-142">この拡張メソッドは、次のコードに示すとおり、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスにある他のメソッドを呼び出すときと同じように、列挙可能な任意のコレクションに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="195e4-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```csharp
string[] strings = { "a", "b", "c", "d", "e" };

var query = strings.AlternateElements();

foreach (var element in query)
{
    Console.WriteLine(element);
}
/*
 This code produces the following output:

 a
 c
 e
*/
```

## <a name="see-also"></a><span data-ttu-id="195e4-143">参照</span><span class="sxs-lookup"><span data-stu-id="195e4-143">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="195e4-144">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="195e4-144">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
