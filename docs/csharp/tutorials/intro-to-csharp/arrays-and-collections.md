---
title: コレクションでの作業 - C# チュートリアルの概要
description: このチュートリアルでは、リスト コレクションについて確認して C# を学習します。
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 25d20de2eae8ad1f544fa17553c173a6141ae464
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156690"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="bd36c-103">リスト型を使用したデータ コレクションの管理について説明します</span><span class="sxs-lookup"><span data-stu-id="bd36c-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="bd36c-104">このチュートリアルでは、C# 言語の概要と <xref:System.Collections.Generic.List%601> クラスの基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="bd36c-105">このチュートリアルでは、開発用に使用できるマシンがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="bd36c-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="bd36c-106">Windows、Linux、または macOS 上でローカルの開発環境を設定する手順については、.NET チュートリアル [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) (10 分で Hello World) に記載されています。</span><span class="sxs-lookup"><span data-stu-id="bd36c-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="bd36c-107">使用するコマンドの概要については、詳細な情報へのリンクが掲載されている[開発ツールに対する理解を深める](local-environment.md)方法に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bd36c-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="bd36c-108">基本のリストの例</span><span class="sxs-lookup"><span data-stu-id="bd36c-108">A basic list example</span></span>

<span data-ttu-id="bd36c-109">*list-tutorial* という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="bd36c-110">それを現在のディレクトリとし、`dotnet new console` を実行します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="bd36c-111">好みのエディターで *Program.cs* を開き、既存のコードを次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

<span data-ttu-id="bd36c-112">`<name>` をユーザー名で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="bd36c-113">*Program.cs* を保存します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-113">Save *Program.cs*.</span></span> <span data-ttu-id="bd36c-114">コンソール ウィンドウに「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="bd36c-115">文字列のリストを作成し、そのリストに 3 つの名前を追加し、それらの名前をすべて大文字で出力しました。</span><span class="sxs-lookup"><span data-stu-id="bd36c-115">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="bd36c-116">先のチュートリアルで学習した概念を使用して、リストをループしています。</span><span class="sxs-lookup"><span data-stu-id="bd36c-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="bd36c-117">名前を表示するコードは、[文字列補間](../../language-reference/tokens/interpolated.md)機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="bd36c-118">`string` の前に文字 `$` を配置すると、文字列宣言に C# コードを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="bd36c-119">実際の文字列は、生成する値でその C# コードを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="bd36c-120">この例では、`{name.ToUpper()}` メソッドを呼び出したため、文字列は <xref:System.String.ToUpper%2A> をそれぞれの名前に置き換え、文字を大文字に変換しています。</span><span class="sxs-lookup"><span data-stu-id="bd36c-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="bd36c-121">続けて確認していきましょう。</span><span class="sxs-lookup"><span data-stu-id="bd36c-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="bd36c-122">リスト コンテンツを変更する</span><span class="sxs-lookup"><span data-stu-id="bd36c-122">Modify list contents</span></span>

<span data-ttu-id="bd36c-123">作成したコレクションは <xref:System.Collections.Generic.List%601> 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="bd36c-124">この型は、要素のシーケンスを格納します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-124">This type stores sequences of elements.</span></span> <span data-ttu-id="bd36c-125">要素の型を山かっこの内側で指定します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="bd36c-126">この <xref:System.Collections.Generic.List%601> 型の重要な点は増減が可能で、要素を追加したり削除したりできることです。</span><span class="sxs-lookup"><span data-stu-id="bd36c-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="bd36c-127">`}` メソッドの閉じかっこ `Main` の前に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-127">Add this code before the closing `}` in the `Main` method:</span></span>

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="bd36c-128">さらに 2 つの名前をリストの末尾に追加しました。</span><span class="sxs-lookup"><span data-stu-id="bd36c-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="bd36c-129">また、1 つを削除しました。</span><span class="sxs-lookup"><span data-stu-id="bd36c-129">You've also removed one as well.</span></span> <span data-ttu-id="bd36c-130">ファイルを保存し、「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="bd36c-131"><xref:System.Collections.Generic.List%601> を使用すると、**インデックス**でも個々の項目を参照できます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="bd36c-132">リスト名に続く `[` と `]` のトークンの間にインデックスを記述します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="bd36c-133">C# では、初めのインデックスには 0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="bd36c-134">追加したコードのすぐ下に次のコードを追加して試します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="bd36c-135">リストの末尾を越えてインデックスにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bd36c-135">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="bd36c-136">インデックスは 0 から始まるため、有効なインデックスの最大値はリスト内の項目の数より 1 小さくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bd36c-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="bd36c-137"><xref:System.Collections.Generic.List%601.Count%2A> プロパティを使用すれば、リストの長さを確認できます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="bd36c-138">次のコードを Main メソッドの末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="bd36c-139">ファイルを保存し、もう一度「`dotnet run`」と入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="bd36c-140">リストを検索して並び替える</span><span class="sxs-lookup"><span data-stu-id="bd36c-140">Search and sort lists</span></span>

