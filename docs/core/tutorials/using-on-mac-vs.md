---
title: Visual Studio for Mac を使用した .NET Core の概要
description: このトピックでは、Visual Studio for Mac と .NET Core を使用して、単純なコンソール アプリケーションをビルドする手順を示します。
ms.date: 12/19/2019
ms.openlocfilehash: 4cd7e311411bce62698e291e763227496877ea39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740493"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="9190a-103">Visual Studio for Mac を使用した macOS での .NET Core の概要</span><span class="sxs-lookup"><span data-stu-id="9190a-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="9190a-104">Visual Studio for Mac では、.NET Core アプリケーション開発用の機能をすべて備えた統合開発環境 (IDE) が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9190a-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="9190a-105">この記事では、Visual Studio for Mac と .NET Core を使用して、単純なコンソール アプリケーションをビルドする手順を示します。</span><span class="sxs-lookup"><span data-stu-id="9190a-105">This article walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="9190a-106">お客様のフィードバックは非常に貴重です。</span><span class="sxs-lookup"><span data-stu-id="9190a-106">Your feedback is highly valued.</span></span> <span data-ttu-id="9190a-107">次の 2 つの方法で Visual Studio for Mac の開発チームにフィードバックを送信できます。</span><span class="sxs-lookup"><span data-stu-id="9190a-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="9190a-108">Visual Studio for Mac で、メニューから **[ヘルプ]**  >  **[問題の報告]** の順に選択するか、ようこそ画面から **[問題の報告]** を選択して、バグ報告を提出するためのウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="9190a-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="9190a-109">お客様のフィードバックは、[開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/8/index.html) ポータルで追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="9190a-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="9190a-110">提案するには、メニューから **[ヘルプ]**  >  **[提案の送信]** の順に選択するか、ようこそ画面から **[提案の送信]** を選択し、[Visual Studio for Mac の開発者コミュニティの Web ページ](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)に移動します。</span><span class="sxs-lookup"><span data-stu-id="9190a-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9190a-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="9190a-111">Prerequisites</span></span>

<span data-ttu-id="9190a-112">[.NET Core の依存関係と要件](../install/dependencies.md?pivots=os-macos)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9190a-112">See the [.NET Core dependencies and requirements](../install/dependencies.md?pivots=os-macos) article.</span></span>

<span data-ttu-id="9190a-113">サポートされているバージョンの .NET Core を使用していることを確認するには、「[.NET Core サポート](/visualstudio/mac/net-core-support)」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9190a-113">Check the [.NET Core Support](/visualstudio/mac/net-core-support) article to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="9190a-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="9190a-114">Get started</span></span>

<span data-ttu-id="9190a-115">必須コンポーネントと Visual Studio for Mac を既にインストールしている場合は、このセクションをスキップして、「[プロジェクトの作成](#creating-a-project)」に進みます。</span><span class="sxs-lookup"><span data-stu-id="9190a-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="9190a-116">以下の手順に従って、必須コンポーネントと Visual Studio for Mac をインストールします。</span><span class="sxs-lookup"><span data-stu-id="9190a-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="9190a-117">[Visual Studio for Mac インストーラー](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9190a-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="9190a-118">インストーラーを実行します。</span><span class="sxs-lookup"><span data-stu-id="9190a-118">Run the installer.</span></span> <span data-ttu-id="9190a-119">使用許諾契約を読み、同意します。</span><span class="sxs-lookup"><span data-stu-id="9190a-119">Read and accept the license agreement.</span></span> <span data-ttu-id="9190a-120">インストール時に、.NET Core をインストールするオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9190a-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="9190a-121">Xamarin (クロスプラットフォーム モバイル アプリ開発テクノロジ) をインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="9190a-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="9190a-122">.NET Core の開発の場合、Xamarin とその関連コンポーネントのインストールは省略できます。</span><span class="sxs-lookup"><span data-stu-id="9190a-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="9190a-123">Visual Studio for Mac のインストール プロセスのチュートリアルについては、[Visual Studio for Mac のドキュメント](/visualstudio/mac/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9190a-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="9190a-124">インストールが完了したら、Visual Studio for Mac IDE を起動します。</span><span class="sxs-lookup"><span data-stu-id="9190a-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="9190a-125">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="9190a-125">Creating a project</span></span>

1. <span data-ttu-id="9190a-126">スタート ウィンドウで **[新規]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9190a-126">Select **New** on the start window.</span></span>

   ![Visual Studio for Mac のスタート ウィンドウの [新規] ボタン](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="9190a-128">**[新しいプロジェクト]** ダイアログで、**[.NET Core]** ノードの下にある **[アプリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9190a-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="9190a-129">**[コンソール アプリケーション]** テンプレートを選択してから **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9190a-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![新しいプロジェクト テンプレートのリスト](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="9190a-131">複数のバージョンの .NET Core をインストールしている場合は、プロジェクトのターゲット フレームワークを選択します。</span><span class="sxs-lookup"><span data-stu-id="9190a-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="9190a-132">**[プロジェクト名]** には「HelloWorld」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9190a-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="9190a-133">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9190a-133">Select **Create**.</span></span>

   ![[Configure your new Console Application (新しいコンソール アプリケーションの構成)] ダイアログ](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="9190a-135">プロジェクトの依存関係が復元されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="9190a-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="9190a-136">プロジェクトには、`Main` メソッドを持つ `Program` クラスを含む *Program.cs* という C# ファイルが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="9190a-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="9190a-137">`Console.WriteLine` ステートメントは、アプリの実行時に</span><span class="sxs-lookup"><span data-stu-id="9190a-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="9190a-138">コンソールに "Hello World!" と出力します。</span><span class="sxs-lookup"><span data-stu-id="9190a-138">to the console when the app is run.</span></span>

   ![Program.cs ファイルが開かれた状態のメイン ウィンドウ](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="9190a-140">アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="9190a-140">Run the application</span></span>

<span data-ttu-id="9190a-141">⌘ ↵ (command + enter) を使用してデバッグ モードで、または ⌥ ⌘ ↵ (option + command + enter) を使用してリリース モードでアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9190a-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![[アプリケーション出力] ウィンドウに Hello World! が表示された状態](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="9190a-143">次のステップ</span><span class="sxs-lookup"><span data-stu-id="9190a-143">Next step</span></span>

<span data-ttu-id="9190a-144">「[Visual Studio for Mac を使用した macOS での完全な .NET Core ソリューションの構築](using-on-mac-vs-full-solution.md)」トピックでは、再利用可能なライブラリと単体テストを含む完全な .NET Core ソリューションを構築する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9190a-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
