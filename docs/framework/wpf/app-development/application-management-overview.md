---
title: アプリケーション管理の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: dbc5bd9f699415fb47f21c6a45b1c58cfcff0f33
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124521"
---
# <a name="application-management-overview"></a><span data-ttu-id="9b332-102">アプリケーション管理の概要</span><span class="sxs-lookup"><span data-stu-id="9b332-102">Application Management Overview</span></span>

<span data-ttu-id="9b332-103">すべてのアプリケーションは、アプリケーションの実装と管理に適用される機能を共有することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="9b332-103">All applications tend to share a common set of functionality that applies to application implementation and management.</span></span> <span data-ttu-id="9b332-104">このトピックでは、アプリケーションを作成および管理するための <xref:System.Windows.Application> クラスの機能の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b332-104">This topic provides an overview of the functionality in the <xref:System.Windows.Application> class for creating and managing applications.</span></span>

## <a name="the-application-class"></a><span data-ttu-id="9b332-105">Application クラス</span><span class="sxs-lookup"><span data-stu-id="9b332-105">The Application Class</span></span>

<span data-ttu-id="9b332-106">WPF では、一般的なアプリケーションスコープの機能が <xref:System.Windows.Application> クラスにカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-106">In WPF, common application-scoped functionality is encapsulated in the <xref:System.Windows.Application> class.</span></span> <span data-ttu-id="9b332-107"><xref:System.Windows.Application> クラスには、次の機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9b332-107">The <xref:System.Windows.Application> class includes the following functionality:</span></span>

- <span data-ttu-id="9b332-108">アプリケーションの有効期間を追跡し、相互作用する。</span><span class="sxs-lookup"><span data-stu-id="9b332-108">Tracking and interacting with application lifetime.</span></span>

- <span data-ttu-id="9b332-109">コマンド ライン パラメーターを取得し、処理する。</span><span class="sxs-lookup"><span data-stu-id="9b332-109">Retrieving and processing command-line parameters.</span></span>

- <span data-ttu-id="9b332-110">未処理の例外を検出し、応答する。</span><span class="sxs-lookup"><span data-stu-id="9b332-110">Detecting and responding to unhandled exceptions.</span></span>

- <span data-ttu-id="9b332-111">アプリケーション スコープのプロパティと リソースを共有する。</span><span class="sxs-lookup"><span data-stu-id="9b332-111">Sharing application-scope properties and resources.</span></span>

- <span data-ttu-id="9b332-112">スタンドアロン アプリケーションのウィンドウを管理する。</span><span class="sxs-lookup"><span data-stu-id="9b332-112">Managing windows in standalone applications.</span></span>

- <span data-ttu-id="9b332-113">ナビゲーションを追跡し、管理する。</span><span class="sxs-lookup"><span data-stu-id="9b332-113">Tracking and managing navigation.</span></span>

<a name="The_Application_Class"></a>

## <a name="how-to-perform-common-tasks-using-the-application-class"></a><span data-ttu-id="9b332-114">アプリケーションのクラスを使用して一般的なタスクを実行する方法</span><span class="sxs-lookup"><span data-stu-id="9b332-114">How to Perform Common Tasks Using the Application Class</span></span>

<span data-ttu-id="9b332-115"><xref:System.Windows.Application> クラスの詳細に関心がない場合は、次の表に、<xref:System.Windows.Application> の一般的なタスクとその実行方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9b332-115">If you are not interested in all of the details of the <xref:System.Windows.Application> class, the following table lists some of the common tasks for <xref:System.Windows.Application> and how to accomplish them.</span></span> <span data-ttu-id="9b332-116">関連する API とトピックを表示することによって、詳細情報とサンプル コードを参照できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-116">By viewing the related API and topics, you can find more information and sample code.</span></span>