<span data-ttu-id="bd36c-141">サンプルでは比較的小さいリストを使用していますが、ご利用のアプリケーションでは、より多くの (場合によっては何千もの) 要素が含まれるリストを作成することもよくあるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="bd36c-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="bd36c-142">そうした大規模なコレクションの中から要素を見つけるには、別々の項目をリストで検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd36c-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="bd36c-143"><xref:System.Collections.Generic.List%601.IndexOf%2A> メソッドは項目を検索し、その項目のインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="bd36c-144">`Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-144">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

<span data-ttu-id="bd36c-145">同じように、リスト内の項目を並び替えできます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-145">The items in your list can be sorted as well.</span></span> <span data-ttu-id="bd36c-146"><xref:System.Collections.Generic.List%601.Sort%2A> メソッドは、リスト内のすべての項目を正規順序 (文字列の場合はアルファベット順) で並び替えます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-146">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="bd36c-147">`Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-147">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="bd36c-148">ファイルを保存し、「`dotnet run`」と入力してこの最新バージョンを試します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-148">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="bd36c-149">次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="bd36c-149">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="bd36c-150">移動しておくと、新しい例で作業を開始するときに楽になります。</span><span class="sxs-lookup"><span data-stu-id="bd36c-150">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="bd36c-151">`Main` メソッドの名前を `WorkingWithStrings` に変更し、`Main` を呼び出す新しい `WorkingWithStrings` メソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-151">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="bd36c-152">完成したコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="bd36c-152">When you have finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");
            }

            index = names.IndexOf("Not Found");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");

            }

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="bd36c-153">その他の型のリスト</span><span class="sxs-lookup"><span data-stu-id="bd36c-153">Lists of other types</span></span>

<span data-ttu-id="bd36c-154">ここまでは、リスト内で `string` 型を使用してきました。</span><span class="sxs-lookup"><span data-stu-id="bd36c-154">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="bd36c-155">別の型を使用して <xref:System.Collections.Generic.List%601> を作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="bd36c-155">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="bd36c-156">数値のセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-156">Let's build a set of numbers.</span></span>

<span data-ttu-id="bd36c-157">新しい `Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-157">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="bd36c-158">これにより整数のリストが作成され、最初の 2 つの整数が値 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-158">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="bd36c-159">これらは、数列の 1 つである*フィボナッチ数列*の最初の 2 つの値です。</span><span class="sxs-lookup"><span data-stu-id="bd36c-159">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="bd36c-160">次のフィボナッチ数はそれぞれ、その直前の 2 つの数値の合計を取得することによって得られます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-160">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="bd36c-161">このコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-161">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="bd36c-162">ファイルを保存し、「`dotnet run`」と入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-162">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="bd36c-163">このセクションにだけ集中したいときは、`WorkingWithStrings();` を呼び出すコードはコメント アウトしてかまいません。</span><span class="sxs-lookup"><span data-stu-id="bd36c-163">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="bd36c-164">`/` のように、呼び出しの前に `// WorkingWithStrings();` 文字を 2 つ記述します。</span><span class="sxs-lookup"><span data-stu-id="bd36c-164">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="bd36c-165">課題</span><span class="sxs-lookup"><span data-stu-id="bd36c-165">Challenge</span></span>

<span data-ttu-id="bd36c-166">このレッスンと以前のレッスンの中から、いくつかの概念を理解できているかどうかを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="bd36c-166">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="bd36c-167">ここまでフィボナッチ数を使用して作成してきたコードを使ってください。</span><span class="sxs-lookup"><span data-stu-id="bd36c-167">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="bd36c-168">シーケンスの最初の 20 個の数を生成するコードを記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="bd36c-168">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="bd36c-169">(ヒント: フィボナッチ数の 20 番目の数は 6765 です。)</span><span class="sxs-lookup"><span data-stu-id="bd36c-169">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="bd36c-170">課題完了</span><span class="sxs-lookup"><span data-stu-id="bd36c-170">Complete challenge</span></span>

<span data-ttu-id="bd36c-171">[GitHub にある完成したサンプル コードを表示すること](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)で、ソリューションの例を確認できます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="bd36c-172">ループの繰り返しごとに、リストの最後の 2 つの整数を取得して合計し、その値をリストに追加しています。</span><span class="sxs-lookup"><span data-stu-id="bd36c-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="bd36c-173">このループは、20 個の項目がリストに追加されるまで繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="bd36c-174">おつかれさまでした。リストについてのチュートリアルはこれで終了です。</span><span class="sxs-lookup"><span data-stu-id="bd36c-174">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="bd36c-175">続けて独自の開発環境で[クラスの概要](introduction-to-classes.md)のチュートリアルに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-175">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="bd36c-176">`List` 型の使用方法の詳細については、[.NET ガイド](../../../standard/index.md)の[コレクション](../../../standard/collections/index.md)に関するトピックで学習できます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-176">You can learn more about working with the `List` type in the [.NET Guide](../../../standard/index.md) topic on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="bd36c-177">その他の多くのコレクション型についても学習できます。</span><span class="sxs-lookup"><span data-stu-id="bd36c-177">You'll also learn about many other collection types.</span></span>
