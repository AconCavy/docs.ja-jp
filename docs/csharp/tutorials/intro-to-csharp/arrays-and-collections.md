---
title: コレクションでの作業 - C# チュートリアルの概要
description: このチュートリアルでは、リスト コレクションについて確認して C# を学習します。
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: e2282df21420630634911e07f4fb3b94f34a792b
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414684"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="a3846-103">リスト型を使用したデータ コレクションの管理について説明します</span><span class="sxs-lookup"><span data-stu-id="a3846-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="a3846-104">このチュートリアルでは、C# 言語の概要と <xref:System.Collections.Generic.List%601> クラスの基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="a3846-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="a3846-105">このチュートリアルでは、開発用に使用できるマシンがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="a3846-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="a3846-106">Windows、Linux、または macOS 上でローカルの開発環境を設定する手順については、.NET チュートリアル [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) (10 分で Hello World) に記載されています。</span><span class="sxs-lookup"><span data-stu-id="a3846-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="a3846-107">使用するコマンドの概要については、詳細な情報へのリンクが掲載されている[開発ツールに対する理解を深める](local-environment.md)方法に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a3846-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="a3846-108">基本のリストの例</span><span class="sxs-lookup"><span data-stu-id="a3846-108">A basic list example</span></span>

<span data-ttu-id="a3846-109">*list-tutorial* という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3846-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="a3846-110">それを現在のディレクトリとし、`dotnet new console` を実行します。</span><span class="sxs-lookup"><span data-stu-id="a3846-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="a3846-111">好みのエディターで *Program.cs* を開き、既存のコードを次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a3846-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="a3846-112">`<name>` をユーザー名で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a3846-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="a3846-113">*Program.cs* を保存します。</span><span class="sxs-lookup"><span data-stu-id="a3846-113">Save *Program.cs*.</span></span> <span data-ttu-id="a3846-114">コンソール ウィンドウに「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="a3846-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="a3846-115">文字列のリストを作成し、そのリストに 3 つの名前を追加し、それらの名前をすべて大文字で出力しました。</span><span class="sxs-lookup"><span data-stu-id="a3846-115">You've created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="a3846-116">先のチュートリアルで学習した概念を使用して、リストをループしています。</span><span class="sxs-lookup"><span data-stu-id="a3846-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="a3846-117">名前を表示するコードは、[文字列補間](../../language-reference/tokens/interpolated.md)機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3846-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="a3846-118">`string` の前に文字 `$` を配置すると、文字列宣言に C# コードを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="a3846-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="a3846-119">実際の文字列は、生成する値でその C# コードを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a3846-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="a3846-120">この例では、<xref:System.String.ToUpper%2A> メソッドを呼び出したため、文字列は `{name.ToUpper()}` をそれぞれの名前に置き換え、文字を大文字に変換しています。</span><span class="sxs-lookup"><span data-stu-id="a3846-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="a3846-121">続けて確認していきましょう。</span><span class="sxs-lookup"><span data-stu-id="a3846-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="a3846-122">リスト コンテンツを変更する</span><span class="sxs-lookup"><span data-stu-id="a3846-122">Modify list contents</span></span>

<span data-ttu-id="a3846-123">作成したコレクションは <xref:System.Collections.Generic.List%601> 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3846-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="a3846-124">この型は、要素のシーケンスを格納します。</span><span class="sxs-lookup"><span data-stu-id="a3846-124">This type stores sequences of elements.</span></span> <span data-ttu-id="a3846-125">要素の型を山かっこの内側で指定します。</span><span class="sxs-lookup"><span data-stu-id="a3846-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="a3846-126">この <xref:System.Collections.Generic.List%601> 型の重要な点は増減が可能で、要素を追加したり削除したりできることです。</span><span class="sxs-lookup"><span data-stu-id="a3846-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="a3846-127">`Main` メソッドの閉じかっこ `}` の前に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3846-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="a3846-128">さらに 2 つの名前をリストの末尾に追加しました。</span><span class="sxs-lookup"><span data-stu-id="a3846-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="a3846-129">また、1 つを削除しました。</span><span class="sxs-lookup"><span data-stu-id="a3846-129">You've also removed one as well.</span></span> <span data-ttu-id="a3846-130">ファイルを保存し、「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="a3846-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="a3846-131"><xref:System.Collections.Generic.List%601> を使用すると、**インデックス**でも個々の項目を参照できます。</span><span class="sxs-lookup"><span data-stu-id="a3846-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="a3846-132">リスト名に続く `[` と `]` のトークンの間にインデックスを記述します。</span><span class="sxs-lookup"><span data-stu-id="a3846-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="a3846-133">C# では、初めのインデックスには 0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3846-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="a3846-134">追加したコードのすぐ下に次のコードを追加して試します。</span><span class="sxs-lookup"><span data-stu-id="a3846-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="a3846-135">リストの末尾を越えてインデックスにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a3846-135">You can't access an index beyond the end of the list.</span></span> <span data-ttu-id="a3846-136">インデックスは 0 から始まるため、有効なインデックスの最大値はリスト内の項目の数より 1 小さくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a3846-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="a3846-137"><xref:System.Collections.Generic.List%601.Count%2A> プロパティを使用すれば、リストの長さを確認できます。</span><span class="sxs-lookup"><span data-stu-id="a3846-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="a3846-138">次のコードを Main メソッドの末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="a3846-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="a3846-139">ファイルを保存し、もう一度「`dotnet run`」と入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="a3846-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="a3846-140">リストを検索して並び替える</span><span class="sxs-lookup"><span data-stu-id="a3846-140">Search and sort lists</span></span>

