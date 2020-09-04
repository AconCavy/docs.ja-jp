---
title: Visual Studio Code を使用して .NET Core コンソール アプリケーションを作成する
description: Visual Studio Code と .NET Core CLI を使用して .NET Core コンソール アプリケーションを作成する方法について説明します。
ms.date: 05/22/2020
ms.openlocfilehash: e936c23d8525e42a9d2781cc680067c9da2ce42f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811927"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="979e4-103">チュートリアル: Visual Studio Code を使用して .NET Core コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="979e4-103">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="979e4-104">このチュートリアルでは、Visual Studio Code と .NET Core CLI を使用して .NET Core コンソール アプリケーションを作成して実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="979e4-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="979e4-105">プロジェクトの作成、コンパイル、実行などのプロジェクト タスクは、.NET Core CLI を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="979e4-105">Project tasks, such as creating, compiling, and running a project are done by using the .NET Core CLI.</span></span> <span data-ttu-id="979e4-106">必要に応じて、別のコード エディターを使用してこのチュートリアルに従い、ターミナルでコマンドを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="979e4-106">You can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="979e4-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="979e4-107">Prerequisites</span></span>

1. <span data-ttu-id="979e4-108">[C# 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)がインストールされている [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="979e4-108">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="979e4-109">Visual Studio Code に拡張機能をインストールする方法については、[VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="979e4-109">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="979e4-110">[.Net Core 3.1 SDK 以降](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="979e4-110">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="979e4-111">アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="979e4-111">Create the app</span></span>

<span data-ttu-id="979e4-112">"HelloWorld" という名前の .NET Core コンソール アプリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="979e4-112">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="979e4-113">Visual Studio Code を開始します。</span><span class="sxs-lookup"><span data-stu-id="979e4-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="979e4-114">メイン メニューから **[ファイル]**  >  **[フォルダーを開く]** (macOS では **[ファイル]**  >  **[開く...]** ) の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="979e4-114">Select **File** > **Open Folder** (**File** > **Open...** on macOS) from the main menu.</span></span>

1. <span data-ttu-id="979e4-115">**[フォルダーを開く]** ダイアログで、*HelloWorld* フォルダーを作成し、 **[フォルダーの選択]** (macOS では **[開く]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="979e4-115">In the **Open Folder** dialog, create a *HelloWorld* folder and click **Select Folder** (**Open** on macOS).</span></span>

   <span data-ttu-id="979e4-116">フォルダー名は既定でプロジェクト名と名前空間名になります。</span><span class="sxs-lookup"><span data-stu-id="979e4-116">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="979e4-117">このチュートリアルでは後でコードを追加しますが、プロジェクト名前空間は `HelloWorld` にします。</span><span class="sxs-lookup"><span data-stu-id="979e4-117">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="979e4-118">メイン メニューで **[表示]**  >  **[ターミナル]** の順に選択して、Visual Studio Code で**ターミナル**を開きます。</span><span class="sxs-lookup"><span data-stu-id="979e4-118">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="979e4-119">**ターミナル**が開き、*HelloWorld* フォルダーにコマンド プロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="979e4-119">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="979e4-120">**ターミナル**で、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="979e4-120">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new console
   ```

<span data-ttu-id="979e4-121">このテンプレートでは、シンプルな "Hello World" アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="979e4-121">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="979e4-122"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> メソッドを呼び出し、コンソール ウィンドウに ":::no-loc text="Hello World!":::" を表示します。</span><span class="sxs-lookup"><span data-stu-id="979e4-122">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display ":::no-loc text="Hello World!":::" in the console window.</span></span>

<span data-ttu-id="979e4-123">テンプレート コードでは、引数として <xref:System.String> 配列を受け取る単一のメソッド `Main` を含む、`Program` というクラスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="979e4-123">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="979e4-124">`Main` はアプリケーションのエントリ ポイントで、アプリケーションを起動するときに、ランタイムによって自動的に呼び出されるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="979e4-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="979e4-125">アプリケーションが起動されるときに提供されるコマンドライン引数はすべて *args* 配列にあります。</span><span class="sxs-lookup"><span data-stu-id="979e4-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="979e4-126">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="979e4-126">Run the app</span></span>

<span data-ttu-id="979e4-127">**ターミナル**で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="979e4-127">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="979e4-128">プログラムによって "Hello World!" が表示されて</span><span class="sxs-lookup"><span data-stu-id="979e4-128">The program displays "Hello World!"</span></span> <span data-ttu-id="979e4-129">終了します。</span><span class="sxs-lookup"><span data-stu-id="979e4-129">and ends.</span></span>

![dotnet run コマンド](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="979e4-131">アプリを拡張する</span><span class="sxs-lookup"><span data-stu-id="979e4-131">Enhance the app</span></span>

<span data-ttu-id="979e4-132">アプリケーションを拡張し、ユーザーに名前の入力を求め、日付と時刻と共にそれを表示するようにします。</span><span class="sxs-lookup"><span data-stu-id="979e4-132">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="979e4-133">*Program.cs* をクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="979e4-133">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="979e4-134">Visual Studio Code で初めて C# ファイルを開くと、[OmniSharp](https://www.omnisharp.net/) がエディターに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="979e4-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Program.cs ファイルを開く](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="979e4-136">Visual Studio Code で、アプリのビルドとデバッグに必要なアセットの追加を求められたら、 **[はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="979e4-136">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![足りない資産の入力を求める](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="979e4-138">*Program.cs* の `Main` メソッドの内容 (`Console.WriteLine` を呼び出す行) を以下のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="979e4-138">Replace the contents of the `Main` method in *Program.cs*, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="979e4-139">このコードによりコンソール ウィンドウにプロンプトが表示され、ユーザーが文字列を入力して <kbd>Enter</kbd> キーを押すまで待機します。</span><span class="sxs-lookup"><span data-stu-id="979e4-139">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="979e4-140">これはこの文字列を `name` という変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="979e4-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="979e4-141">さらに現在の現地時刻を含む <xref:System.DateTime.Now?displayProperty=nameWithType> プロパティの値を取得して、それを `date` という変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="979e4-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="979e4-142">これらの値がコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="979e4-142">And it displays these values in the console window.</span></span> <span data-ttu-id="979e4-143">最後に、コンソール ウィンドウにプロンプトを表示し、<xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> メソッドを呼び出してユーザーによる入力を待ちます。</span><span class="sxs-lookup"><span data-stu-id="979e4-143">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="979e4-144">`\n` は、改行文字を表します。</span><span class="sxs-lookup"><span data-stu-id="979e4-144">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="979e4-145">文字列の前にドル記号 (`$`) を付けると、変数名などの式を文字列で中かっこで囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="979e4-145">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="979e4-146">式の値が、式の代わりに文字列に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="979e4-146">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="979e4-147">この構文は、[補間された文字列](../../csharp/language-reference/tokens/interpolated.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="979e4-147">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="979e4-148">変更内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="979e4-148">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="979e4-149">Visual Studio Code では、変更を明示的に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="979e4-149">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="979e4-150">Visual Studio とは異なり、アプリをビルドして実行してもファイルの変更は自動的には保存されません。</span><span class="sxs-lookup"><span data-stu-id="979e4-150">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="979e4-151">もう一度プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="979e4-151">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="979e4-152">プロンプトに対し、名前を入力し、<kbd>Enter</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="979e4-152">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="プログラムの出力が変更されたターミナル ウィンドウ":::

1. <span data-ttu-id="979e4-154">任意のキーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="979e4-154">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="979e4-155">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="979e4-155">Additional resources</span></span>

- [<span data-ttu-id="979e4-156">Visual Studio Code の設定</span><span class="sxs-lookup"><span data-stu-id="979e4-156">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="979e4-157">次の手順</span><span class="sxs-lookup"><span data-stu-id="979e4-157">Next steps</span></span>

<span data-ttu-id="979e4-158">このチュートリアルでは、.NET Core コンソール アプリケーションを作成しました。</span><span class="sxs-lookup"><span data-stu-id="979e4-158">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="979e4-159">次のチュートリアルでは、アプリをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="979e4-159">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="979e4-160">Visual Studio Code を使用して .NET Core コンソール アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="979e4-160">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
