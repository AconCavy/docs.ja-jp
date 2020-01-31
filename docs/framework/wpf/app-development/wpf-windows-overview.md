---
title: Windows の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: 17582192fabf85777bba250f6f53047a84f264b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742359"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="8e421-102">WPF ウィンドウの概要</span><span class="sxs-lookup"><span data-stu-id="8e421-102">WPF Windows Overview</span></span>
<span data-ttu-id="8e421-103">ユーザーは、Windows を通じて Windows Presentation Foundation (WPF) スタンドアロンアプリケーションと対話します。</span><span class="sxs-lookup"><span data-stu-id="8e421-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="8e421-104">ウィンドウの主な目的は、データを視覚化してユーザーがデータと対話できるコンテンツをホストすることです。</span><span class="sxs-lookup"><span data-stu-id="8e421-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="8e421-105">スタンドアロン WPF アプリケーションは、<xref:System.Windows.Window> クラスを使用して独自のウィンドウを提供します。</span><span class="sxs-lookup"><span data-stu-id="8e421-105">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="8e421-106">このトピックでは、スタンドアロンアプリケーションでのウィンドウの作成と管理の基礎について説明する前に、<xref:System.Windows.Window> について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e421-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e421-107">XAML ブラウザーアプリケーション (Xbap) や疎 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ページなど、ブラウザーでホストされる WPF アプリケーションは、独自のウィンドウを提供しません。</span><span class="sxs-lookup"><span data-stu-id="8e421-107">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="8e421-108">代わりに、Windows Internet Explorer によって提供される windows でホストされます。</span><span class="sxs-lookup"><span data-stu-id="8e421-108">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="8e421-109">「 [WPF XAML ブラウザーアプリケーションの概要](wpf-xaml-browser-applications-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e421-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a><span data-ttu-id="8e421-110">ウィンドウ クラス</span><span class="sxs-lookup"><span data-stu-id="8e421-110">The Window Class</span></span>  
 <span data-ttu-id="8e421-111">次の図は、ウィンドウの構成部分を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e421-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![ウィンドウ要素を示すスクリーンショット。](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="8e421-113">ウィンドウは、非クライアント領域とクライアント領域の 2 つに分かれます。</span><span class="sxs-lookup"><span data-stu-id="8e421-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="8e421-114">ウィンドウの*非クライアント領域*は WPF によって実装され、次のような、ほとんどのウィンドウに共通のウィンドウ部分が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8e421-114">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="8e421-115">境界線。</span><span class="sxs-lookup"><span data-stu-id="8e421-115">A border.</span></span>  
  
- <span data-ttu-id="8e421-116">タイトル バー。</span><span class="sxs-lookup"><span data-stu-id="8e421-116">A title bar.</span></span>  
  
- <span data-ttu-id="8e421-117">アイコン。</span><span class="sxs-lookup"><span data-stu-id="8e421-117">An icon.</span></span>  
  
- <span data-ttu-id="8e421-118">最小化ボタン、最大化ボタン、および元に戻すボタン。</span><span class="sxs-lookup"><span data-stu-id="8e421-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="8e421-119">閉じるボタン。</span><span class="sxs-lookup"><span data-stu-id="8e421-119">A Close button.</span></span>  
  
- <span data-ttu-id="8e421-120">ウィンドウを最小化、最大化、元のサイズに戻す、移動、サイズ変更、および閉じるためのメニュー項目を含むシステム メニュー。</span><span class="sxs-lookup"><span data-stu-id="8e421-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="8e421-121">ウィンドウの*クライアント領域*は、ウィンドウの非クライアント領域内の領域であり、開発者がメニューバー、ツールバー、コントロールなどのアプリケーション固有のコンテンツを追加するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="8e421-122">WPF では、ウィンドウは、次の操作を実行するために使用する <xref:System.Windows.Window> クラスによってカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-122">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="8e421-123">ウィンドウを表示する。</span><span class="sxs-lookup"><span data-stu-id="8e421-123">Display a window.</span></span>  
  
- <span data-ttu-id="8e421-124">ウィンドウのサイズ、位置、および外観を構成する。</span><span class="sxs-lookup"><span data-stu-id="8e421-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="8e421-125">アプリケーション固有のコンテンツをホストする。</span><span class="sxs-lookup"><span data-stu-id="8e421-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="8e421-126">ウィンドウの有効期間を管理する。</span><span class="sxs-lookup"><span data-stu-id="8e421-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a><span data-ttu-id="8e421-127">ウィンドウの実装</span><span class="sxs-lookup"><span data-stu-id="8e421-127">Implementing a Window</span></span>  
 <span data-ttu-id="8e421-128">一般的なウィンドウの実装は、外観と動作の両方で構成されます。*外観*はウィンドウがユーザーにどのように見えるかを定義し、*動作*は、ユーザーがウィンドウを操作するときにウィンドウがどのように機能するかを定義します。</span><span class="sxs-lookup"><span data-stu-id="8e421-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="8e421-129">WPF では、コードまたは [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップのいずれかを使用して、ウィンドウの外観と動作を実装できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-129">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="8e421-130">ただし、一般に、ウィンドウの外観は [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップを使用して実装され、その動作は分離コードを使用して実装されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8e421-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="8e421-131">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップファイルと分離コードファイルを連携させるには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="8e421-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="8e421-132">マークアップでは、`Window` 要素に `x:Class` 属性が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="8e421-133">アプリケーションがビルドされると、マークアップファイルに `x:Class` が存在することにより、Microsoft build engine (MSBuild) によって <xref:System.Windows.Window> から派生した `partial` クラスが作成され、`x:Class` 属性によって指定された名前になります。</span><span class="sxs-lookup"><span data-stu-id="8e421-133">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="8e421-134">そのためには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] スキーマ (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`) の XML 名前空間宣言を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-134">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="8e421-135">生成された `partial` クラスは、`InitializeComponent` メソッドを実装します。このメソッドは、イベントを登録し、マークアップで実装されるプロパティを設定するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="8e421-136">分離コードでは、クラスは、マークアップで `x:Class` 属性によって指定された名前と同じ名前を持つ `partial` クラスである必要があり、<xref:System.Windows.Window>から派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="8e421-137">これにより、分離コードファイルは、アプリケーションのビルド時にマークアップファイル用に生成される `partial` クラスに関連付けられます (「 [WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8e421-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="8e421-138">分離コードでは、<xref:System.Windows.Window> クラスは、`InitializeComponent` メソッドを呼び出すコンストラクターを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="8e421-139">`InitializeComponent` は、マークアップファイルによって生成される `partial` クラスによって実装され、イベントを登録したり、マークアップで定義されているプロパティを設定したりします。</span><span class="sxs-lookup"><span data-stu-id="8e421-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e421-140">Visual Studio を使用して新しい <xref:System.Windows.Window> をプロジェクトに追加すると、<xref:System.Windows.Window> はマークアップと分離コードの両方を使用して実装され、ここで説明するマークアップファイルと分離コードファイルの関連付けを作成するために必要な構成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8e421-140">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="8e421-141">この構成を使用して、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップでのウィンドウの外観を定義し、分離コードでその動作を実装することに集中できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="8e421-142">次の例では、ボタンが [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップに実装されているウィンドウと、コードビハインドで実装されているボタンの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントのイベントハンドラーを示します。</span><span class="sxs-lookup"><span data-stu-id="8e421-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="8e421-143">MSBuild 用のウィンドウ定義の構成</span><span class="sxs-lookup"><span data-stu-id="8e421-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="8e421-144">ウィンドウを実装する方法によって、MSBuild に対してどのように構成されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="8e421-144">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="8e421-145">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップと分離コードの両方を使用して定義されたウィンドウの場合:</span><span class="sxs-lookup"><span data-stu-id="8e421-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="8e421-146">XAML マークアップファイルは、MSBuild `Page` 項目として構成されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-146">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="8e421-147">分離コードファイルは、MSBuild `Compile` 項目として構成されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-147">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="8e421-148">これは、次の MSBuild プロジェクトファイルに示されています。</span><span class="sxs-lookup"><span data-stu-id="8e421-148">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="8e421-149">WPF アプリケーションのビルドの詳細については、「 [Wpf アプリケーションのビルド](building-a-wpf-application-wpf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e421-149">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a><span data-ttu-id="8e421-150">ウィンドウの有効期間</span><span class="sxs-lookup"><span data-stu-id="8e421-150">Window Lifetime</span></span>  
 <span data-ttu-id="8e421-151">クラスと同様に、ウィンドウにも有効期間があります。有効期間は、ウィンドウが開いて最初にインスタンス化されたときに開始し、アクティブ化と非アクティブ化を経て、最後に閉じられるまで継続します。</span><span class="sxs-lookup"><span data-stu-id="8e421-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a><span data-ttu-id="8e421-152">ウィンドウを開く</span><span class="sxs-lookup"><span data-stu-id="8e421-152">Opening a Window</span></span>  
 <span data-ttu-id="8e421-153">ウィンドウを開くには、次の例に示すように最初にインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e421-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="8e421-154">この例では、アプリケーションの起動時に、`MarkupAndCodeBehindWindow` がインスタンス化されます。これは、<xref:System.Windows.Application.Startup> イベントが発生したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8e421-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="8e421-155">ウィンドウがインスタンス化されると、そのウィンドウへの参照が、<xref:System.Windows.Application> オブジェクトによって管理されるウィンドウの一覧に自動的に追加されます (<xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>を参照)。</span><span class="sxs-lookup"><span data-stu-id="8e421-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="8e421-156">また、既定では、インスタンス化される最初のウィンドウは、メインアプリケーションウィンドウとして <xref:System.Windows.Application> によって設定されます (<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8e421-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="8e421-157">最後に、<xref:System.Windows.Window.Show%2A> メソッドを呼び出してウィンドウを開きます。結果を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="8e421-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Window. Show を呼び出して開かれたウィンドウです。](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="8e421-159"><xref:System.Windows.Window.Show%2A> を呼び出すことによって開かれるウィンドウは、モードレスウィンドウです。つまり、アプリケーションは、ユーザーが同じアプリケーション内の他のウィンドウをアクティブ化できるモードで動作します。</span><span class="sxs-lookup"><span data-stu-id="8e421-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e421-160">ダイアログボックスなどのウィンドウをモーダルで開くために <xref:System.Windows.Window.ShowDialog%2A> が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="8e421-161">詳細については、「[ダイアログボックスの概要](dialog-boxes-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e421-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="8e421-162"><xref:System.Windows.Window.Show%2A> が呼び出されると、ウィンドウは、ユーザー入力を受け取ることを許可するインフラストラクチャを確立するために、表示される前に初期化作業を実行します。</span><span class="sxs-lookup"><span data-stu-id="8e421-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="8e421-163">ウィンドウが初期化されると、<xref:System.Windows.Window.SourceInitialized> イベントが発生し、ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="8e421-164">ショートカットとして、<xref:System.Windows.Application.StartupUri%2A> を設定して、アプリケーションの起動時に自動的に開かれる最初のウィンドウを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="8e421-165">アプリケーションが起動すると、<xref:System.Windows.Application.StartupUri%2A> の値によって指定されたウィンドウがモードレスで; に開かれます。内部的には、<xref:System.Windows.Window.Show%2A> メソッドを呼び出すことによってウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="8e421-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a><span data-ttu-id="8e421-166">ウィンドウの所有権</span><span class="sxs-lookup"><span data-stu-id="8e421-166">Window Ownership</span></span>  
 <span data-ttu-id="8e421-167"><xref:System.Windows.Window.Show%2A> メソッドを使用して開いたウィンドウには、それを作成したウィンドウとの暗黙的な関係がありません。ユーザーは、どちらのウィンドウとも独立して対話できます。つまり、どちらのウィンドウも次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="8e421-168">もう一方をカバーします (いずれかのウィンドウの [<xref:System.Windows.Window.Topmost%2A>] プロパティが [`true`] に設定されている場合を除きます)。</span><span class="sxs-lookup"><span data-stu-id="8e421-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="8e421-169">もう一方のウィンドウに影響を与えずに、最小化/最大化し、元のサイズに戻す。</span><span class="sxs-lookup"><span data-stu-id="8e421-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="8e421-170">一部のウィンドウには、そのウィンドウを開いたウィンドウとの関係が必要です。</span><span class="sxs-lookup"><span data-stu-id="8e421-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="8e421-171">たとえば、統合開発環境 (IDE: Integrated Development Environment) アプリケーションでは、プロパティウィンドウとツールウィンドウを開くことができます。このウィンドウは、通常の動作が、そのウィンドウを作成するウィンドウをカバーするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-171">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="8e421-172">また、そのようなウィンドウは、必ず作成元のウィンドウと一緒に閉じ、最小化/最大化し、元のサイズに戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="8e421-173">このような関係を確立するには、1*つのウィンドウを別の*ウィンドウにし、所有*ウィンドウ*の [<xref:System.Windows.Window.Owner%2A>] プロパティに [*所有者] ウィンドウ*への参照を設定します。</span><span class="sxs-lookup"><span data-stu-id="8e421-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="8e421-174">これを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="8e421-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="8e421-175">所有権が確立されると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8e421-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="8e421-176">所有ウィンドウは、その <xref:System.Windows.Window.Owner%2A> プロパティの値を調べることによって所有者ウィンドウを参照できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="8e421-177">[所有者] ウィンドウでは、<xref:System.Windows.Window.OwnedWindows%2A> プロパティの値を調べることによって、所有しているすべてのウィンドウを検出できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a><span data-ttu-id="8e421-178">ウィンドウのアクティブ化の防止</span><span class="sxs-lookup"><span data-stu-id="8e421-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="8e421-179">表示されたときにウィンドウをアクティブにしないシナリオがあります。たとえば、電子メールアプリケーションのインターネット messenger スタイルのアプリケーションや通知ウィンドウのメッセージ交換ウィンドウなどです。</span><span class="sxs-lookup"><span data-stu-id="8e421-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="8e421-180">アプリケーションに、表示されたときにアクティブにならないウィンドウがある場合は、<xref:System.Windows.Window.Show%2A> メソッドを初めて呼び出す前に、その <xref:System.Windows.Window.ShowActivated%2A> プロパティを `false` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="8e421-181">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8e421-181">As a consequence:</span></span>  
  
- <span data-ttu-id="8e421-182">ウィンドウはアクティブになりません。</span><span class="sxs-lookup"><span data-stu-id="8e421-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="8e421-183">ウィンドウの <xref:System.Windows.Window.Activated> イベントが発生していません。</span><span class="sxs-lookup"><span data-stu-id="8e421-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="8e421-184">現在アクティブなウィンドウは、アクティブのままです。</span><span class="sxs-lookup"><span data-stu-id="8e421-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="8e421-185">ただし、ユーザーがクライアント領域または非クライアント領域をクリックすると、ウィンドウは直ちにアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="8e421-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="8e421-186">この場合、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8e421-186">In this case:</span></span>  
  
- <span data-ttu-id="8e421-187">ウィンドウはアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="8e421-187">The window is activated.</span></span>  
  
- <span data-ttu-id="8e421-188">ウィンドウの <xref:System.Windows.Window.Activated> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="8e421-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="8e421-189">直前にアクティブだったウィンドウは非アクティブになります。</span><span class="sxs-lookup"><span data-stu-id="8e421-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="8e421-190">その後、ユーザーの操作に応答して、ウィンドウの <xref:System.Windows.Window.Deactivated> イベントと <xref:System.Windows.Window.Activated> イベントが期待どおりに発生します。</span><span class="sxs-lookup"><span data-stu-id="8e421-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a><span data-ttu-id="8e421-191">ウィンドウのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="8e421-191">Window Activation</span></span>  
 <span data-ttu-id="8e421-192">ウィンドウを初めて開いたときには、アクティブなウィンドウになります (<xref:System.Windows.Window.ShowActivated%2A> が `false`に設定されている場合を除きます)。</span><span class="sxs-lookup"><span data-stu-id="8e421-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="8e421-193">*アクティブウィンドウ*は、キーストロークやマウスクリックなど、現在ユーザー入力をキャプチャしているウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="8e421-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="8e421-194">ウィンドウがアクティブになると、<xref:System.Windows.Window.Activated> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="8e421-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e421-195">ウィンドウを最初に開いたときに、<xref:System.Windows.FrameworkElement.Loaded> イベントと <xref:System.Windows.Window.ContentRendered> イベントが発生するのは、<xref:System.Windows.Window.Activated> イベントが発生した後だけです。</span><span class="sxs-lookup"><span data-stu-id="8e421-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="8e421-196">これを念頭に置いて、<xref:System.Windows.Window.ContentRendered> が発生したときに、ウィンドウを効果的に開いていると見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="8e421-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="8e421-197">ウィンドウがアクティブになった後で、ユーザーは同じアプリケーションの別のウィンドウをアクティブ化したり、別のアプリケーションをアクティブ化したりできます。</span><span class="sxs-lookup"><span data-stu-id="8e421-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="8e421-198">これが発生すると、現在アクティブなウィンドウが非アクティブ化され、<xref:System.Windows.Window.Deactivated> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="8e421-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="8e421-199">同様に、ユーザーが現在非アクティブになっているウィンドウを選択すると、ウィンドウが再びアクティブになり <xref:System.Windows.Window.Activated> が発生します。</span><span class="sxs-lookup"><span data-stu-id="8e421-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="8e421-200"><xref:System.Windows.Window.Activated> と <xref:System.Windows.Window.Deactivated> を処理する一般的な理由の1つは、ウィンドウがアクティブなときにのみ実行できる機能を有効または無効にすることです。</span><span class="sxs-lookup"><span data-stu-id="8e421-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="8e421-201">たとえば、ゲームやビデオ プレーヤーなど、ユーザーの一定の入力や介入が必要な対話型コンテンツが表示されるウィンドウがあります。</span><span class="sxs-lookup"><span data-stu-id="8e421-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="8e421-202">次の例は、この動作を実装するために <xref:System.Windows.Window.Activated> と <xref:System.Windows.Window.Deactivated> を処理する方法を示す簡略化されたビデオプレーヤーです。</span><span class="sxs-lookup"><span data-stu-id="8e421-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="8e421-203">ウィンドウが非アクティブでも、バックグラウンドでコードを実行できる種類のアプリケーションもあります。</span><span class="sxs-lookup"><span data-stu-id="8e421-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="8e421-204">たとえば、メール クライアントは、ユーザーが他のアプリケーションを使用している間もメール サーバーへのポーリングを続けています。</span><span class="sxs-lookup"><span data-stu-id="8e421-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="8e421-205">このようなアプリケーションは、メイン ウィンドウが非アクティブのときにも、別の動作や追加の動作を頻繁に実行します。</span><span class="sxs-lookup"><span data-stu-id="8e421-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="8e421-206">メール プログラムでは、新しいメール アイテムを受信トレイに追加し、通知アイコンをシステム トレイに追加することがあります。</span><span class="sxs-lookup"><span data-stu-id="8e421-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="8e421-207">通知アイコンは、メールウィンドウがアクティブでない場合にのみ表示する必要があります。これは、<xref:System.Windows.Window.IsActive%2A> プロパティを調べることによって決定できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="8e421-208">バックグラウンドタスクが完了すると、<xref:System.Windows.Window.Activate%2A> メソッドを呼び出すことにより、ユーザーにより緊急通知を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8e421-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="8e421-209"><xref:System.Windows.Window.Activate%2A> が呼び出されたときに、ユーザーが別のアプリケーションと対話している場合は、ウィンドウのタスクバーボタンが点滅します。</span><span class="sxs-lookup"><span data-stu-id="8e421-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="8e421-210">ユーザーが現在のアプリケーションと対話している場合は、<xref:System.Windows.Window.Activate%2A> を呼び出すとウィンドウが前面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e421-211"><xref:System.Windows.Application.Activated?displayProperty=nameWithType> イベントと <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> イベントを使用して、アプリケーションスコープのアクティブ化を処理できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a><span data-ttu-id="8e421-212">ウィンドウを閉じる</span><span class="sxs-lookup"><span data-stu-id="8e421-212">Closing a Window</span></span>  
 <span data-ttu-id="8e421-213">ウィンドウの有効期間は、表示されたときに開始し、ユーザーが閉じたときに終了します。</span><span class="sxs-lookup"><span data-stu-id="8e421-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="8e421-214">ウィンドウを閉じるには、非クライアント領域の要素を使用します。これには、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8e421-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="8e421-215">**システム**メニューの**閉じる**項目。</span><span class="sxs-lookup"><span data-stu-id="8e421-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="8e421-216">Alt キーを押しながら F4 キーを押す。</span><span class="sxs-lookup"><span data-stu-id="8e421-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="8e421-217">**[閉じる]** ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="8e421-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="8e421-218">クライアント領域にさらに機構を追加してウィンドウを閉じることもできます。その一般的な例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="8e421-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="8e421-219">通常はメインアプリケーションウィンドウの **[ファイル]** メニューの **[終了]** 項目。</span><span class="sxs-lookup"><span data-stu-id="8e421-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="8e421-220">通常はセカンダリアプリケーションウィンドウで、 **[ファイル]** メニューの **[閉じる]** 項目。</span><span class="sxs-lookup"><span data-stu-id="8e421-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="8e421-221">**[キャンセル**] ボタン (通常はモーダルダイアログボックス)。</span><span class="sxs-lookup"><span data-stu-id="8e421-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="8e421-222">**[閉じる]** ボタン。通常は、モードレスダイアログボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="8e421-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="8e421-223">これらのカスタム機構のいずれかに応答してウィンドウを閉じるには、<xref:System.Windows.Window.Close%2A> メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="8e421-224">次の例では、 **[ファイル]** メニューの **[終了]** をクリックして、ウィンドウを閉じる機能を実装しています。</span><span class="sxs-lookup"><span data-stu-id="8e421-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="8e421-225">ウィンドウが閉じると、<xref:System.Windows.Window.Closing> と <xref:System.Windows.Window.Closed>の2つのイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="8e421-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="8e421-226">ウィンドウが閉じられる前に <xref:System.Windows.Window.Closing> が発生し、ウィンドウを閉じることができないようにするためのメカニズムが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8e421-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="8e421-227">ウィンドウが閉じるのを防ぐのは、一般的に、ウィンドウ コンテンツに変更したデータが含まれている場合です。</span><span class="sxs-lookup"><span data-stu-id="8e421-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="8e421-228">このような状況では、<xref:System.Windows.Window.Closing> イベントを処理して、データがダーティかどうかを判断し、データがダーティであるかどうかを判断し、データを保存せずにウィンドウを閉じるか、ウィンドウの終了を取り消すかどうかをユーザーに確認することができます。</span><span class="sxs-lookup"><span data-stu-id="8e421-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="8e421-229">次の例は、<xref:System.Windows.Window.Closing>を処理する主な側面を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e421-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="8e421-230"><xref:System.Windows.Window.Closing> イベントハンドラーには <xref:System.ComponentModel.CancelEventArgs>が渡されます。これは、ウィンドウが閉じられないように `true` に設定した `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> プロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="8e421-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="8e421-231"><xref:System.Windows.Window.Closing> が処理されない場合、または処理されても取り消されない場合は、ウィンドウが閉じます。</span><span class="sxs-lookup"><span data-stu-id="8e421-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="8e421-232">ウィンドウが実際に閉じられる直前に、<xref:System.Windows.Window.Closed> が発生します。</span><span class="sxs-lookup"><span data-stu-id="8e421-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="8e421-233">この時点で、ウィンドウが閉じるのを防ぐことはできません。</span><span class="sxs-lookup"><span data-stu-id="8e421-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e421-234">メインアプリケーションウィンドウを閉じるか、最後のウィンドウを閉じると、アプリケーションを自動的にシャットダウンするように構成できます (「<xref:System.Windows.Application.MainWindow%2A>」を参照)。</span><span class="sxs-lookup"><span data-stu-id="8e421-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="8e421-235">詳細については、「<xref:System.Windows.Application.ShutdownMode%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e421-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="8e421-236">ウィンドウは、非クライアント領域とクライアント領域に用意されている機構を使用して明示的に閉じることができますが、次のようなアプリケーションまたはウィンドウの他の部分での動作の結果として、ウィンドウを暗黙的に閉じることもできます。</span><span class="sxs-lookup"><span data-stu-id="8e421-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="8e421-237">ユーザーは、Windows をログオフまたはシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="8e421-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="8e421-238">ウィンドウの所有者が閉じます (「<xref:System.Windows.Window.Owner%2A>)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e421-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="8e421-239">メインアプリケーションウィンドウが閉じられ、<xref:System.Windows.Application.ShutdownMode%2A> が <xref:System.Windows.ShutdownMode.OnMainWindowClose>ます。</span><span class="sxs-lookup"><span data-stu-id="8e421-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="8e421-240"><xref:System.Windows.Application.Shutdown%2A> が呼ばれたとき。</span><span class="sxs-lookup"><span data-stu-id="8e421-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e421-241">ウィンドウを閉じると、再度開くことはできません。</span><span class="sxs-lookup"><span data-stu-id="8e421-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a><span data-ttu-id="8e421-242">ウィンドウの有効期間イベント</span><span class="sxs-lookup"><span data-stu-id="8e421-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="8e421-243">次の図は、ウィンドウの有効期間におけるプリンシパルイベントのシーケンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="8e421-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![ウィンドウの有効期間内のイベントを表示する図。](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="8e421-245">次の図は、アクティブ化せずに表示されるウィンドウの有効期間におけるプリンシパルイベントのシーケンスを示しています (<xref:System.Windows.Window.ShowActivated%2A> は、ウィンドウが表示される前に `false` に設定されています)。</span><span class="sxs-lookup"><span data-stu-id="8e421-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![アクティブ化を行わずに、ウィンドウの有効期間内のイベントを表示する図。](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a><span data-ttu-id="8e421-247">ウィンドウの位置</span><span class="sxs-lookup"><span data-stu-id="8e421-247">Window Location</span></span>  
 <span data-ttu-id="8e421-248">ウィンドウが開いているとき、ウィンドウはデスクトップに対して相対的な x ディメンションと y ディメンションの位置にあります。</span><span class="sxs-lookup"><span data-stu-id="8e421-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="8e421-249">この場所は、<xref:System.Windows.Window.Left%2A> と <xref:System.Windows.Window.Top%2A> のプロパティをそれぞれ調べることによって決定できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="8e421-250">これらのプロパティを設定して、ウィンドウの位置を変更できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="8e421-251">また、<xref:System.Windows.Window.WindowStartupLocation%2A> プロパティに次のいずれかの <xref:System.Windows.WindowStartupLocation> 列挙値を設定して最初に表示されたときに <xref:System.Windows.Window> の初期位置を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="8e421-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="8e421-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (既定)</span><span class="sxs-lookup"><span data-stu-id="8e421-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="8e421-253">起動時の場所が <xref:System.Windows.WindowStartupLocation.Manual>として指定され、<xref:System.Windows.Window.Left%2A> プロパティと <xref:System.Windows.Window.Top%2A> プロパティが設定されていない場合 <xref:System.Windows.Window> は、に表示される場所を Windows に確認します。</span><span class="sxs-lookup"><span data-stu-id="8e421-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="8e421-254">最上位ウィンドウと Z オーダー</span><span class="sxs-lookup"><span data-stu-id="8e421-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="8e421-255">ウィンドウには、x 位置と y 位置に加えて、他のウィンドウを基準にして垂直位置を決定する z ディメンションの位置もあります。</span><span class="sxs-lookup"><span data-stu-id="8e421-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="8e421-256">これはウィンドウの z オーダーともいい、標準 z オーダーと最上位 z オーダーの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="8e421-257">*通常の z オーダー*におけるウィンドウの位置は、現在アクティブかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="8e421-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="8e421-258">既定では、ウィンドウは標準 z オーダーにあります。</span><span class="sxs-lookup"><span data-stu-id="8e421-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="8e421-259">*最上位 z オーダー*のウィンドウの位置は、現在アクティブかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="8e421-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="8e421-260">また、最上位 z オーダーにあるウィンドウは、常に、標準 z オーダーにあるウィンドウの上に位置します。</span><span class="sxs-lookup"><span data-stu-id="8e421-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="8e421-261">ウィンドウは、その <xref:System.Windows.Window.Topmost%2A> プロパティを `true`に設定することにより、最上位の z オーダーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="8e421-262">各 z オーダー内では、現在アクティブなウィンドウは、同じ z オーダーにある他のすべてのウィンドウの上に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a><span data-ttu-id="8e421-263">ウィンドウ サイズ</span><span class="sxs-lookup"><span data-stu-id="8e421-263">Window Size</span></span>  
 <span data-ttu-id="8e421-264">ウィンドウのサイズは、デスクトップの位置を指定するだけでなく、さまざまな幅と高さのプロパティ、<xref:System.Windows.Window.SizeToContent%2A>など、いくつかのプロパティによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="8e421-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>、<xref:System.Windows.FrameworkElement.Width%2A>、および <xref:System.Windows.FrameworkElement.MaxWidth%2A> は、有効期間中にウィンドウが持つことができる幅の範囲を管理するために使用され、次の例に示すように構成されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="8e421-266">ウィンドウの高さは、<xref:System.Windows.FrameworkElement.MinHeight%2A>、<xref:System.Windows.FrameworkElement.Height%2A>、および <xref:System.Windows.FrameworkElement.MaxHeight%2A>によって管理され、次の例に示すように構成されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="8e421-267">さまざまな幅の値と高さの値はそれぞれ範囲を指定しているため、サイズを変更できるウィンドウの幅と高さは、それぞれの寸法に指定された範囲内のいずれかの値を取ります。</span><span class="sxs-lookup"><span data-stu-id="8e421-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="8e421-268">現在の幅と高さを検出するには、<xref:System.Windows.FrameworkElement.ActualWidth%2A> と <xref:System.Windows.FrameworkElement.ActualHeight%2A>をそれぞれ調べます。</span><span class="sxs-lookup"><span data-stu-id="8e421-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="8e421-269">ウィンドウの幅と高さに、ウィンドウのコンテンツのサイズに合わせてサイズを設定する場合は、次の値を持つ <xref:System.Windows.Window.SizeToContent%2A> プロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="8e421-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="8e421-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="8e421-271">効果 (既定値)。</span><span class="sxs-lookup"><span data-stu-id="8e421-271">No effect (default).</span></span>  
  
- <span data-ttu-id="8e421-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="8e421-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="8e421-273">コンテンツの幅に合わせる。 <xref:System.Windows.FrameworkElement.MinWidth%2A> と <xref:System.Windows.FrameworkElement.MaxWidth%2A> の両方をコンテンツの幅に設定するのと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="8e421-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="8e421-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="8e421-275">コンテンツの高さに合わせる。 <xref:System.Windows.FrameworkElement.MinHeight%2A> と <xref:System.Windows.FrameworkElement.MaxHeight%2A> の両方をコンテンツの高さに設定するのと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="8e421-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="8e421-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="8e421-277">コンテンツの幅と高さに合わせる。 <xref:System.Windows.FrameworkElement.MinHeight%2A> と <xref:System.Windows.FrameworkElement.MaxHeight%2A> の両方をコンテンツの高さに設定し、<xref:System.Windows.FrameworkElement.MinWidth%2A> と <xref:System.Windows.FrameworkElement.MaxWidth%2A> の両方をコンテンツの幅に設定した場合と同じ効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="8e421-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="8e421-278">次の例では、ウィンドウを最初に表示するときに、そのコンテンツに合わせて垂直方向と水平方向の両方のサイズを自動的に変更するウィンドウを示しています。</span><span class="sxs-lookup"><span data-stu-id="8e421-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="8e421-279">次の例では、コンテンツに合わせてウィンドウのサイズを変更する方法を指定するために、コードで <xref:System.Windows.Window.SizeToContent%2A> プロパティを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8e421-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="8e421-280">サイズ変更プロパティの優先順位</span><span class="sxs-lookup"><span data-stu-id="8e421-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="8e421-281">基本的に、ウィンドウのさまざまなサイズのプロパティを組み合わせて、サイズを変更できるウィンドウの幅と高さの範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="8e421-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="8e421-282">有効な範囲を確実に維持するために、<xref:System.Windows.Window> は次の優先順位を使用してサイズプロパティの値を評価します。</span><span class="sxs-lookup"><span data-stu-id="8e421-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="8e421-283">**高さのプロパティ:**</span><span class="sxs-lookup"><span data-stu-id="8e421-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="8e421-284">**幅のプロパティ:**</span><span class="sxs-lookup"><span data-stu-id="8e421-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="8e421-285">優先順位は、ウィンドウが最大化されたときのサイズを決定することもできます。これは、<xref:System.Windows.Window.WindowState%2A> プロパティを使用して管理されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>   
## <a name="window-state"></a><span data-ttu-id="8e421-286">ウィンドウの状態</span><span class="sxs-lookup"><span data-stu-id="8e421-286">Window State</span></span>  
 <span data-ttu-id="8e421-287">サイズを変更できるウィンドウには、有効期間中、通常、最小化、最大化の 3 つの状態があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="8e421-288">*通常*の状態のウィンドウは、ウィンドウの既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="8e421-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="8e421-289">この状態のウィンドウは、サイズ変更グリップ、またはサイズ変更可能な場合は境界線を使用して、ユーザーが移動したりサイズ変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="8e421-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="8e421-290"><xref:System.Windows.Window.ShowInTaskbar%2A> が `true`に設定されている場合、*最小化*された状態のウィンドウは、タスクバーボタンに折りたたまれます。それ以外の場合は、可能な限り小さいサイズに縮小され、デスクトップの左下隅に再配置されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="8e421-291">最小化されたウィンドウはいずれの種類も、境界線またはサイズ変更グリップを使用してサイズ変更できません。ただし、タスク バーに表示されていない最小化されたウィンドウはデスクトップの任意の場所にドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="8e421-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="8e421-292">最大化され*た状態の*ウィンドウは、最大サイズに拡張されます。これは、<xref:System.Windows.FrameworkElement.MaxWidth%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>、および <xref:System.Windows.Window.SizeToContent%2A> プロパティによって決まります。</span><span class="sxs-lookup"><span data-stu-id="8e421-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="8e421-293">最小化されたウィンドウと同様、最大化されたウィンドウは、サイズ変更グリップを使用したり、境界線をドラッグしたりすることによってサイズ変更できません。</span><span class="sxs-lookup"><span data-stu-id="8e421-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e421-294">ウィンドウの <xref:System.Windows.Window.Top%2A>、<xref:System.Windows.Window.Left%2A>、<xref:System.Windows.FrameworkElement.Width%2A>、および <xref:System.Windows.FrameworkElement.Height%2A> の各プロパティの値は、ウィンドウが現在最大化または最小化されている場合でも、常に通常の状態の値を表します。</span><span class="sxs-lookup"><span data-stu-id="8e421-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="8e421-295">ウィンドウの状態を構成するには、その <xref:System.Windows.Window.WindowState%2A> プロパティを設定します。次の <xref:System.Windows.WindowState> 列挙値のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="8e421-296"><xref:System.Windows.WindowState.Normal> (既定)</span><span class="sxs-lookup"><span data-stu-id="8e421-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="8e421-297">開くときに最大化されて表示されるウィンドウを作成する方法を、次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="8e421-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="8e421-298">一般に、ウィンドウの初期状態を構成するには <xref:System.Windows.Window.WindowState%2A> を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="8e421-299">サイズ変更可能なウィンドウが表示されると、ユーザーはウィンドウのタイトル バーにある最小化ボタン、最大化ボタン、および元に戻すボタンを使用して、ウィンドウの状態を変更できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a><span data-ttu-id="8e421-300">ウィンドウの外観</span><span class="sxs-lookup"><span data-stu-id="8e421-300">Window Appearance</span></span>  
 <span data-ttu-id="8e421-301">ウィンドウのクライアント領域の外観を変更するために、ボタン、ラベル、テキスト ボックスなど、ウィンドウ固有のコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="8e421-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="8e421-302">非クライアント領域を構成するために、<xref:System.Windows.Window> にはいくつかのプロパティが用意され <xref:System.Windows.Window.Title%2A> ています。これには、ウィンドウのアイコンを設定したり、タイトルを設定したりするための <xref:System.Windows.Window.Icon%2A> が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8e421-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="8e421-303">また、ウィンドウのサイズ変更モード、ウィンドウ スタイル、デスクトップのタスク バーにボタンとして表示するかどうかを構成して、非クライアント領域の境界線の外観と動作も変更できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a><span data-ttu-id="8e421-304">サイズ変更モード</span><span class="sxs-lookup"><span data-stu-id="8e421-304">Resize Mode</span></span>  
 <span data-ttu-id="8e421-305"><xref:System.Windows.Window.WindowStyle%2A> プロパティに応じて、ユーザーがウィンドウのサイズを変更する方法 (および場合) を制御できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="8e421-306">ウィンドウスタイルの選択は、ユーザーがマウスで境界線をドラッグしてウィンドウのサイズを変更できるかどうか、非クライアント領域に**最小化**、**最大化**、および**サイズ変更**の各ボタンが表示されるかどうか、また、有効になっているかどうかにかかわらず、表示されるかどうかに影響します。</span><span class="sxs-lookup"><span data-stu-id="8e421-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="8e421-307"><xref:System.Windows.Window.ResizeMode%2A> プロパティを設定して、ウィンドウのサイズを変更する方法を構成できます。これは、次の <xref:System.Windows.ResizeMode> 列挙値のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="8e421-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="8e421-308"><xref:System.Windows.ResizeMode.CanResize> (既定)</span><span class="sxs-lookup"><span data-stu-id="8e421-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="8e421-309"><xref:System.Windows.Window.WindowStyle%2A>と同様に、ウィンドウのサイズ変更モードは、その有効期間中に変更される可能性はほとんどありません。つまり、ほとんどの場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップから設定されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="8e421-310"><xref:System.Windows.Window.WindowState%2A> プロパティを調べることで、ウィンドウが最大化、最小化、または復元されているかどうかを検出できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a><span data-ttu-id="8e421-311">ウィンドウ スタイル</span><span class="sxs-lookup"><span data-stu-id="8e421-311">Window Style</span></span>  
 <span data-ttu-id="8e421-312">ウィンドウの非クライアント領域から公開される境界線は、多くのアプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="8e421-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="8e421-313">ただし、ウィンドウの種類によって、異なる種類の境界線が必要な状況や、境界線がまったく必要ない状況があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="8e421-314">ウィンドウで取得する境界線の種類を制御するには、その <xref:System.Windows.Window.WindowStyle%2A> プロパティを、<xref:System.Windows.WindowStyle> 列挙体の次のいずれかの値に設定します。</span><span class="sxs-lookup"><span data-stu-id="8e421-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="8e421-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (既定)</span><span class="sxs-lookup"><span data-stu-id="8e421-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="8e421-316">これらのウィンドウスタイルの効果を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="8e421-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![ウィンドウの境界線スタイルの図。](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="8e421-318">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップまたはコードのいずれかを使用して <xref:System.Windows.Window.WindowStyle%2A> を設定できます。ウィンドウの有効期間中は変更される可能性が低いため、ほとんどの場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップを使用して構成します。</span><span class="sxs-lookup"><span data-stu-id="8e421-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="8e421-319">四角形以外のウィンドウ スタイル</span><span class="sxs-lookup"><span data-stu-id="8e421-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="8e421-320"><xref:System.Windows.Window.WindowStyle%2A> に許可されている罫線のスタイルでは不十分な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="8e421-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="8e421-321">たとえば、Microsoft Windows Media Player で使用するような、四角形以外の境界線を持つアプリケーションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="8e421-321">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="8e421-322">たとえば、次の図に示すように、音声バブルウィンドウについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="8e421-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 !["ドラッグアンドドロップ" という音声バブルウィンドウ。](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="8e421-324">この種類のウィンドウを作成するには、[<xref:System.Windows.Window.WindowStyle%2A>] プロパティを <xref:System.Windows.WindowStyle.None>に設定し、透明度に <xref:System.Windows.Window> の特別なサポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="8e421-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="8e421-325">値をこの組み合わせで使用し、ウィンドウが完全に透明にレンダリングされるように設定します。</span><span class="sxs-lookup"><span data-stu-id="8e421-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="8e421-326">この状態では、ウィンドウの非クライアント領域の表示要素 (閉じるメニュー、最小化ボタン、最大化ボタン、元に戻すボタンなど) は使用できません。</span><span class="sxs-lookup"><span data-stu-id="8e421-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="8e421-327">したがって、独自の表示要素を用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a><span data-ttu-id="8e421-328">タスク バーのプレゼンス</span><span class="sxs-lookup"><span data-stu-id="8e421-328">Task Bar Presence</span></span>  

<span data-ttu-id="8e421-329">ウィンドウの既定の外観には、次の図に示すようなタスクバーボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![タスクバーボタンのあるウィンドウを示すスクリーンショット。](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="8e421-331">ウィンドウの種類によっては、メッセージボックスやダイアログボックスなどのタスクバーボタンが表示されない場合があります (「[ダイアログボックスの概要](dialog-boxes-overview.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8e421-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="8e421-332"><xref:System.Windows.Window.ShowInTaskbar%2A> プロパティ (既定では`true`) を設定して、ウィンドウのタスクバーボタンを表示するかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="8e421-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a><span data-ttu-id="8e421-333">セキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="8e421-333">Security Considerations</span></span>  
 <span data-ttu-id="8e421-334"><xref:System.Windows.Window> には、`UnmanagedCode` セキュリティ権限をインスタンス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="8e421-335">ローカル コンピューターにインストールされ、ローカル コンピューターから起動されるアプリケーションの場合は、アプリケーションに付与されるアクセス許可セットの範囲内になります。</span><span class="sxs-lookup"><span data-stu-id="8e421-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="8e421-336">ただし、これは、ClickOnce を使用してインターネットまたはローカルイントラネットゾーンから起動されるアプリケーションに付与されるアクセス許可のセットの範囲外です。</span><span class="sxs-lookup"><span data-stu-id="8e421-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="8e421-337">その結果、ユーザーには ClickOnce のセキュリティ警告が表示され、アプリケーションのアクセス許可セットを完全信頼に昇格させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e421-337">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="8e421-338">また、Xbap では既定でウィンドウまたはダイアログボックスを表示できません。</span><span class="sxs-lookup"><span data-stu-id="8e421-338">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="8e421-339">スタンドアロンアプリケーションのセキュリティに関する考慮事項については、「 [WPF のセキュリティ方針-プラットフォームのセキュリティ](../wpf-security-strategy-platform-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e421-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a><span data-ttu-id="8e421-340">その他の種類のウィンドウ</span><span class="sxs-lookup"><span data-stu-id="8e421-340">Other Types of Windows</span></span>  
 <span data-ttu-id="8e421-341"><xref:System.Windows.Navigation.NavigationWindow> は、誘導可能なコンテンツをホストするように設計されたウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="8e421-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="8e421-342">詳細については、「[ナビゲーションの概要](navigation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e421-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="8e421-343">ダイアログ ボックスは、ユーザーから情報を収集して機能を完了するためによく使用されるウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="8e421-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="8e421-344">たとえば、ユーザーがファイルを開こうとした場合、通常、 **[ファイルを開く]** ダイアログボックスは、ユーザーからファイル名を取得するためにアプリケーションによって表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e421-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="8e421-345">詳細については、「[ダイアログ ボックスの概要](dialog-boxes-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e421-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e421-346">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e421-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="8e421-347">ダイアログ ボックスの概要</span><span class="sxs-lookup"><span data-stu-id="8e421-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="8e421-348">WPF アプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="8e421-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
