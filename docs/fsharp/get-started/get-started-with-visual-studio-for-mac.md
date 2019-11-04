---
title: Visual Studio for Mac で F＃ をはじめよう
description: を Visual Studio for Mac と共F#に使用する方法について説明します。
ms.date: 07/03/2018
ms.openlocfilehash: d3604178f93cf17d21f25b09084be7e7977378b5
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082979"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="2030e-103">Visual Studio for Mac で F＃ をはじめよう</span><span class="sxs-lookup"><span data-stu-id="2030e-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="2030e-104">F＃ および Visual F＃ ツールは、Visual Studio for Mac IDE でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2030e-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="2030e-105">[Visual Studio for Mac がインストール](install-fsharp.md#install-f-with-visual-studio-for-mac) されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2030e-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="2030e-106">コンソールアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="2030e-106">Creating a console application</span></span>

<span data-ttu-id="2030e-107">コンソールアプリケーションは、Visual Studio for Mac の最も基本的なプロジェクトの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="2030e-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="2030e-108">これを行う方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2030e-108">Here's how to do it.</span></span>  <span data-ttu-id="2030e-109">Visual Studio for Mac を開いて、次を実行します。</span><span class="sxs-lookup"><span data-stu-id="2030e-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="2030e-110">**[ファイル]** メニューの **[新しいソリューション]** をポイントします。</span><span class="sxs-lookup"><span data-stu-id="2030e-110">On the **File** menu, point to **New Solution**.</span></span>

2. <span data-ttu-id="2030e-111">[新しいプロジェクト] ダイアログには、コンソールアプリケーションに2つの異なるテンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="2030e-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="2030e-112">.NET Framework をターゲットとする > .NET の下に1つあります。</span><span class="sxs-lookup"><span data-stu-id="2030e-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="2030e-113">その他のテンプレートは .net core > アプリの下にあり、.NET Core を対象としています。</span><span class="sxs-lookup"><span data-stu-id="2030e-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="2030e-114">どちらのテンプレートも、この記事の目的で機能します。</span><span class="sxs-lookup"><span data-stu-id="2030e-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="2030e-115">コンソール アプリを変更 (C#) F# に必要な場合。</span><span class="sxs-lookup"><span data-stu-id="2030e-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="2030e-116">**[次へ]** ボタンをクリックして先に進みます。</span><span class="sxs-lookup"><span data-stu-id="2030e-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="2030e-117">プロジェクトに名前を付け、アプリに必要なオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="2030e-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="2030e-118">プレビュー ウィンドウには、選択したオプションに基づいて作成されるディレクトリ構造が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2030e-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="2030e-119">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2030e-119">Click **Create**.</span></span>  <span data-ttu-id="2030e-120">ソリューション エクスプローラーに F# プロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2030e-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="2030e-121">コードを記述する</span><span class="sxs-lookup"><span data-stu-id="2030e-121">Writing your code</span></span>

<span data-ttu-id="2030e-122">まずはコードを記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="2030e-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="2030e-123">`Program.fs` ファイルが開いていることを確認し、その内容を次のものに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2030e-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="2030e-124">前のコードサンプルでは、`x` という名前の入力を受け取り、それを単独で乗算する関数 `square` が定義されています。</span><span class="sxs-lookup"><span data-stu-id="2030e-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="2030e-125">F# は[型の推定](../language-reference/type-inference.md)を行うので、`x` の型を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2030e-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="2030e-126">F# コンパイラは乗算が有効な型を認識し、`square` が呼び出される方法に基づいて `x` に型を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2030e-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="2030e-127">マウス ポインターを `square` に合わせると、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="2030e-127">If you hover over `square`, you should see the following:</span></span>

```console
val square: x:int -> int
```

<span data-ttu-id="2030e-128">これは、関数の型シグネチャと呼ばれるものです。</span><span class="sxs-lookup"><span data-stu-id="2030e-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="2030e-129">次のように読み取ることができます。「square は、x という名前の整数を受け取り、整数を生成する関数」と読むことができます。</span><span class="sxs-lookup"><span data-stu-id="2030e-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="2030e-130">コンパイラがこの時点では`square` に`int` 型を与えていることに注意してください。これは乗算が *あらゆる* 型に一般的なのではなく、ある閉じた型の集合に一般的であるためです</span><span class="sxs-lookup"><span data-stu-id="2030e-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="2030e-131">F# コンパイラはこの時点で`int` を選択しましたが、例えば `float` といった別の型で `square` を呼び出すと、型シグネチャを調整します。</span><span class="sxs-lookup"><span data-stu-id="2030e-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="2030e-132">別の関数 `main` は、`EntryPoint` 属性で修飾され、プログラムの実行をそこから開始することを F# コンパイラに指示するために定義されています。</span><span class="sxs-lookup"><span data-stu-id="2030e-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="2030e-133">他の [C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)と同じ規則に従い、コマンド ライン引数をこの関数に渡し、整数値 (通常は `0`) を返す事ができます。</span><span class="sxs-lookup"><span data-stu-id="2030e-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="2030e-134">この関数の中で、`square` 関数を引数 `12` で呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2030e-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="2030e-135">次に F# コンパイラは `square` の型に `int -> int` (つまり `int` を受け取り `int` を生成する関数) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2030e-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="2030e-136">`printfn` 関数は、C スタイルのプログラミング言語に似たフォーマット文字列と、フォーマット文字列にあるパラメータに対応するパラメータを用いて結果と改行を出力する出力関数です。</span><span class="sxs-lookup"><span data-stu-id="2030e-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="2030e-137">コードを実行する</span><span class="sxs-lookup"><span data-stu-id="2030e-137">Running your code</span></span>

<span data-ttu-id="2030e-138">上部のメニューから **[実行]** をクリックし、 **[デバッグなしで開始]** をクリックして、コードを実行し、結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="2030e-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="2030e-139">これにより、デバッグなしでプログラムが実行され、結果を確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2030e-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="2030e-140">Visual Studio for Mac からコンソール ウィンドウがポップアップされ、以下が出力されます。</span><span class="sxs-lookup"><span data-stu-id="2030e-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="2030e-141">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="2030e-141">Congratulations!</span></span>  <span data-ttu-id="2030e-142">Visual Studio for Mac で初めての F# プロジェクトを作成し、関数の呼び出し結果を出力する F# 関数を作成し、プロジェクトを実行して結果を確認しました。</span><span class="sxs-lookup"><span data-stu-id="2030e-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="2030e-143">F# インタラクティブを使用する</span><span class="sxs-lookup"><span data-stu-id="2030e-143">Using F# Interactive</span></span>

<span data-ttu-id="2030e-144">Visual Studio for Mac の Visual F# ツールの最も優れた機能の 1 つは、F# インタラクティブ ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2030e-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="2030e-145">この機能を使用すると、コードを呼び出して結果を確認するという事がインタラクティブに実行できるプロセスにコードを送信できます。</span><span class="sxs-lookup"><span data-stu-id="2030e-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="2030e-146">使用を開始するには、 `square`コードで定義されている関数を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="2030e-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="2030e-147">次に、トップレベルメニューの **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2030e-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="2030e-148">次に選択**選択範囲を F# Interactive に送信**します。</span><span class="sxs-lookup"><span data-stu-id="2030e-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="2030e-149">これには、F# 対話型ウィンドウで、コードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="2030e-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="2030e-150">または、選択範囲を右クリックし、選択**選択範囲を F# Interactive に送信**します。</span><span class="sxs-lookup"><span data-stu-id="2030e-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="2030e-151">F#対話型ウィンドウが表示され、次のようなウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2030e-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```console
>

val square : x:int -> int

>
```

<span data-ttu-id="2030e-152">前に `square` 関数をポイントしたときに見たのと同じ関数シグネチャが表示されています。</span><span class="sxs-lookup"><span data-stu-id="2030e-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="2030e-153">`square`が F# Interactive プロセスで定義されるようになったため、さまざまな値を呼び出すことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="2030e-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="2030e-154">関数が実行され、結果が `it` という新しい名前にバインドされ、`it` の型と値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2030e-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="2030e-155">各行は、`;;` で終了する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2030e-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="2030e-156">これによって関数呼び出しが完了した事を F# Interactive が認識します。</span><span class="sxs-lookup"><span data-stu-id="2030e-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="2030e-157">F# Interactive で新しい関数を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="2030e-157">You can also define new functions in F# Interactive:</span></span>

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="2030e-158">上のでは新しい関数`isOdd`が定義されています。これはを`int`受け取り、それが奇数かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="2030e-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="2030e-159">この関数を呼び出すと、異なる入力で何が返されるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2030e-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="2030e-160">関数呼び出しの中で関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2030e-160">You can call functions within function calls:</span></span>

```console
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="2030e-161">[パイプ転送演算子](../language-reference/symbol-and-operator-reference/index.md)を使用して、値を次の2つの関数にパイプライン処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="2030e-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="2030e-162">パイプ転送演算子などの詳細については、以降のチュートリアルで説明します。</span><span class="sxs-lookup"><span data-stu-id="2030e-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="2030e-163">ここでは、F# Interactive でできることの一部を取り上げています。</span><span class="sxs-lookup"><span data-stu-id="2030e-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="2030e-164">詳細については、[F# を使用した対話型プログラミング](../tutorials/fsharp-interactive/index.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2030e-164">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2030e-165">次のステップ</span><span class="sxs-lookup"><span data-stu-id="2030e-165">Next steps</span></span>

<span data-ttu-id="2030e-166">まだ確認していない場合は、F# 言語のコア機能の一部をカバーしている [F# のツアー](../tour.md)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2030e-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="2030e-167">F# の一部機能の概要を説明し、Visual Studio for Mac にコピーして実行できる十分なコード サンプルを提供します。</span><span class="sxs-lookup"><span data-stu-id="2030e-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="2030e-168">[F# ガイド](../index.md)で紹介されている、優れた外部リソースもあります。</span><span class="sxs-lookup"><span data-stu-id="2030e-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2030e-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="2030e-169">See also</span></span>

- [<span data-ttu-id="2030e-170">Visual F#</span><span class="sxs-lookup"><span data-stu-id="2030e-170">Visual F#</span></span>](../index.md)
- [<span data-ttu-id="2030e-171">F# のツアー</span><span class="sxs-lookup"><span data-stu-id="2030e-171">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="2030e-172">F#言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="2030e-172">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="2030e-173">型の推論</span><span class="sxs-lookup"><span data-stu-id="2030e-173">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="2030e-174">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="2030e-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