|<span data-ttu-id="9b332-117">タスク</span><span class="sxs-lookup"><span data-stu-id="9b332-117">Task</span></span>|<span data-ttu-id="9b332-118">アプローチ</span><span class="sxs-lookup"><span data-stu-id="9b332-118">Approach</span></span>|
|----------|--------------|
|<span data-ttu-id="9b332-119">現在のアプリケーションを表すオブジェクトを取得する</span><span class="sxs-lookup"><span data-stu-id="9b332-119">Get an object that represents the current application</span></span>|<span data-ttu-id="9b332-120"><xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b332-120">Use the <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> property.</span></span>|
|<span data-ttu-id="9b332-121">起動画面をアプリケーションに追加する</span><span class="sxs-lookup"><span data-stu-id="9b332-121">Add a startup screen to an application</span></span>|<span data-ttu-id="9b332-122">「[スプラッシュスクリーンを WPF アプリケーションに追加する」を](how-to-add-a-splash-screen-to-a-wpf-application.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-122">See [Add a Splash Screen to a WPF Application](how-to-add-a-splash-screen-to-a-wpf-application.md).</span></span>|
|<span data-ttu-id="9b332-123">アプリケーションを起動する</span><span class="sxs-lookup"><span data-stu-id="9b332-123">Start an application</span></span>|<span data-ttu-id="9b332-124"><xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b332-124">Use the <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> method.</span></span>|
|<span data-ttu-id="9b332-125">アプリケーションを停止する</span><span class="sxs-lookup"><span data-stu-id="9b332-125">Stop an application</span></span>|<span data-ttu-id="9b332-126"><xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> オブジェクトの <xref:System.Windows.Application.Shutdown%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b332-126">Use the <xref:System.Windows.Application.Shutdown%2A> method of the <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> object.</span></span>|
|<span data-ttu-id="9b332-127">コマンド ラインから引数を取得する</span><span class="sxs-lookup"><span data-stu-id="9b332-127">Get arguments from the command line</span></span>|<span data-ttu-id="9b332-128"><xref:System.Windows.Application.Startup?displayProperty=nameWithType> イベントを処理し、<xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b332-128">Handle the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event and use the <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9b332-129">例については、<xref:System.Windows.Application.Startup?displayProperty=nameWithType> イベントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-129">For an example, see the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event.</span></span>|
|<span data-ttu-id="9b332-130">アプリケーションの終了コードを取得し、設定する</span><span class="sxs-lookup"><span data-stu-id="9b332-130">Get and set the application exit code</span></span>|<span data-ttu-id="9b332-131"><xref:System.Windows.Application.Exit?displayProperty=nameWithType> イベントハンドラーの <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> プロパティを設定するか、<xref:System.Windows.Application.Shutdown%2A> メソッドを呼び出して整数を渡します。</span><span class="sxs-lookup"><span data-stu-id="9b332-131">Set the <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> property in the <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event handler or call the <xref:System.Windows.Application.Shutdown%2A> method and pass in an integer.</span></span>|
|<span data-ttu-id="9b332-132">未処理の例外を検出し、応答する</span><span class="sxs-lookup"><span data-stu-id="9b332-132">Detect and respond to unhandled exceptions</span></span>|<span data-ttu-id="9b332-133"><xref:System.Windows.Application.DispatcherUnhandledException> イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="9b332-133">Handle the <xref:System.Windows.Application.DispatcherUnhandledException> event.</span></span>|
|<span data-ttu-id="9b332-134">アプリケーション スコープのリソースを取得し、設定する</span><span class="sxs-lookup"><span data-stu-id="9b332-134">Get and set application-scoped resources</span></span>|<span data-ttu-id="9b332-135"><xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b332-135">Use the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property.</span></span>|
|<span data-ttu-id="9b332-136">アプリケーション スコープのリソース ディクショナリを使用する</span><span class="sxs-lookup"><span data-stu-id="9b332-136">Use an application-scope resource dictionary</span></span>|<span data-ttu-id="9b332-137">「[アプリケーションスコープのリソースディクショナリを使用する](how-to-use-an-application-scope-resource-dictionary.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-137">See [Use an Application-Scope Resource Dictionary](how-to-use-an-application-scope-resource-dictionary.md).</span></span>|
|<span data-ttu-id="9b332-138">アプリケーション スコープのプロパティを取得し、設定する</span><span class="sxs-lookup"><span data-stu-id="9b332-138">Get and set application-scoped properties</span></span>|<span data-ttu-id="9b332-139"><xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b332-139">Use the <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> property.</span></span>|
|<span data-ttu-id="9b332-140">アプリケーションの状態を取得し、保存する</span><span class="sxs-lookup"><span data-stu-id="9b332-140">Get and save an application's state</span></span>|<span data-ttu-id="9b332-141">「アプリケーション[セッション全体でアプリケーションスコープのプロパティを永続化および復元](persist-and-restore-application-scope-properties.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-141">See [Persist and Restore Application-Scope Properties Across Application Sessions](persist-and-restore-application-scope-properties.md).</span></span>|
|<span data-ttu-id="9b332-142">リソース ファイル、コンテンツ ファイル、起点ファイルなど、コード以外のデータ ファイルを管理する。</span><span class="sxs-lookup"><span data-stu-id="9b332-142">Manage non-code data files, including resource files, content files, and site-of-origin files.</span></span>|<span data-ttu-id="9b332-143">「 [WPF アプリケーションのリソースファイル、コンテンツファイル、およびデータファイル](wpf-application-resource-content-and-data-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-143">See [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>|
|<span data-ttu-id="9b332-144">スタンドアロン アプリケーションのウィンドウを管理する</span><span class="sxs-lookup"><span data-stu-id="9b332-144">Manage windows in standalone applications</span></span>|<span data-ttu-id="9b332-145">「[WPF ウィンドウの概要](wpf-windows-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-145">See [WPF Windows Overview](wpf-windows-overview.md).</span></span>|
|<span data-ttu-id="9b332-146">ナビゲーションを追跡し、管理する</span><span class="sxs-lookup"><span data-stu-id="9b332-146">Track and manage navigation</span></span>|<span data-ttu-id="9b332-147">「[ナビゲーションの概要](navigation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-147">See [Navigation Overview](navigation-overview.md).</span></span>|

<a name="The_Application_Definition"></a>

## <a name="the-application-definition"></a><span data-ttu-id="9b332-148">アプリケーション定義</span><span class="sxs-lookup"><span data-stu-id="9b332-148">The Application Definition</span></span>

<span data-ttu-id="9b332-149"><xref:System.Windows.Application> クラスの機能を利用するには、アプリケーション定義を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-149">To utilize the functionality of the <xref:System.Windows.Application> class, you must implement an application definition.</span></span> <span data-ttu-id="9b332-150">WPF アプリケーション定義は <xref:System.Windows.Application> から派生したクラスで、特別な MSBuild 設定を使用して構成されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-150">A WPF application definition is a class that derives from <xref:System.Windows.Application> and is configured with a special MSBuild setting.</span></span>

### <a name="implementing-an-application-definition"></a><span data-ttu-id="9b332-151">アプリケーション定義の実装</span><span class="sxs-lookup"><span data-stu-id="9b332-151">Implementing an Application Definition</span></span>

<span data-ttu-id="9b332-152">一般的な WPF アプリケーション定義は、マークアップと分離コードの両方を使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-152">A typical WPF application definition is implemented using both markup and code-behind.</span></span> <span data-ttu-id="9b332-153">これにより、マークアップを使用して、アプリケーションのプロパティやリソースを宣言によって設定したり、イベントを登録したりでき、分離コードでイベントを処理し、アプリケーション固有の動作を実装することができます。</span><span class="sxs-lookup"><span data-stu-id="9b332-153">This allows you to use markup to declaratively set application properties, resources, and register events, while handling events and implementing application-specific behavior in code-behind.</span></span>

<span data-ttu-id="9b332-154">次の例では、マークアップと分離コードの両方を使用してアプリケーション定義を実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9b332-154">The following example shows how to implement an application definition using both markup and code-behind:</span></span>

[!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]

[!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
[!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]

<span data-ttu-id="9b332-155">マークアップ ファイルと分離コード ファイルを連携させるには、次のようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-155">To allow a markup file and code-behind file to work together, the following needs to happen:</span></span>

- <span data-ttu-id="9b332-156">マークアップでは、`Application` 要素に `x:Class` 属性が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-156">In markup, the `Application` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="9b332-157">アプリケーションがビルドされると、マークアップファイルに `x:Class` が存在することにより、MSBuild は <xref:System.Windows.Application> から派生する `partial` クラスを作成し、`x:Class` 属性によって指定された名前を持ちます。</span><span class="sxs-lookup"><span data-stu-id="9b332-157">When the application is built, the existence of `x:Class` in the markup file causes MSBuild to create a `partial` class that derives from <xref:System.Windows.Application> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="9b332-158">そのためには、XAML スキーマ (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`) の XML 名前空間宣言を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-158">This requires the addition of an XML namespace declaration for the XAML schema (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`).</span></span>

- <span data-ttu-id="9b332-159">分離コードでは、クラスは、マークアップで `x:Class` 属性によって指定された名前と同じ名前を持つ `partial` クラスである必要があり、<xref:System.Windows.Application>から派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-159">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup and must derive from <xref:System.Windows.Application>.</span></span> <span data-ttu-id="9b332-160">これにより、分離コードファイルは、アプリケーションのビルド時にマークアップファイル用に生成される `partial` クラスに関連付けられます (「 [WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="9b332-160">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="9b332-161">Visual Studio を使用して新しい WPF アプリケーションプロジェクトまたは WPF ブラウザーアプリケーションプロジェクトを作成すると、アプリケーション定義が既定で含まれ、マークアップと分離コードの両方を使用して定義されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-161">When you create a new WPF Application project or WPF Browser Application project using Visual Studio, an application definition is included by default and is defined using both markup and code-behind.</span></span>

<span data-ttu-id="9b332-162">このコードは、アプリケーション定義を実装するために最低限必要です。</span><span class="sxs-lookup"><span data-stu-id="9b332-162">This code is the minimum that is required to implement an application definition.</span></span> <span data-ttu-id="9b332-163">ただし、アプリケーションをビルドして実行する前に、追加の MSBuild 構成をアプリケーション定義に対して行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-163">However, an additional MSBuild configuration needs to be made to the application definition before building and running the application.</span></span>

### <a name="configuring-the-application-definition-for-msbuild"></a><span data-ttu-id="9b332-164">MSBuild 用のアプリケーション定義の構成</span><span class="sxs-lookup"><span data-stu-id="9b332-164">Configuring the Application Definition for MSBuild</span></span>

<span data-ttu-id="9b332-165">スタンドアロンアプリケーションと XAML ブラウザーアプリケーション (Xbap) を実行するには、特定のレベルのインフラストラクチャを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-165">Standalone applications and XAML browser applications (XBAPs) require the implementation of a certain level of infrastructure before they can run.</span></span> <span data-ttu-id="9b332-166">このインフラストラクチャの最も重要な部分は、エントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="9b332-166">The most important part of this infrastructure is the entry point.</span></span> <span data-ttu-id="9b332-167">ユーザーがアプリケーションを起動するとき、オペレーティング システムはエントリ ポイントを呼び出します。これは、アプリケーションを起動するための、よく知られている機能です。</span><span class="sxs-lookup"><span data-stu-id="9b332-167">When an application is launched by a user, the operating system calls the entry point, which is a well-known function for starting applications.</span></span>

<span data-ttu-id="9b332-168">従来、開発者は、テクノロジに応じて、このコードの一部または全部を自分で記述する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="9b332-168">Traditionally, developers have needed to write some or all of this code for themselves, depending on the technology.</span></span> <span data-ttu-id="9b332-169">ただし、次の MSBuild プロジェクトファイルに示すように、WPF は、アプリケーション定義のマークアップファイルが MSBuild `ApplicationDefinition` 項目として構成されている場合に、このコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="9b332-169">However, WPF generates this code for you when the markup file of your application definition is configured as an MSBuild `ApplicationDefinition` item, as shown in the following MSBuild project file:</span></span>

```xml
<Project
  DefaultTargets="Build"
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  ...
  <ApplicationDefinition Include="App.xaml" />
  <Compile Include="App.xaml.cs" />
  ...
</Project>
```

<span data-ttu-id="9b332-170">分離コードファイルにコードが含まれているため、通常どおり、MSBuild `Compile` 項目としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="9b332-170">Because the code-behind file contains code, it is marked as an MSBuild `Compile` item, as is normal.</span></span>

<span data-ttu-id="9b332-171">これらの MSBuild 構成をアプリケーション定義のマークアップファイルと分離コードファイルに適用すると、MSBuild によって次のようなコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-171">The application of these MSBuild configurations to the markup and code-behind files of an application definition causes MSBuild to generate code like the following:</span></span>

[!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
[!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]

<span data-ttu-id="9b332-172">生成されたコードは、アプリケーション定義に追加のインフラストラクチャコードを追加します。これには、エントリポイントメソッド `Main`が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9b332-172">The resulting code augments your application definition with additional infrastructure code, which includes the entry-point method `Main`.</span></span> <span data-ttu-id="9b332-173"><xref:System.STAThreadAttribute> 属性は、wpf アプリケーションのメイン UI スレッドが、WPF アプリケーションに必要な STA スレッドであることを示すために、`Main` メソッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-173">The <xref:System.STAThreadAttribute> attribute is applied to the `Main` method to indicate that the main UI thread for the WPF application is an STA thread, which is required for WPF applications.</span></span> <span data-ttu-id="9b332-174">呼び出されると、`Main` は `App` の新しいインスタンスを作成してから、`InitializeComponent` メソッドを呼び出してイベントを登録し、マークアップで実装されるプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="9b332-174">When called, `Main` creates a new instance of `App` before calling the `InitializeComponent` method to register the events and set the properties that are implemented in markup.</span></span> <span data-ttu-id="9b332-175">`InitializeComponent` が生成されるため、<xref:System.Windows.Controls.Page> および <xref:System.Windows.Window> 実装の場合と同様に、アプリケーション定義から `InitializeComponent` を明示的に呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9b332-175">Because `InitializeComponent` is generated for you, you don't need to explicitly call `InitializeComponent` from an application definition like you do for <xref:System.Windows.Controls.Page> and <xref:System.Windows.Window> implementations.</span></span> <span data-ttu-id="9b332-176">最後に、<xref:System.Windows.Application.Run%2A> メソッドが呼び出され、アプリケーションが起動されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-176">Finally, the <xref:System.Windows.Application.Run%2A> method is called to start the application.</span></span>

<a name="Getting_the_Current_Application"></a>

## <a name="getting-the-current-application"></a><span data-ttu-id="9b332-177">現在のアプリケーションの取得</span><span class="sxs-lookup"><span data-stu-id="9b332-177">Getting the Current Application</span></span>

<span data-ttu-id="9b332-178"><xref:System.Windows.Application> クラスの機能はアプリケーション全体で共有されるため、<xref:System.AppDomain>ごとに <xref:System.Windows.Application> クラスのインスタンスは1つしか存在できません。</span><span class="sxs-lookup"><span data-stu-id="9b332-178">Because the functionality of the <xref:System.Windows.Application> class are shared across an application, there can be only one instance of the <xref:System.Windows.Application> class per <xref:System.AppDomain>.</span></span> <span data-ttu-id="9b332-179">これを適用するには、<xref:System.Windows.Application> クラスをシングルトンクラスとして実装します (「[シングルトンC#の実装](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316(v=pandp.10))」を参照してください)。これにより、単独のインスタンスが1つ作成され、`static`<xref:System.Windows.Application.Current%2A> プロパティを使用して共有アクセスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-179">To enforce this, the <xref:System.Windows.Application> class is implemented as a singleton class (see [Implementing Singleton in C#](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316(v=pandp.10))), which creates a single instance of itself and provides shared access to it with the `static`<xref:System.Windows.Application.Current%2A> property.</span></span>

<span data-ttu-id="9b332-180">次のコードは、現在の <xref:System.AppDomain>の <xref:System.Windows.Application> オブジェクトへの参照を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9b332-180">The following code shows how to acquire a reference to the <xref:System.Windows.Application> object for the current <xref:System.AppDomain>.</span></span>

[!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]

<span data-ttu-id="9b332-181"><xref:System.Windows.Application.Current%2A> は、<xref:System.Windows.Application> クラスのインスタンスへの参照を返します。</span><span class="sxs-lookup"><span data-stu-id="9b332-181"><xref:System.Windows.Application.Current%2A> returns a reference to an instance of the <xref:System.Windows.Application> class.</span></span> <span data-ttu-id="9b332-182"><xref:System.Windows.Application> 派生クラスへの参照が必要な場合は、次の例に示すように、<xref:System.Windows.Application.Current%2A> プロパティの値をキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-182">If you want a reference to your <xref:System.Windows.Application> derived class you must cast the value of the <xref:System.Windows.Application.Current%2A> property, as shown in the following example.</span></span>

[!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]

<span data-ttu-id="9b332-183"><xref:System.Windows.Application> オブジェクトの有効期間の任意の時点で、<xref:System.Windows.Application.Current%2A> の値を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="9b332-183">You can inspect the value of <xref:System.Windows.Application.Current%2A> at any point in the lifetime of an <xref:System.Windows.Application> object.</span></span> <span data-ttu-id="9b332-184">ただし、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="9b332-184">However, you should be careful.</span></span> <span data-ttu-id="9b332-185"><xref:System.Windows.Application> クラスがインスタンス化された後、<xref:System.Windows.Application> オブジェクトの状態に一貫性がない期間があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-185">After the <xref:System.Windows.Application> class is instantiated, there is a period during which the state of the <xref:System.Windows.Application> object is inconsistent.</span></span> <span data-ttu-id="9b332-186">この期間中、<xref:System.Windows.Application> は、アプリケーションインフラストラクチャの確立、プロパティの設定、イベントの登録など、コードの実行に必要なさまざまな初期化タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="9b332-186">During this period, <xref:System.Windows.Application> is performing the various initialization tasks that are required by your code to run, including establishing application infrastructure, setting properties, and registering events.</span></span> <span data-ttu-id="9b332-187">この期間中に <xref:System.Windows.Application> オブジェクトを使用しようとすると、設定されているさまざまな <xref:System.Windows.Application> プロパティに依存している場合、コードに予期しない結果が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-187">If you try to use the <xref:System.Windows.Application> object during this period, your code may have unexpected results, particularly if it depends on the various <xref:System.Windows.Application> properties being set.</span></span>

<span data-ttu-id="9b332-188"><xref:System.Windows.Application> 初期化作業が完了すると、その有効期間は実際に開始されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-188">When <xref:System.Windows.Application> completes its initialization work, its lifetime truly begins.</span></span>

<a name="Application_Lifetime"></a>

## <a name="application-lifetime"></a><span data-ttu-id="9b332-189">アプリケーションの有効期間</span><span class="sxs-lookup"><span data-stu-id="9b332-189">Application Lifetime</span></span>

<span data-ttu-id="9b332-190">WPF アプリケーションの有効期間は、<xref:System.Windows.Application> によって発生するいくつかのイベントによってマークされ、アプリケーションが開始されたとき、アクティブ化されているかどうか、およびシャットダウンされた日時を知らせることができます。</span><span class="sxs-lookup"><span data-stu-id="9b332-190">The lifetime of a WPF application is marked by several events that are raised by <xref:System.Windows.Application> to let you know when your application has started, has been activated and deactivated, and has been shut down.</span></span>

<a name="Splash_Screen"></a>

### <a name="splash-screen"></a><span data-ttu-id="9b332-191">スプラッシュ スクリーン</span><span class="sxs-lookup"><span data-stu-id="9b332-191">Splash Screen</span></span>

<span data-ttu-id="9b332-192">.NET Framework 3.5 SP1 以降では、スタートアップウィンドウまたは*スプラッシュスクリーン*で使用するイメージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-192">Starting in the .NET Framework 3.5 SP1, you can specify an image to be used in a startup window, or *splash screen*.</span></span> <span data-ttu-id="9b332-193"><xref:System.Windows.SplashScreen> クラスを使用すると、アプリケーションの読み込み中にスタートアップウィンドウを簡単に表示できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-193">The <xref:System.Windows.SplashScreen> class makes it easy to display a startup window while your application is loading.</span></span> <span data-ttu-id="9b332-194"><xref:System.Windows.SplashScreen> ウィンドウが作成され、<xref:System.Windows.Application.Run%2A> が呼び出される前に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-194">The <xref:System.Windows.SplashScreen> window is created and shown before <xref:System.Windows.Application.Run%2A> is called.</span></span> <span data-ttu-id="9b332-195">詳細については、「[アプリケーションの起動時間](../advanced/application-startup-time.md)」と「[スプラッシュスクリーンを WPF アプリケーションに追加する](how-to-add-a-splash-screen-to-a-wpf-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-195">For more information, see [Application Startup Time](../advanced/application-startup-time.md) and [Add a Splash Screen to a WPF Application](how-to-add-a-splash-screen-to-a-wpf-application.md).</span></span>

<a name="Starting_an_Application"></a>

### <a name="starting-an-application"></a><span data-ttu-id="9b332-196">アプリケーションの起動</span><span class="sxs-lookup"><span data-stu-id="9b332-196">Starting an Application</span></span>

<span data-ttu-id="9b332-197"><xref:System.Windows.Application.Run%2A> が呼び出され、アプリケーションが初期化されると、アプリケーションを実行する準備が整います。</span><span class="sxs-lookup"><span data-stu-id="9b332-197">After <xref:System.Windows.Application.Run%2A> is called and the application is initialized, the application is ready to run.</span></span> <span data-ttu-id="9b332-198">この瞬間は、<xref:System.Windows.Application.Startup> イベントが発生したときに示されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-198">This moment is signified when the <xref:System.Windows.Application.Startup> event is raised:</span></span>

[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]

<span data-ttu-id="9b332-199">アプリケーションの有効期間のこの時点で、最も一般的なのは UI を表示することです。</span><span class="sxs-lookup"><span data-stu-id="9b332-199">At this point in an application's lifetime, the most common thing to do is to show a UI.</span></span>

<a name="Showing_a_User_Interface"></a>

### <a name="showing-a-user-interface"></a><span data-ttu-id="9b332-200">ユーザー インターフェイスの表示</span><span class="sxs-lookup"><span data-stu-id="9b332-200">Showing a User Interface</span></span>

<span data-ttu-id="9b332-201">ほとんどのスタンドアロン Windows アプリケーションでは、実行開始時に <xref:System.Windows.Window> が開かれます。</span><span class="sxs-lookup"><span data-stu-id="9b332-201">Most standalone Windows applications open a <xref:System.Windows.Window> when they begin running.</span></span> <span data-ttu-id="9b332-202"><xref:System.Windows.Application.Startup> イベントハンドラーは、次のコードに示すように、これを実行できる1つの場所です。</span><span class="sxs-lookup"><span data-stu-id="9b332-202">The <xref:System.Windows.Application.Startup> event handler is one location from which you can do this, as demonstrated by the following code.</span></span>

[!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]

[!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
[!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]

> [!NOTE]
> <span data-ttu-id="9b332-203">既定では、スタンドアロンアプリケーションでインスタンス化される最初の <xref:System.Windows.Window> がメインアプリケーションウィンドウになります。</span><span class="sxs-lookup"><span data-stu-id="9b332-203">The first <xref:System.Windows.Window> to be instantiated in a standalone application becomes the main application window by default.</span></span> <span data-ttu-id="9b332-204">この <xref:System.Windows.Window> オブジェクトは、<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> プロパティによって参照されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-204">This <xref:System.Windows.Window> object is referenced by the <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9b332-205"><xref:System.Windows.Application.MainWindow%2A> プロパティの値は、最初にインスタンス化された <xref:System.Windows.Window> とは異なるウィンドウをメインウィンドウにする必要がある場合にプログラムで変更できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-205">The value of the <xref:System.Windows.Application.MainWindow%2A> property can be changed programmatically if a different window than the first instantiated <xref:System.Windows.Window> should be the main window.</span></span>

<span data-ttu-id="9b332-206">XBAP が最初に起動すると、ほとんどの場合、<xref:System.Windows.Controls.Page>に移動します。</span><span class="sxs-lookup"><span data-stu-id="9b332-206">When an XBAP first starts, it will most likely navigate to a <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="9b332-207">これを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="9b332-207">This is shown in the following code.</span></span>

[!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]

[!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
[!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]

<span data-ttu-id="9b332-208"><xref:System.Windows.Window> を開いたり <xref:System.Windows.Controls.Page>に移動したりするために <xref:System.Windows.Application.Startup> を処理する場合は、代わりにマークアップで `StartupUri` 属性を設定できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-208">If you handle <xref:System.Windows.Application.Startup> to only open a <xref:System.Windows.Window> or navigate to a <xref:System.Windows.Controls.Page>, you can set the `StartupUri` attribute in markup instead.</span></span>

<span data-ttu-id="9b332-209">次の例では、スタンドアロンアプリケーションから <xref:System.Windows.Application.StartupUri%2A> を使用して <xref:System.Windows.Window>を開く方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9b332-209">The following example shows how to use the <xref:System.Windows.Application.StartupUri%2A> from a standalone application to open a <xref:System.Windows.Window>.</span></span>

[!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]

<span data-ttu-id="9b332-210">次の例は、XBAP からの <xref:System.Windows.Application.StartupUri%2A> を使用して <xref:System.Windows.Controls.Page>に移動する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9b332-210">The following example shows how to use <xref:System.Windows.Application.StartupUri%2A> from an XBAP to navigate to a <xref:System.Windows.Controls.Page>.</span></span>

[!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]

<span data-ttu-id="9b332-211">このマークアップは、ウィンドウを開くことについて、前のコードと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-211">This markup has the same effect as the previous code for opening a window.</span></span>

> [!NOTE]
> <span data-ttu-id="9b332-212">ナビゲーションの詳細については、「[ナビゲーションの概要](navigation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-212">For more information on navigation, see [Navigation Overview](navigation-overview.md).</span></span>

<span data-ttu-id="9b332-213">パラメーター化されていないコンストラクターを使用してインスタンス化する必要がある場合、またはプロパティを表示する前にそのイベントをサブスクライブする必要がある場合、またはアプリケーションの起動時に指定されたコマンドライン引数を処理する必要がある場合は、<xref:System.Windows.Application.Startup> イベントを処理して <xref:System.Windows.Window> を開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-213">You need to handle the <xref:System.Windows.Application.Startup> event to open a <xref:System.Windows.Window> if you need to instantiate it using a non-parameterless constructor, or you need to set its properties or subscribe to its events before showing it, or you need to process any command-line arguments that were supplied when the application was launched.</span></span>

<a name="Processing_Command_Line_Arguments"></a>

### <a name="processing-command-line-arguments"></a><span data-ttu-id="9b332-214">コマンド ライン引数の処理</span><span class="sxs-lookup"><span data-stu-id="9b332-214">Processing Command-Line Arguments</span></span>

<span data-ttu-id="9b332-215">Windows では、スタンドアロンアプリケーションはコマンドプロンプトまたはデスクトップから起動できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-215">In Windows, standalone applications can be launched from either a command prompt or the desktop.</span></span> <span data-ttu-id="9b332-216">どちらの場合も、コマンド ライン引数をアプリケーションに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="9b332-216">In both cases, command-line arguments can be passed to the application.</span></span> <span data-ttu-id="9b332-217">次の例は、1 つのコマンド ライン引数 "/StartMinimized" を指定して起動されるアプリケーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="9b332-217">The following example shows an application that is launched with a single command-line argument, "/StartMinimized":</span></span>

`wpfapplication.exe /StartMinimized`

<span data-ttu-id="9b332-218">WPF は、アプリケーションの初期化中に、オペレーティングシステムからコマンドライン引数を取得し、<xref:System.Windows.StartupEventArgs> パラメーターの <xref:System.Windows.StartupEventArgs.Args%2A> プロパティを使用して <xref:System.Windows.Application.Startup> イベントハンドラーに渡します。</span><span class="sxs-lookup"><span data-stu-id="9b332-218">During application initialization, WPF retrieves the command-line arguments from the operating system and passes them to the <xref:System.Windows.Application.Startup> event handler via the <xref:System.Windows.StartupEventArgs.Args%2A> property of the <xref:System.Windows.StartupEventArgs> parameter.</span></span> <span data-ttu-id="9b332-219">次のようなコードを使用して、コマンド ライン引数を取得し、格納することができます。</span><span class="sxs-lookup"><span data-stu-id="9b332-219">You can retrieve and store the command-line arguments using code like the following.</span></span>

[!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]

[!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
[!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]

<span data-ttu-id="9b332-220">このコードは <xref:System.Windows.Application.Startup> を処理して **、コマンドライン引数が指定**されているかどうかを確認します。その場合は、メインウィンドウが開き、<xref:System.Windows.WindowState.Minimized>の <xref:System.Windows.WindowState> が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-220">The code handles <xref:System.Windows.Application.Startup> to check whether the **/StartMinimized** command-line argument was provided; if so, it opens the main window with a <xref:System.Windows.WindowState> of <xref:System.Windows.WindowState.Minimized>.</span></span> <span data-ttu-id="9b332-221"><xref:System.Windows.Window.WindowState%2A> プロパティはプログラムによって設定する必要があるため、メイン <xref:System.Windows.Window> はコードで明示的に開く必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-221">Note that because the <xref:System.Windows.Window.WindowState%2A> property must be set programmatically, the main <xref:System.Windows.Window> must be opened explicitly in code.</span></span>

<span data-ttu-id="9b332-222">Xbap は ClickOnce 配置を使用して起動されるため、コマンドライン引数を取得して処理することはできません (「 [WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="9b332-222">XBAPs cannot retrieve and process command-line arguments because they are launched using ClickOnce deployment (see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md)).</span></span> <span data-ttu-id="9b332-223">ただし、起動に使用される URL のクエリ文字列パラメーターを取得して処理することはできます。</span><span class="sxs-lookup"><span data-stu-id="9b332-223">However, they can retrieve and process query string parameters from the URLs that are used to launch them.</span></span>

<a name="Application_Activation_and_Deactivation"></a>

### <a name="application-activation-and-deactivation"></a><span data-ttu-id="9b332-224">アプリケーションのアクティブ化と非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="9b332-224">Application Activation and Deactivation</span></span>

<span data-ttu-id="9b332-225">Windows では、ユーザーがアプリケーションを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="9b332-225">Windows allows users to switch between applications.</span></span> <span data-ttu-id="9b332-226">最も一般的な方法は、Alt キーを押しながら Tab キーを押す方法です。</span><span class="sxs-lookup"><span data-stu-id="9b332-226">The most common way is to use the ALT+TAB key combination.</span></span> <span data-ttu-id="9b332-227">アプリケーションは、ユーザーが選択できる表示 <xref:System.Windows.Window> がある場合にのみ、に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="9b332-227">An application can only be switched to if it has a visible <xref:System.Windows.Window> that a user can select.</span></span> <span data-ttu-id="9b332-228">現在選択されている <xref:System.Windows.Window> は*アクティブウィンドウ*(*前面ウィンドウ*とも呼ばれます) であり、ユーザー入力を受け取る <xref:System.Windows.Window> です。</span><span class="sxs-lookup"><span data-stu-id="9b332-228">The currently selected <xref:System.Windows.Window> is the *active window* (also known as the *foreground window*) and is the <xref:System.Windows.Window> that receives user input.</span></span> <span data-ttu-id="9b332-229">アクティブなウィンドウを含むアプリケーションは、*アクティブなアプリケーション*(または*フォアグラウンドアプリケーション*) です。</span><span class="sxs-lookup"><span data-stu-id="9b332-229">The application with the active window is the *active application* (or *foreground application*).</span></span> <span data-ttu-id="9b332-230">アプリケーションは、次の状況でアクティブ アプリケーションになります。</span><span class="sxs-lookup"><span data-stu-id="9b332-230">An application becomes the active application in the following circumstances:</span></span>

- <span data-ttu-id="9b332-231">このファイルが起動され、<xref:System.Windows.Window>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-231">It is launched and shows a <xref:System.Windows.Window>.</span></span>

- <span data-ttu-id="9b332-232">ユーザーは、アプリケーションで <xref:System.Windows.Window> を選択することによって、別のアプリケーションから切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="9b332-232">A user switches from another application by selecting a <xref:System.Windows.Window> in the application.</span></span>

<span data-ttu-id="9b332-233"><xref:System.Windows.Application.Activated?displayProperty=nameWithType> イベントを処理することによって、アプリケーションがアクティブになったことを検出できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-233">You can detect when an application becomes active by handling the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> event.</span></span>

<span data-ttu-id="9b332-234">同様に、アプリケーションは、次の状況で非アクティブになります。</span><span class="sxs-lookup"><span data-stu-id="9b332-234">Likewise, an application can become inactive in the following circumstances:</span></span>

- <span data-ttu-id="9b332-235">ユーザーが現在のアプリケーションから別のアプリケーションに切り替えた。</span><span class="sxs-lookup"><span data-stu-id="9b332-235">A user switches to another application from the current one.</span></span>

- <span data-ttu-id="9b332-236">アプリケーションがシャットダウンされた。</span><span class="sxs-lookup"><span data-stu-id="9b332-236">When the application shuts down.</span></span>

<span data-ttu-id="9b332-237"><xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> イベントを処理することによって、アプリケーションが非アクティブになったことを検出できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-237">You can detect when an application becomes inactive by handling the <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> event.</span></span>

<span data-ttu-id="9b332-238">次のコードは、アプリケーションがアクティブかどうかを判断するために、<xref:System.Windows.Application.Activated> イベントと <xref:System.Windows.Application.Deactivated> イベントを処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9b332-238">The following code shows how to handle the <xref:System.Windows.Application.Activated> and <xref:System.Windows.Application.Deactivated> events to determine whether an application is active.</span></span>

[!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]

[!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
[!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]

<span data-ttu-id="9b332-239"><xref:System.Windows.Window> は、アクティブ化および非アクティブ化することもできます。</span><span class="sxs-lookup"><span data-stu-id="9b332-239">A <xref:System.Windows.Window> can also be activated and deactivated.</span></span> <span data-ttu-id="9b332-240">詳細については、「<xref:System.Windows.Window.Activated?displayProperty=nameWithType>」および「<xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-240">See <xref:System.Windows.Window.Activated?displayProperty=nameWithType> and <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="9b332-241">Xbap に対して <xref:System.Windows.Application.Activated?displayProperty=nameWithType> も <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> も発生しません。</span><span class="sxs-lookup"><span data-stu-id="9b332-241">Neither <xref:System.Windows.Application.Activated?displayProperty=nameWithType> nor <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> is raised for XBAPs.</span></span>

<a name="Application_Shutdown"></a>

### <a name="application-shutdown"></a><span data-ttu-id="9b332-242">アプリケーションのシャットダウン</span><span class="sxs-lookup"><span data-stu-id="9b332-242">Application Shutdown</span></span>

<span data-ttu-id="9b332-243">アプリケーションの有効期間は、シャット ダウンされると終了します。シャットダウンは、次の理由で発生します。</span><span class="sxs-lookup"><span data-stu-id="9b332-243">The life of an application ends when it is shut down, which can occur for the following reasons:</span></span>

- <span data-ttu-id="9b332-244">ユーザーは、すべての <xref:System.Windows.Window>を閉じます。</span><span class="sxs-lookup"><span data-stu-id="9b332-244">A user closes every <xref:System.Windows.Window>.</span></span>

- <span data-ttu-id="9b332-245">ユーザーがメイン <xref:System.Windows.Window>を閉じます。</span><span class="sxs-lookup"><span data-stu-id="9b332-245">A user closes the main <xref:System.Windows.Window>.</span></span>

- <span data-ttu-id="9b332-246">ユーザーは、ログオフまたはシャットダウンによって Windows セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="9b332-246">A user ends the Windows session by logging off or shutting down.</span></span>

- <span data-ttu-id="9b332-247">アプリケーション固有の条件が満たされた。</span><span class="sxs-lookup"><span data-stu-id="9b332-247">An application-specific condition has been met.</span></span>

<span data-ttu-id="9b332-248">アプリケーションのシャットダウンを管理するために、<xref:System.Windows.Application> には、<xref:System.Windows.Application.Shutdown%2A> メソッド、<xref:System.Windows.Application.ShutdownMode%2A> プロパティ、および <xref:System.Windows.Application.SessionEnding> イベントと <xref:System.Windows.Application.Exit> イベントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9b332-248">To help you manage application shutdown, <xref:System.Windows.Application> provides the <xref:System.Windows.Application.Shutdown%2A> method, the <xref:System.Windows.Application.ShutdownMode%2A> property, and the <xref:System.Windows.Application.SessionEnding> and <xref:System.Windows.Application.Exit> events.</span></span>

> [!NOTE]
> <span data-ttu-id="9b332-249"><xref:System.Windows.Application.Shutdown%2A> は、<xref:System.Security.Permissions.UIPermission>を持つアプリケーションからのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9b332-249"><xref:System.Windows.Application.Shutdown%2A> can only be called from applications that have <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="9b332-250">スタンドアロン WPF アプリケーションは、常にこのアクセス許可を持っています。</span><span class="sxs-lookup"><span data-stu-id="9b332-250">Standalone WPF applications always have this permission.</span></span> <span data-ttu-id="9b332-251">ただし、インターネットゾーンの部分信頼セキュリティサンドボックスで実行されている Xbap では実行されません。</span><span class="sxs-lookup"><span data-stu-id="9b332-251">However, XBAPs running in the Internet zone partial-trust security sandbox do not.</span></span>

#### <a name="shutdown-mode"></a><span data-ttu-id="9b332-252">シャットダウン モード</span><span class="sxs-lookup"><span data-stu-id="9b332-252">Shutdown Mode</span></span>

<span data-ttu-id="9b332-253">ほとんどのアプリケーションは、すべてのウィンドウが閉じられるか、メイン ウィンドウが閉じられたときにシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="9b332-253">Most applications shut down either when all the windows are closed or when the main window is closed.</span></span> <span data-ttu-id="9b332-254">ただし、場合によっては、他のアプリケーションに固有の条件によって、アプリケーションがシャット ダウンするタイミングに影響します。</span><span class="sxs-lookup"><span data-stu-id="9b332-254">Sometimes, however, other application-specific conditions may determine when an application shuts down.</span></span> <span data-ttu-id="9b332-255">次の <xref:System.Windows.ShutdownMode> 列挙値のいずれかを使用して <xref:System.Windows.Application.ShutdownMode%2A> を設定することにより、アプリケーションがシャットダウンする条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-255">You can specify the conditions under which your application will shut down by setting <xref:System.Windows.Application.ShutdownMode%2A> with one of the following <xref:System.Windows.ShutdownMode> enumeration values:</span></span>

- <xref:System.Windows.ShutdownMode.OnLastWindowClose>

- <xref:System.Windows.ShutdownMode.OnMainWindowClose>

- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>

<span data-ttu-id="9b332-256"><xref:System.Windows.Application.ShutdownMode%2A> の既定値は <xref:System.Windows.ShutdownMode.OnLastWindowClose>です。これは、アプリケーションの最後のウィンドウがユーザーによって閉じられたときに、アプリケーションが自動的にシャットダウンすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9b332-256">The default value of <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnLastWindowClose>, which means that an application automatically shuts down when the last window in the application is closed by the user.</span></span> <span data-ttu-id="9b332-257">ただし、メインウィンドウが閉じられたときにアプリケーションをシャットダウンする必要がある場合は、<xref:System.Windows.Application.ShutdownMode%2A> を <xref:System.Windows.ShutdownMode.OnMainWindowClose>に設定すると WPF によって自動的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-257">However, if your application should be shut down when the main window is closed, WPF automatically does that if you set <xref:System.Windows.Application.ShutdownMode%2A> to <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span> <span data-ttu-id="9b332-258">次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-258">This is shown in the following example.</span></span>

[!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]

<span data-ttu-id="9b332-259">アプリケーション固有のシャットダウン条件がある場合は、<xref:System.Windows.Application.ShutdownMode%2A> を <xref:System.Windows.ShutdownMode.OnExplicitShutdown>に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b332-259">When you have application-specific shutdown conditions, you set <xref:System.Windows.Application.ShutdownMode%2A> to <xref:System.Windows.ShutdownMode.OnExplicitShutdown>.</span></span> <span data-ttu-id="9b332-260">この場合、<xref:System.Windows.Application.Shutdown%2A> メソッドを明示的に呼び出すことによって、アプリケーションをシャットダウンする必要があります。それ以外の場合、すべてのウィンドウが閉じている場合でも、アプリケーションの実行は継続されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-260">In this case, it is your responsibility to shut an application down by explicitly calling the <xref:System.Windows.Application.Shutdown%2A> method; otherwise, your application will continue running even if all the windows are closed.</span></span> <span data-ttu-id="9b332-261"><xref:System.Windows.Application.Shutdown%2A> は、<xref:System.Windows.Application.ShutdownMode%2A> が <xref:System.Windows.ShutdownMode.OnLastWindowClose> または <xref:System.Windows.ShutdownMode.OnMainWindowClose>の場合に暗黙的に呼び出されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-261">Note that <xref:System.Windows.Application.Shutdown%2A> is called implicitly when the <xref:System.Windows.Application.ShutdownMode%2A> is either <xref:System.Windows.ShutdownMode.OnLastWindowClose> or <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>

> [!NOTE]
> <span data-ttu-id="9b332-262"><xref:System.Windows.Application.ShutdownMode%2A> は XBAP から設定できますが、無視されます。XBAP は、ブラウザーから移動したとき、または XBAP をホストしているブラウザーを閉じたときに常にシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="9b332-262"><xref:System.Windows.Application.ShutdownMode%2A> can be set from an XBAP, but it is ignored; an XBAP is always shut down when it is navigated away from in a browser or when the browser that hosts the XBAP is closed.</span></span> <span data-ttu-id="9b332-263">詳細については、「[ナビゲーションの概要](navigation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-263">For more information, see [Navigation Overview](navigation-overview.md).</span></span>

#### <a name="session-ending"></a><span data-ttu-id="9b332-264">セッションの終了</span><span class="sxs-lookup"><span data-stu-id="9b332-264">Session Ending</span></span>

<span data-ttu-id="9b332-265"><xref:System.Windows.Application.ShutdownMode%2A> プロパティによって示されるシャットダウン条件は、アプリケーションに固有のものです。</span><span class="sxs-lookup"><span data-stu-id="9b332-265">The shutdown conditions that are described by the <xref:System.Windows.Application.ShutdownMode%2A> property are specific to an application.</span></span> <span data-ttu-id="9b332-266">ただし、場合によっては、アプリケーションは、外部条件の結果としてシャットダウンすることもあります。</span><span class="sxs-lookup"><span data-stu-id="9b332-266">In some cases, though, an application may shut down as a result of an external condition.</span></span> <span data-ttu-id="9b332-267">最も一般的な外部条件は、ユーザーが次の操作によって Windows セッションを終了したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="9b332-267">The most common external condition occurs when a user ends the Windows session by the following actions:</span></span>

- <span data-ttu-id="9b332-268">ログオフ中</span><span class="sxs-lookup"><span data-stu-id="9b332-268">Logging off</span></span>

- <span data-ttu-id="9b332-269">シャット ダウン</span><span class="sxs-lookup"><span data-stu-id="9b332-269">Shutting down</span></span>

- <span data-ttu-id="9b332-270">再起動中</span><span class="sxs-lookup"><span data-stu-id="9b332-270">Restarting</span></span>

- <span data-ttu-id="9b332-271">休止</span><span class="sxs-lookup"><span data-stu-id="9b332-271">Hibernating</span></span>

<span data-ttu-id="9b332-272">Windows セッションが終了したことを検出するには、次の例に示すように、<xref:System.Windows.Application.SessionEnding> イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="9b332-272">To detect when a Windows session ends, you can handle the <xref:System.Windows.Application.SessionEnding> event, as illustrated in the following example.</span></span>

[!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]

[!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
[!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]

<span data-ttu-id="9b332-273">この例では、コードは <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> プロパティを調べて、Windows セッションがどのように終了しているかを判断します。</span><span class="sxs-lookup"><span data-stu-id="9b332-273">In this example, the code inspects the <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> property to determine how the Windows session is ending.</span></span> <span data-ttu-id="9b332-274">この値を使用して、ユーザーに確認メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="9b332-274">It uses this value to display a confirmation message to the user.</span></span> <span data-ttu-id="9b332-275">ユーザーがセッションを終了したくない場合、コードは <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> を `true` に設定して、Windows セッションが終了しないようにします。</span><span class="sxs-lookup"><span data-stu-id="9b332-275">If the user does not want the session to end, the code sets <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> to `true` to prevent the Windows session from ending.</span></span>

> [!NOTE]
> <span data-ttu-id="9b332-276">Xbap に対して <xref:System.Windows.Application.SessionEnding> が発生しません。</span><span class="sxs-lookup"><span data-stu-id="9b332-276"><xref:System.Windows.Application.SessionEnding> is not raised for XBAPs.</span></span>

#### <a name="exit"></a><span data-ttu-id="9b332-277">Exit</span><span class="sxs-lookup"><span data-stu-id="9b332-277">Exit</span></span>

<span data-ttu-id="9b332-278">アプリケーションがシャット ダウンするときには、アプリケーション状態の保存など、いくつかの最終処理を実行しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-278">When an application shuts down, it may need to perform some final processing, such as persisting application state.</span></span> <span data-ttu-id="9b332-279">このような状況では、次の例に示す `App_Exit` イベントハンドラーのように、<xref:System.Windows.Application.Exit> イベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-279">For these situations, you can handle the <xref:System.Windows.Application.Exit> event, as the `App_Exit` event handler does in the following example.</span></span> <span data-ttu-id="9b332-280">これは、 *app.xaml*ファイルのイベントハンドラーとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-280">It is defined as an event handler in the *App.xaml* file.</span></span> <span data-ttu-id="9b332-281">その実装は、 *App.xaml.cs*ファイルと*app.xaml*ファイルで強調表示されています。</span><span class="sxs-lookup"><span data-stu-id="9b332-281">Its implementation is highlighted in the *App.xaml.cs* and *Application.xaml.vb* files.</span></span>

[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]

[!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
[!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]

<span data-ttu-id="9b332-282">完全な例については、「アプリケーション[セッション全体でアプリケーションスコープのプロパティを永続化および復元](persist-and-restore-application-scope-properties.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-282">For the complete example, see [Persist and Restore Application-Scope Properties Across Application Sessions](persist-and-restore-application-scope-properties.md).</span></span>

<span data-ttu-id="9b332-283"><xref:System.Windows.Application.Exit> は、スタンドアロンアプリケーションと Xbap の両方で処理できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-283"><xref:System.Windows.Application.Exit> can be handled by both standalone applications and XBAPs.</span></span> <span data-ttu-id="9b332-284">Xbap の場合、次のような状況では <xref:System.Windows.Application.Exit> が発生します。</span><span class="sxs-lookup"><span data-stu-id="9b332-284">For XBAPs, <xref:System.Windows.Application.Exit> is raised when in the following circumstances:</span></span>

- <span data-ttu-id="9b332-285">XBAP は移動されません。</span><span class="sxs-lookup"><span data-stu-id="9b332-285">An XBAP is navigated away from.</span></span>

- <span data-ttu-id="9b332-286">Internet Explorer で、XBAP をホストしているタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9b332-286">In Internet Explorer, when the tab that is hosting the XBAP is closed.</span></span>

- <span data-ttu-id="9b332-287">ブラウザーが閉じられた。</span><span class="sxs-lookup"><span data-stu-id="9b332-287">When the browser is closed.</span></span>

#### <a name="exit-code"></a><span data-ttu-id="9b332-288">終了コード</span><span class="sxs-lookup"><span data-stu-id="9b332-288">Exit Code</span></span>

<span data-ttu-id="9b332-289">ほとんどのアプリケーションは、ユーザー要求に応じてオペレーティング システムから起動されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-289">Applications are mostly launched by the operating system in response to a user request.</span></span> <span data-ttu-id="9b332-290">ただし、アプリケーションは、特定のタスクを実行するために、別のアプリケーションに起動されることもあります。</span><span class="sxs-lookup"><span data-stu-id="9b332-290">However, an application can be launched by another application to perform some specific task.</span></span> <span data-ttu-id="9b332-291">起動されたアプリケーションがシャット ダウンするとき、起動元のアプリケーションは、起動されたアプリケーションのシャット ダウン条件を知ならなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="9b332-291">When the launched application shuts down, the launching application may want to know the condition under which the launched application shut down.</span></span> <span data-ttu-id="9b332-292">このような状況では、アプリケーションがシャットダウン時にアプリケーションの終了コードを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="9b332-292">In these situations, Windows allows applications to return an application exit code on shutdown.</span></span> <span data-ttu-id="9b332-293">既定では、WPF アプリケーションは終了コード値0を返します。</span><span class="sxs-lookup"><span data-stu-id="9b332-293">By default, WPF applications return an exit code value of 0.</span></span>

> [!NOTE]
> <span data-ttu-id="9b332-294">Visual Studio からデバッグする場合、アプリケーションの終了コードは、次のようなメッセージで、アプリケーションのシャットダウン時に**出力**ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-294">When you debug from Visual Studio, the application exit code is displayed in the **Output** window when the application shuts down, in a message that looks like the following:</span></span>
>
> `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`
>
> <span data-ttu-id="9b332-295">**[表示]** メニューの **[出力]** をクリックして、 **[出力]** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="9b332-295">You open the **Output** window by clicking **Output** on the **View** menu.</span></span>

<span data-ttu-id="9b332-296">終了コードを変更するには、<xref:System.Windows.Application.Shutdown%28System.Int32%29> のオーバーロードを呼び出します。このオーバーロードは、終了コードとして整数引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="9b332-296">To change the exit code, you can call the <xref:System.Windows.Application.Shutdown%28System.Int32%29> overload, which accepts an integer argument to be the exit code:</span></span>

[!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
[!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]

<span data-ttu-id="9b332-297">終了コードの値を検出し、その値を変更するには、<xref:System.Windows.Application.Exit> イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="9b332-297">You can detect the value of the exit code, and change it, by handling the <xref:System.Windows.Application.Exit> event.</span></span> <span data-ttu-id="9b332-298"><xref:System.Windows.Application.Exit> イベントハンドラーには、<xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> プロパティを使用して終了コードへのアクセスを提供する <xref:System.Windows.ExitEventArgs> が渡されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-298">The <xref:System.Windows.Application.Exit> event handler is passed an <xref:System.Windows.ExitEventArgs> which provides access to the exit code with the <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> property.</span></span> <span data-ttu-id="9b332-299">詳細については、<xref:System.Windows.Application.Exit> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b332-299">For more information, see <xref:System.Windows.Application.Exit>.</span></span>

> [!NOTE]
> <span data-ttu-id="9b332-300">終了コードは、スタンドアロンアプリケーションと Xbap の両方で設定できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-300">You can set the exit code in both standalone applications and XBAPs.</span></span> <span data-ttu-id="9b332-301">ただし、Xbap の場合、終了コードの値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-301">However, the exit code value is ignored for XBAPs.</span></span>

<a name="Unhandled_Exceptions"></a>

### <a name="unhandled-exceptions"></a><span data-ttu-id="9b332-302">未処理の例外</span><span class="sxs-lookup"><span data-stu-id="9b332-302">Unhandled Exceptions</span></span>

<span data-ttu-id="9b332-303">ときには、アプリケーションは、予期しない例外がスローされたときなど、異常な条件下でシャットダウンすることがあります。</span><span class="sxs-lookup"><span data-stu-id="9b332-303">Sometimes an application may shut down under abnormal conditions, such as when an unanticipated exception is thrown.</span></span> <span data-ttu-id="9b332-304">この場合、アプリケーションには、例外を検出して処理するためのコードがありません。</span><span class="sxs-lookup"><span data-stu-id="9b332-304">In this case, the application may not have the code to detect and process the exception.</span></span> <span data-ttu-id="9b332-305">この種類の例外は、未処理の例外と呼ばれます。アプリケーションが閉じられる前に、次の図に示されているような通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-305">This type of exception is an unhandled exception; a notification similar to that shown in the following figure is displayed before the application is closed.</span></span>

![未処理の例外通知を示すスクリーンショット。](./media/application-management-overview/unhandled-exception-notification.png)

<span data-ttu-id="9b332-307">ユーザー エクスペリエンスの観点から、アプリケーションは、次のいずれか、またはすべてを行うことによって、この既定の動作を回避することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9b332-307">From the user experience perspective, it is better for an application to avoid this default behavior by doing some or all of the following:</span></span>

- <span data-ttu-id="9b332-308">わかりやすい情報を表示する。</span><span class="sxs-lookup"><span data-stu-id="9b332-308">Displaying user-friendly information.</span></span>

- <span data-ttu-id="9b332-309">アプリケーションの続行を試みる。</span><span class="sxs-lookup"><span data-stu-id="9b332-309">Attempting to keep an application running.</span></span>

- <span data-ttu-id="9b332-310">開発者にとってわかりやすい例外情報を Windows イベントログに記録します。</span><span class="sxs-lookup"><span data-stu-id="9b332-310">Recording detailed, developer-friendly exception information in the Windows event log.</span></span>

<span data-ttu-id="9b332-311">このサポートを実装することは、未処理の例外を検出できるかどうかによって異なります。これは、<xref:System.Windows.Application.DispatcherUnhandledException> イベントが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9b332-311">Implementing this support depends on being able to detect unhandled exceptions, which is what the <xref:System.Windows.Application.DispatcherUnhandledException> event is raised for.</span></span>

[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]

[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]

<span data-ttu-id="9b332-312"><xref:System.Windows.Application.DispatcherUnhandledException> イベントハンドラーには、例外自体 (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>) を含む、未処理の例外に関するコンテキスト情報を含む <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> パラメーターが渡されます。</span><span class="sxs-lookup"><span data-stu-id="9b332-312">The <xref:System.Windows.Application.DispatcherUnhandledException> event handler is passed a <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> parameter that contains contextual information regarding the unhandled exception, including the exception itself (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="9b332-313">この情報を使用して、例外の処理方法を決定できます。</span><span class="sxs-lookup"><span data-stu-id="9b332-313">You can use this information to determine how to handle the exception.</span></span>

<span data-ttu-id="9b332-314"><xref:System.Windows.Application.DispatcherUnhandledException>を処理する場合は、<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> プロパティを `true`に設定する必要があります。それ以外の場合、WPF は例外を未処理のままと見なし、前に説明した既定の動作に戻します。</span><span class="sxs-lookup"><span data-stu-id="9b332-314">When you handle <xref:System.Windows.Application.DispatcherUnhandledException>, you should set the <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> property to `true`; otherwise, WPF still considers the exception to be unhandled and reverts to the default behavior described earlier.</span></span> <span data-ttu-id="9b332-315">未処理の例外が発生し、<xref:System.Windows.Application.DispatcherUnhandledException> イベントが処理されない場合、またはイベントが処理され、<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> が `false`に設定されている場合は、アプリケーションは直ちにシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="9b332-315">If an unhandled exception is raised and either the <xref:System.Windows.Application.DispatcherUnhandledException> event is not handled, or the event is handled and <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> is set to `false`, the application shuts down immediately.</span></span> <span data-ttu-id="9b332-316">さらに、他の <xref:System.Windows.Application> イベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="9b332-316">Furthermore, no other <xref:System.Windows.Application> events are raised.</span></span> <span data-ttu-id="9b332-317">そのため、アプリケーションのシャットダウン前に実行する必要があるコードがアプリケーションに含まれている場合は、<xref:System.Windows.Application.DispatcherUnhandledException> を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b332-317">Consequently, you need to handle <xref:System.Windows.Application.DispatcherUnhandledException> if your application has code that must run before the application shuts down.</span></span>

<span data-ttu-id="9b332-318">アプリケーションは、未処理の例外の結果としてシャットダウンすることがありますが、通常は、次のセクションで説明されているように、ユーザーの要求に応じてシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="9b332-318">Although an application may shut down as a result of an unhandled exception, an application usually shuts down in response to a user request, as discussed in the next section.</span></span>

<a name="Application_Lifetime_Events"></a>

### <a name="application-lifetime-events"></a><span data-ttu-id="9b332-319">アプリケーションの有効期間イベント</span><span class="sxs-lookup"><span data-stu-id="9b332-319">Application Lifetime Events</span></span>

<span data-ttu-id="9b332-320">スタンドアロンアプリケーションと Xbap の有効期間はまったく同じではありません。</span><span class="sxs-lookup"><span data-stu-id="9b332-320">Standalone applications and XBAPs don't have exactly the same lifetimes.</span></span> <span data-ttu-id="9b332-321">次の図は、スタンドアロン アプリケーションの有効期間中の主なイベントと発生順を示しています。</span><span class="sxs-lookup"><span data-stu-id="9b332-321">The following figure illustrates the key events in the lifetime of a standalone application and shows the sequence in which they are raised.</span></span>

<span data-ttu-id="9b332-322">![スタンドアロン&#45;アプリケーションアプリケーションオブジェクトイベント](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")</span><span class="sxs-lookup"><span data-stu-id="9b332-322">![Standalone Application &#45; Application Object Events](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")</span></span>

<span data-ttu-id="9b332-323">同様に、次の図は、XBAP の有効期間中の主なイベントと、それらが発生する順序を示しています。</span><span class="sxs-lookup"><span data-stu-id="9b332-323">Likewise, the following figure illustrates the key events in the lifetime of an XBAP, and shows the sequence in which they are raised.</span></span>

<span data-ttu-id="9b332-324">![XBAP &#45;アプリケーションオブジェクトイベント](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")</span><span class="sxs-lookup"><span data-stu-id="9b332-324">![XBAP &#45; Application Object Events](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")</span></span>

## <a name="see-also"></a><span data-ttu-id="9b332-325">参照</span><span class="sxs-lookup"><span data-stu-id="9b332-325">See also</span></span>

- <xref:System.Windows.Application>
- [<span data-ttu-id="9b332-326">WPF ウィンドウの概要</span><span class="sxs-lookup"><span data-stu-id="9b332-326">WPF Windows Overview</span></span>](wpf-windows-overview.md)
- [<span data-ttu-id="9b332-327">ナビゲーションの概要</span><span class="sxs-lookup"><span data-stu-id="9b332-327">Navigation Overview</span></span>](navigation-overview.md)
- [<span data-ttu-id="9b332-328">WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル</span><span class="sxs-lookup"><span data-stu-id="9b332-328">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
- [<span data-ttu-id="9b332-329">WPF におけるパッケージの URI</span><span class="sxs-lookup"><span data-stu-id="9b332-329">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
- <span data-ttu-id="9b332-330">[アプリケーションモデル: 操作方法に関するトピック](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9b332-330">[Application Model: How-to Topics](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))</span></span>
- [<span data-ttu-id="9b332-331">アプリケーション開発</span><span class="sxs-lookup"><span data-stu-id="9b332-331">Application Development</span></span>](index.md)