<span data-ttu-id="a3846-141">サンプルでは比較的小さいリストを使用していますが、ご利用のアプリケーションでは、より多くの (場合によっては何千もの) 要素が含まれるリストを作成することもよくあるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="a3846-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="a3846-142">そうした大規模なコレクションの中から要素を見つけるには、別々の項目をリストで検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3846-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="a3846-143"><xref:System.Collections.Generic.List%601.IndexOf%2A> メソッドは項目を検索し、その項目のインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="a3846-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="a3846-144">項目がリストにない場合、`IndexOf` は `-1` を返します。</span><span class="sxs-lookup"><span data-stu-id="a3846-144">If the item isn't in the list, `IndexOf` returns `-1`.</span></span> <span data-ttu-id="a3846-145">`Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3846-145">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="a3846-146">同じように、リスト内の項目を並び替えできます。</span><span class="sxs-lookup"><span data-stu-id="a3846-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="a3846-147"><xref:System.Collections.Generic.List%601.Sort%2A> メソッドは、リスト内のすべての項目を正規順序 (文字列の場合はアルファベット順) で並び替えます。</span><span class="sxs-lookup"><span data-stu-id="a3846-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically for strings).</span></span> <span data-ttu-id="a3846-148">`Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3846-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="a3846-149">ファイルを保存し、「`dotnet run`」と入力してこの最新バージョンを試します。</span><span class="sxs-lookup"><span data-stu-id="a3846-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="a3846-150">次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="a3846-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="a3846-151">移動しておくと、新しい例で作業を開始するときに楽になります。</span><span class="sxs-lookup"><span data-stu-id="a3846-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="a3846-152">`Main` メソッドの名前を `WorkingWithStrings` に変更し、`WorkingWithStrings` を呼び出す新しい `Main` メソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="a3846-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="a3846-153">完成したコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a3846-153">When you've finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="a3846-154">その他の型のリスト</span><span class="sxs-lookup"><span data-stu-id="a3846-154">Lists of other types</span></span>

<span data-ttu-id="a3846-155">ここまでは、リスト内で `string` 型を使用してきました。</span><span class="sxs-lookup"><span data-stu-id="a3846-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="a3846-156">別の型を使用して <xref:System.Collections.Generic.List%601> を作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="a3846-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="a3846-157">数値のセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3846-157">Let's build a set of numbers.</span></span>

<span data-ttu-id="a3846-158">新しい `Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3846-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="a3846-159">これにより整数のリストが作成され、最初の 2 つの整数が値 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a3846-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="a3846-160">これらは、数列の 1 つである*フィボナッチ数列*の最初の 2 つの値です。</span><span class="sxs-lookup"><span data-stu-id="a3846-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="a3846-161">次のフィボナッチ数はそれぞれ、その直前の 2 つの数値の合計を取得することによって得られます。</span><span class="sxs-lookup"><span data-stu-id="a3846-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="a3846-162">このコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3846-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="a3846-163">ファイルを保存し、「`dotnet run`」と入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="a3846-163">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="a3846-164">このセクションにだけ集中したいときは、`WorkingWithStrings();` を呼び出すコードはコメント アウトしてかまいません。</span><span class="sxs-lookup"><span data-stu-id="a3846-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="a3846-165">`// WorkingWithStrings();` のように、呼び出しの前に `/` 文字を 2 つ記述します。</span><span class="sxs-lookup"><span data-stu-id="a3846-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="a3846-166">課題</span><span class="sxs-lookup"><span data-stu-id="a3846-166">Challenge</span></span>

<span data-ttu-id="a3846-167">このレッスンと以前のレッスンの中から、いくつかの概念を理解できているかどうかを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="a3846-167">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="a3846-168">ここまでフィボナッチ数を使用して作成してきたコードを使ってください。</span><span class="sxs-lookup"><span data-stu-id="a3846-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="a3846-169">シーケンスの最初の 20 個の数を生成するコードを記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="a3846-169">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="a3846-170">(ヒント: フィボナッチ数の 20 番目の数は 6765 です。)</span><span class="sxs-lookup"><span data-stu-id="a3846-170">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="a3846-171">課題完了</span><span class="sxs-lookup"><span data-stu-id="a3846-171">Complete challenge</span></span>

<span data-ttu-id="a3846-172">[GitHub にある完成したサンプル コードを表示すること](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)で、ソリューションの例を確認できます。</span><span class="sxs-lookup"><span data-stu-id="a3846-172">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="a3846-173">ループの繰り返しごとに、リストの最後の 2 つの整数を取得して合計し、その値をリストに追加しています。</span><span class="sxs-lookup"><span data-stu-id="a3846-173">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="a3846-174">このループは、20 個の項目がリストに追加されるまで繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="a3846-174">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="a3846-175">おつかれさまでした。リストについてのチュートリアルはこれで終了です。</span><span class="sxs-lookup"><span data-stu-id="a3846-175">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="a3846-176">続けて独自の開発環境で[クラスの概要](introduction-to-classes.md)のチュートリアルに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="a3846-176">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="a3846-177">`List` 型の使用方法の詳細については、[コレクション](../../../standard/collections/index.md)に関する .NET 基礎の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3846-177">You can learn more about working with the `List` type in the .NET fundamentals article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="a3846-178">その他の多くのコレクション型についても学習できます。</span><span class="sxs-lookup"><span data-stu-id="a3846-178">You'll also learn about many other collection types.</span></span>
