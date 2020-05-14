---
title: XAML ブラウザー アプリケーションの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
ms.openlocfilehash: 825b689dea145d18035344cd902ea1b8a50e82c3
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124209"
---
# <a name="wpf-xaml-browser-applications-overview"></a><span data-ttu-id="4c39f-102">WPF XAML ブラウザー アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="4c39f-102">WPF XAML Browser Applications Overview</span></span>
<a name="introduction"></a> <span data-ttu-id="4c39f-103">XAML ブラウザー アプリケーション (XBAP) は、Web アプリケーションとリッチ クライアント アプリケーションの両方の機能を兼ね備えています。</span><span class="sxs-lookup"><span data-stu-id="4c39f-103">XAML browser applications (XBAPs) combines features of both Web applications and rich-client applications.</span></span> <span data-ttu-id="4c39f-104">たとえば、Web アプリケーションと同様、Web サーバーに配置して、Internet Explorer または Firefox から開始できます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-104">Like Web applications, XBAPs can be deployed to a Web server and started from Internet Explorer or Firefox.</span></span> <span data-ttu-id="4c39f-105">また、リッチ クライアント アプリケーションと同様、WPF の機能を利用することができます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-105">Like rich-client applications, XBAPs can take advantage of the capabilities of WPF.</span></span> <span data-ttu-id="4c39f-106">XBAP の開発方法もリッチ クライアントの開発に似ています。</span><span class="sxs-lookup"><span data-stu-id="4c39f-106">Developing XBAPs is also similar to rich-client development.</span></span> <span data-ttu-id="4c39f-107">このトピックでは、XBAP 開発の概要を示し、XBAP 開発が標準的なリッチ クライアント開発と異なる点について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-107">This topic provides a simple, high-level introduction to XBAP development and describes where XBAP development differs from standard rich-client development.</span></span>

 <span data-ttu-id="4c39f-108">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="4c39f-108">This topic contains the following sections:</span></span>

- [<span data-ttu-id="4c39f-109">新しい XAML ブラウザー アプリケーション (XBAP) の作成</span><span class="sxs-lookup"><span data-stu-id="4c39f-109">Creating a New XAML Browser Application (XBAP)</span></span>](#creating_a_new_xaml_browser_application_xbap)

- [<span data-ttu-id="4c39f-110">XBAP の配置</span><span class="sxs-lookup"><span data-stu-id="4c39f-110">Deploying an XBAP</span></span>](#deploying_a_xbap)

- [<span data-ttu-id="4c39f-111">ホスト Web ページとの通信</span><span class="sxs-lookup"><span data-stu-id="4c39f-111">Communicating with the Host Web Page</span></span>](#communicating_with_the_host_web_page)

- [<span data-ttu-id="4c39f-112">XBAP セキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="4c39f-112">XBAP Security Considerations</span></span>](#xbap_security_considerations)

- [<span data-ttu-id="4c39f-113">XBAP 起動時のパフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="4c39f-113">XBAP Start Time Performance Considerations</span></span>](#xbap_start_time_performance_considerations)

<a name="creating_a_new_xaml_browser_application_xbap"></a>
## <a name="creating-a-new-xaml-browser-application-xbap"></a><span data-ttu-id="4c39f-114">新しい XAML ブラウザー アプリケーション (XBAP) の作成</span><span class="sxs-lookup"><span data-stu-id="4c39f-114">Creating a New XAML Browser Application (XBAP)</span></span>
 <span data-ttu-id="4c39f-115">新しい XBAP プロジェクトを作成する最も簡単な方法は、Visual Studio を使用することです。</span><span class="sxs-lookup"><span data-stu-id="4c39f-115">The simplest way to create a new XBAP project is with Visual Studio.</span></span> <span data-ttu-id="4c39f-116">新しいプロジェクトを作成するときに、テンプレートの一覧で **[WPF ブラウザー アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-116">When creating a new project, select **WPF Browser Application** from the list of templates.</span></span> <span data-ttu-id="4c39f-117">詳細については、[新しい WPF ブラウザー アプリケーション プロジェクトを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c39f-117">For more information, see [How to: Create a New WPF Browser Application Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).</span></span>

 <span data-ttu-id="4c39f-118">XBAP プロジェクトを実行すると、そのプロジェクトは、スタンドアロン ウィンドウではなくブラウザー ウィンドウで開きます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-118">When you run the XBAP project, it opens in a browser window instead of a stand-alone window.</span></span> <span data-ttu-id="4c39f-119">XBAP を Visual Studio でデバッグするとき、アプリケーションはインターネット ゾーン アクセス許可に基づいて実行されます。したがって、そのアクセス許可を超えると、セキュリティ例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-119">When you debug the XBAP from Visual Studio, the application runs with Internet zone permission and will therefore throw security exceptions if those permissions are exceeded.</span></span> <span data-ttu-id="4c39f-120">詳細については、[セキュリティ](../security-wpf.md)に関するページと、「[WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c39f-120">For more information, see [Security](../security-wpf.md) and [WPF Partial Trust Security](../wpf-partial-trust-security.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4c39f-121">Visual Studio を使用して開発していない場合やプロジェクト ファイルについて詳しい情報が必要な場合は、「[WPF アプリケーション (WPF) のビルド](building-a-wpf-application-wpf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c39f-121">If you are not developing with Visual Studio or want to learn more about the project files, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>

<a name="deploying_a_xbap"></a>
## <a name="deploying-an-xbap"></a><span data-ttu-id="4c39f-122">XBAP の配置</span><span class="sxs-lookup"><span data-stu-id="4c39f-122">Deploying an XBAP</span></span>
 <span data-ttu-id="4c39f-123">XBAP をビルドすると、次の 3 つのファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-123">When you build an XBAP, the output includes the following three files:</span></span>

|<span data-ttu-id="4c39f-124">ファイル</span><span class="sxs-lookup"><span data-stu-id="4c39f-124">File</span></span>|<span data-ttu-id="4c39f-125">説明</span><span class="sxs-lookup"><span data-stu-id="4c39f-125">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="4c39f-126">実行可能ファイル (.exe)</span><span class="sxs-lookup"><span data-stu-id="4c39f-126">Executable (.exe)</span></span>|<span data-ttu-id="4c39f-127">コンパイル済みのコードが含まれます。拡張子は .exe です。</span><span class="sxs-lookup"><span data-stu-id="4c39f-127">This contains the compiled code and has an .exe extension.</span></span>|
|<span data-ttu-id="4c39f-128">アプリケーション マニフェスト (.manifest)</span><span class="sxs-lookup"><span data-stu-id="4c39f-128">Application manifest (.manifest)</span></span>|<span data-ttu-id="4c39f-129">アプリケーションに関連付けられたメタデータが含まれます。拡張子は .manifest です。</span><span class="sxs-lookup"><span data-stu-id="4c39f-129">This contains metadata associated with the application and has a .manifest extension.</span></span>|
|<span data-ttu-id="4c39f-130">配置マニフェスト (.xbap)</span><span class="sxs-lookup"><span data-stu-id="4c39f-130">Deployment manifest (.xbap)</span></span>|<span data-ttu-id="4c39f-131">ClickOnce がアプリケーションの配置に使用する情報が含まれます。拡張子は .xbap です。</span><span class="sxs-lookup"><span data-stu-id="4c39f-131">This file contains the information that ClickOnce uses to deploy the application and has the .xbap extension.</span></span>|

 <span data-ttu-id="4c39f-132">XBAP は Web サーバーに配置します (Microsoft インターネット インフォメーション サービス (IIS) 5.0 以降のバージョンなど)。</span><span class="sxs-lookup"><span data-stu-id="4c39f-132">You deploy XBAPs to a Web server, for example Microsoft Internet Information Services (IIS) 5.0 or later versions.</span></span> <span data-ttu-id="4c39f-133">.NET Framework を Web サーバーにインストールする必要はありませんが、WPF Multipurpose Internet Mail Extensions (MIME) の種類とファイル名拡張子を登録する必要はあります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-133">You do not have to install the .NET Framework on the Web server, but you do have to register the WPF Multipurpose Internet Mail Extensions (MIME) types and file name extensions.</span></span> <span data-ttu-id="4c39f-134">詳細については、[WPF アプリケーションを配置するための IIS 5.0 および IIS 6.0 の構成](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4c39f-134">For more information, see [Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).</span></span>

 <span data-ttu-id="4c39f-135">XBAP を配置用に準備するには、.exe および関連付けられたマニフェストを Web サーバーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="4c39f-135">To prepare your XBAP for deployment, copy the .exe and the associated manifests to the Web server.</span></span> <span data-ttu-id="4c39f-136">配置マニフェスト (拡張子が .xbap のファイル) を開くために、ハイパーリンクを含む HTML ページを作成します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-136">Create an HTML page that contains a hyperlink to open the deployment manifest, which is the file that has the .xbap extension.</span></span> <span data-ttu-id="4c39f-137">ユーザーが .xbap ファイルへのリンクをクリックすると、ClickOnce によって、アプリケーションのダウンロードと開始が自動的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-137">When the user clicks the link to the .xbap file, ClickOnce automatically handles the mechanics of downloading and starting the application.</span></span> <span data-ttu-id="4c39f-138">次のコード例は、XBAP を指定するハイパーリンクを含む HTML ページを示しています。</span><span class="sxs-lookup"><span data-stu-id="4c39f-138">The following example code shows an HTML page that contains a hyperlink that points to an XBAP.</span></span>

```html
<html>
    <head></head>
    <body>
        <a href="XbapEx.xbap">Click this link to launch the application</a>
    </body>
</html>
```

 <span data-ttu-id="4c39f-139">Web ページのフレームで XBAP をホストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-139">You can also host an XBAP in the frame of a Web page.</span></span> <span data-ttu-id="4c39f-140">1 つ以上のフレームを含む Web ページを作成し、</span><span class="sxs-lookup"><span data-stu-id="4c39f-140">Create a Web page with one or more frames.</span></span> <span data-ttu-id="4c39f-141">配置マニフェスト ファイルに対するフレームのソース プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-141">Set the source property of a frame to the deployment manifest file.</span></span> <span data-ttu-id="4c39f-142">組み込みのメカニズムを使用して、ホスティング Web ページと XBAP との間で通信を行う場合は、フレームでアプリケーションをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-142">If you want to use the built-in mechanism to communicate between the hosting Web page and the XBAP, you must host the application in a frame.</span></span> <span data-ttu-id="4c39f-143">次のコード例は、2 つのフレームが含まれる HTML ページを示しています。ここでは、2 つ目のフレームのソースが XBAP に設定されています。</span><span class="sxs-lookup"><span data-stu-id="4c39f-143">The following example code shows an HTML page with two frames, the source for the second frame is set to an XBAP.</span></span>

```html
<html>
    <head>
        <title>A page with frames</title>
    </head>
    <frameset cols="50%,50%">
        <frame src="introduction.htm">
        <frame src="XbapEx.xbap">
    </frameset>
</html>
```

### <a name="clearing-cached-xbaps"></a><span data-ttu-id="4c39f-144">キャッシュされた XBAP のクリア</span><span class="sxs-lookup"><span data-stu-id="4c39f-144">Clearing Cached XBAPs</span></span>
 <span data-ttu-id="4c39f-145">XBAP をリビルドして開始した後に、旧バージョンの XBAP が開くことがあります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-145">In some situations after rebuilding and starting your XBAP, you may find that an earlier version of the XBAP is opened.</span></span> <span data-ttu-id="4c39f-146">たとえば、この動作は、XBAP アセンブリのバージョン番号が静的である場合に、XBAP をコマンド ラインから開始すると発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-146">For example, this behavior may occur when your XBAP assembly version number is static and you start the XBAP from the command line.</span></span> <span data-ttu-id="4c39f-147">この場合、キャッシュされているバージョン (それまで開始されていたバージョン) と新しいバージョンのバージョン番号が同じであるため、XBAP の新しいバージョンはダウンロードされません。</span><span class="sxs-lookup"><span data-stu-id="4c39f-147">In this case, because the version number between the cached version (the version that was previously started) and the new version remains the same, the new version of the XBAP is not downloaded.</span></span> <span data-ttu-id="4c39f-148">代わりに、キャッシュされたバージョンが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-148">Instead, the cached version is loaded.</span></span>

 <span data-ttu-id="4c39f-149">このような場合、キャッシュされているバージョンを削除するには、コマンド プロンプトで (Visual Studio または Windows SDK でインストールされる) **Mage** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-149">In these situations, you can remove the cached version by using the **Mage** command (installed with Visual Studio or the Windows SDK) at the command prompt.</span></span> <span data-ttu-id="4c39f-150">次のコマンドにより、アプリケーション キャッシュがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-150">The following command clears the application cache.</span></span>

 ```console
 Mage.exe -cc
 ```

 <span data-ttu-id="4c39f-151">このコマンドを実行すると、必ず最新バージョンの XBAP が開始されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-151">This command guarantees that the latest version of your XBAP is started.</span></span> <span data-ttu-id="4c39f-152">アプリケーションを Visual Studio でデバッグするときは、XBAP の最新バージョンを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-152">When you debug your application in Visual Studio, the latest version of your XBAP should be started.</span></span> <span data-ttu-id="4c39f-153">一般的に、配置バージョン番号は、ビルドするたびに更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4c39f-153">In general, you should update your deployment version number with each build.</span></span> <span data-ttu-id="4c39f-154">Mage の詳細については、「[Mage.exe (マニフェストの生成および編集ツール)](../../tools/mage-exe-manifest-generation-and-editing-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c39f-154">For more information about Mage, see [Mage.exe (Manifest Generation and Editing Tool)](../../tools/mage-exe-manifest-generation-and-editing-tool.md).</span></span>

<a name="communicating_with_the_host_web_page"></a>
## <a name="communicating-with-the-host-web-page"></a><span data-ttu-id="4c39f-155">ホスト Web ページとの通信</span><span class="sxs-lookup"><span data-stu-id="4c39f-155">Communicating with the Host Web Page</span></span>
 <span data-ttu-id="4c39f-156">アプリケーションが HTML フレーム内でホストされている場合は、XBAP を含む Web ページと通信できます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-156">When the application is hosted in an HTML frame, you can communicate with the Web page that contains the XBAP.</span></span> <span data-ttu-id="4c39f-157">それには、<xref:System.Windows.Interop.BrowserInteropHelper> の <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> プロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-157">You do this by retrieving the <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> property of <xref:System.Windows.Interop.BrowserInteropHelper>.</span></span> <span data-ttu-id="4c39f-158">このプロパティは、HTML ウィンドウを表すスクリプト オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-158">This property returns a script object that represents the HTML window.</span></span> <span data-ttu-id="4c39f-159">[window オブジェクト](https://developer.mozilla.org/en-US/docs/Web/API/Window)上のプロパティ、メソッド、およびイベントにアクセスするには、標準のドット構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-159">You can then access the properties, methods, and events on the [window object](https://developer.mozilla.org/en-US/docs/Web/API/Window) by using regular dot syntax.</span></span> <span data-ttu-id="4c39f-160">スクリプト メソッドおよびグローバル変数にアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-160">You can also access script methods and global variables.</span></span> <span data-ttu-id="4c39f-161">次の例は、スクリプト オブジェクトを取得して、ブラウザーを閉じる方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4c39f-161">The following example shows how to retrieve the script object and close the browser.</span></span>

 [!code-csharp[XbapBrowserInterop#10](~/samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]

### <a name="debugging-xbaps-that-use-hostscript"></a><span data-ttu-id="4c39f-162">HostScript を使用する XBAP のデバッグ</span><span class="sxs-lookup"><span data-stu-id="4c39f-162">Debugging XBAPs that Use HostScript</span></span>
 <span data-ttu-id="4c39f-163">XBAP で <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> オブジェクトを使用して HTML ウィンドウと通信する場合、Visual Studio でアプリケーションを実行およびデバッグするには、2 つの設定を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-163">If your XBAP uses the <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> object to communicate with the HTML window, there are two settings that you must specify to run and debug the application in Visual Studio.</span></span> <span data-ttu-id="4c39f-164">そのアプリケーションは元のサイトにアクセスできる必要がありますが、そのアプリケーションを開始するときは、XBAP を含む HTML ページを使用しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="4c39f-164">The application must have access to its site of origin and you must start the application with the HTML page that contains the XBAP.</span></span> <span data-ttu-id="4c39f-165">この 2 つの設定を確認する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-165">The following steps describe how to check these two settings:</span></span>

1. <span data-ttu-id="4c39f-166">Visual Studio でプロジェクトのプロパティを開きます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-166">In Visual Studio, open the project properties.</span></span>

2. <span data-ttu-id="4c39f-167">**[セキュリティ]** タブの **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c39f-167">On the **Security** tab, click **Advanced**.</span></span>

     <span data-ttu-id="4c39f-168">[セキュリティの詳細設定] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-168">The Advanced Security Settings dialog box appears.</span></span>

3. <span data-ttu-id="4c39f-169">**[アプリケーション アクセスをその元のサイトに与える]** チェック ボックスがオンになっていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c39f-169">Make sure that the **Grant the application access to its site of origin** check box is checked and then click **OK**.</span></span>

4. <span data-ttu-id="4c39f-170">**[デバッグ]** タブで、 **[ブラウザーを開始時に使用する URL]** をクリックし、XBAP を含む HTML ページの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-170">On the **Debug** tab, select the **Start browser with URL** option and specify the URL for the HTML page that contains the XBAP.</span></span>

5. <span data-ttu-id="4c39f-171">Internet Explorer で、 **[ツール]** をクリックし、 **[インターネット オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c39f-171">In Internet Explorer, click the **Tools** button and then select **Internet Options**.</span></span>

     <span data-ttu-id="4c39f-172">[インターネット オプション] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-172">The Internet Options dialog box appears.</span></span>

6. <span data-ttu-id="4c39f-173">**[詳細設定]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c39f-173">Click the **Advanced** tab.</span></span>

7. <span data-ttu-id="4c39f-174">**[セキュリティ]** の下にある **[設定]** ボックスで、 **[マイ コンピューターのファイルでのアクティブ コンテンツの実行を許可する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4c39f-174">In the **Settings** list under **Security**, check the **Allow active content to run in files on My Computer** check box.</span></span>

8. <span data-ttu-id="4c39f-175">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c39f-175">Click **OK**.</span></span>

     <span data-ttu-id="4c39f-176">変更は、Internet Explorer を再起動すると有効になります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-176">The changes will take effect after you restart Internet Explorer.</span></span>

> [!CAUTION]
> <span data-ttu-id="4c39f-177">Internet Explorer でアクティブ コンテンツを有効にすると、コンピューターが危険にさらされるおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-177">Enabling active content in Internet Explorer may put your computer at risk.</span></span> <span data-ttu-id="4c39f-178">Internet Explorer のセキュリティ設定を変更したくない場合は、HTML ページをサーバーから起動して、Visual Studio デバッガーをプロセスにアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-178">If you do not want to change your Internet Explorer security settings, you can launch the HTML page from a server and attach the Visual Studio debugger to the process.</span></span>

<a name="xbap_security_considerations"></a>
## <a name="xbap-security-considerations"></a><span data-ttu-id="4c39f-179">XBAP セキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="4c39f-179">XBAP Security Considerations</span></span>
 <span data-ttu-id="4c39f-180">XBAP は、通常、インターネット ゾーン アクセス許可セットに制限された部分信頼セキュリティ サンドボックスで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-180">XBAPs typically execute in a partial-trust security sandbox that is restricted to the Internet zone permission set.</span></span> <span data-ttu-id="4c39f-181">したがって、実装ではインターネット ゾーン内でサポートされている WPF 要素のサブセットをサポートするか、アプリケーションのアクセス許可を昇格させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-181">Consequently, your implementation must support the subset of WPF elements that are supported in the Internet zone or you must elevate the permissions of your application.</span></span> <span data-ttu-id="4c39f-182">詳細については、[セキュリティ](../security-wpf.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4c39f-182">For more information, see [Security](../security-wpf.md).</span></span>

 <span data-ttu-id="4c39f-183"><xref:System.Windows.Controls.WebBrowser> コントロールをアプリケーションで使用する場合、内部的には WPF によってネイティブ WebBrowser ActiveX コントロールがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-183">When you use a <xref:System.Windows.Controls.WebBrowser> control in your application, WPF internally instantiates the native WebBrowser ActiveX control.</span></span> <span data-ttu-id="4c39f-184">アプリケーションが Internet Explorer で実行されている部分信頼 XBAP である場合、ActiveX コントロールは Internet Explorer プロセスの専用スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-184">When your application is a partial-trust XBAP running in Internet Explorer, the ActiveX control runs in a dedicated thread of the Internet Explorer process.</span></span> <span data-ttu-id="4c39f-185">このため、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-185">Therefore, the following limitations apply:</span></span>

- <span data-ttu-id="4c39f-186"><xref:System.Windows.Controls.WebBrowser> コントロールでは、セキュリティ上の制限など、ホスト ブラウザーに似た動作を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-186">The <xref:System.Windows.Controls.WebBrowser> control should provide behavior similar to the host browser, including security restrictions.</span></span> <span data-ttu-id="4c39f-187">このようなセキュリティ上の制限の中には、Internet Explorer のセキュリティ設定を使用して制御できるものがあります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-187">Some of these security restrictions can be controlled through the Internet Explorer security settings.</span></span> <span data-ttu-id="4c39f-188">詳細については、[セキュリティ](../security-wpf.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4c39f-188">For more information, see [Security](../security-wpf.md).</span></span>

- <span data-ttu-id="4c39f-189">XBAP が HTML ページでドメインをまたいでロードされると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-189">An exception is thrown when an XBAP is loaded cross-domain in an HTML page.</span></span>

- <span data-ttu-id="4c39f-190">入力が WPF <xref:System.Windows.Controls.WebBrowser> とは別のスレッドで行われるため、キーボード入力をインターセプトできず、IME の状態が共有されません。</span><span class="sxs-lookup"><span data-stu-id="4c39f-190">Input is on a separate thread from the WPF <xref:System.Windows.Controls.WebBrowser>, so keyboard input cannot be intercepted and the IME state is not shared.</span></span>

- <span data-ttu-id="4c39f-191">ナビゲーションのタイミングまたは順序は、ActiveX コントロールが他のスレッド上で実行されるため異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-191">The timing or order of navigation may be different due to the ActiveX control running on another thread.</span></span> <span data-ttu-id="4c39f-192">たとえば、ページへの移動が、必ずしも別のナビゲーション要求の開始によって取り消されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="4c39f-192">For example, navigating to a page is not always cancelled by starting another navigation request.</span></span>

- <span data-ttu-id="4c39f-193">WPF アプリケーションが独立したスレッドで実行されるため、カスタムの ActiveX コントロールに通信の問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-193">A custom ActiveX control may have trouble with communication since the WPF application is running in a separate thread.</span></span>

- <span data-ttu-id="4c39f-194"><xref:System.Windows.Interop.HwndHost> が他のスレッドまたはプロセスで、実行中のウィンドウをサブクラス化できないため、<xref:System.Windows.Interop.HwndHost.MessageHook> は発生しません。</span><span class="sxs-lookup"><span data-stu-id="4c39f-194"><xref:System.Windows.Interop.HwndHost.MessageHook> does not get raised because <xref:System.Windows.Interop.HwndHost> cannot subclass a window running in another thread or process.</span></span>

### <a name="creating-a-full-trust-xbap"></a><span data-ttu-id="4c39f-195">完全な信頼の XBAP の作成</span><span class="sxs-lookup"><span data-stu-id="4c39f-195">Creating a Full-Trust XBAP</span></span>
 <span data-ttu-id="4c39f-196">XBAP で完全な信頼が必要な場合、プロジェクトを変更してこのアクセス許可を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-196">If your XBAP requires full trust, you can change your project to enable this permission.</span></span> <span data-ttu-id="4c39f-197">完全な信頼を有効にする手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-197">The following steps describe how to enable full trust:</span></span>

1. <span data-ttu-id="4c39f-198">Visual Studio でプロジェクトのプロパティを開きます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-198">In Visual Studio, open the project properties.</span></span>

2. <span data-ttu-id="4c39f-199">**[セキュリティ]** タブで、 **[これは完全に信頼するアプリケーションです]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c39f-199">On the **Security** tab, select the **This is a full trust application** option.</span></span>

 <span data-ttu-id="4c39f-200">この設定により、次の変更が実行されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-200">This setting makes the following changes:</span></span>

- <span data-ttu-id="4c39f-201">プロジェクト ファイル内の `<TargetZone>` 要素の値が `Custom` に変更される。</span><span class="sxs-lookup"><span data-stu-id="4c39f-201">In the project file, the `<TargetZone>` element value is changed to `Custom`.</span></span>

- <span data-ttu-id="4c39f-202">アプリケーション マニフェスト (app.manifest) の `Unrestricted="true"` 属性が <xref:System.Security.PermissionSet> 要素に追加される。</span><span class="sxs-lookup"><span data-stu-id="4c39f-202">In the application manifest (app.manifest), an `Unrestricted="true"` attribute is added to the \`<xref:System.Security.PermissionSet> element.</span></span>

    ```xml
    <PermissionSet class="System.Security.PermissionSet"
                   version="1"
                   ID="Custom"
                   SameSite="site"
                   Unrestricted="true" />
    ```

### <a name="deploying-a-full-trust-xbap"></a><span data-ttu-id="4c39f-203">完全な信頼の XBAP の配置</span><span class="sxs-lookup"><span data-stu-id="4c39f-203">Deploying a Full-Trust XBAP</span></span>
 <span data-ttu-id="4c39f-204">ClickOnce 信頼済み配置モデルに従っていない完全な信頼の XBAP を配置する場合、ユーザーがアプリケーションを実行するときの動作は、セキュリティ ゾーンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-204">When you deploy a full-trust XBAP that does not follow the ClickOnce Trusted Deployment model, the behavior when the user runs the application will depend on the security zone.</span></span> <span data-ttu-id="4c39f-205">ユーザーがアプリケーションをインストールしようとすると警告が表示されることもあります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-205">In some cases, the user will receive a warning when they attempt to install it.</span></span> <span data-ttu-id="4c39f-206">ユーザーは、インストールを続行するか取り消すかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-206">The user can choose to continue or cancel the installation.</span></span> <span data-ttu-id="4c39f-207">次の表は、各セキュリティ ゾーンのアプリケーション動作と、完全な信頼を受け取るアプリケーションで行う必要のある操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="4c39f-207">The following table describes the behavior of the application for each security zone and what you have to do for the application to receive full trust.</span></span>

|<span data-ttu-id="4c39f-208">セキュリティ ゾーン</span><span class="sxs-lookup"><span data-stu-id="4c39f-208">Security Zone</span></span>|<span data-ttu-id="4c39f-209">動作</span><span class="sxs-lookup"><span data-stu-id="4c39f-209">Behavior</span></span>|<span data-ttu-id="4c39f-210">完全信頼を受け取るための操作</span><span class="sxs-lookup"><span data-stu-id="4c39f-210">Getting Full Trust</span></span>|
|-------------------|--------------|------------------------|
|<span data-ttu-id="4c39f-211">ローカル コンピューター</span><span class="sxs-lookup"><span data-stu-id="4c39f-211">Local computer</span></span>|<span data-ttu-id="4c39f-212">完全な信頼を自動的に受け取る</span><span class="sxs-lookup"><span data-stu-id="4c39f-212">Automatic full trust</span></span>|<span data-ttu-id="4c39f-213">アクションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4c39f-213">No action is needed.</span></span>|
|<span data-ttu-id="4c39f-214">イントラネットおよび信頼済みサイト</span><span class="sxs-lookup"><span data-stu-id="4c39f-214">Intranet and trusted sites</span></span>|<span data-ttu-id="4c39f-215">完全な信頼のプロンプトを表示する</span><span class="sxs-lookup"><span data-stu-id="4c39f-215">Prompt for full trust</span></span>|<span data-ttu-id="4c39f-216">プロンプトにソースが表示されるように、証明書を使用して XBAP に署名します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-216">Sign the XBAP with a certificate so that the user sees the source in the prompt.</span></span>|
|<span data-ttu-id="4c39f-217">インターネット</span><span class="sxs-lookup"><span data-stu-id="4c39f-217">Internet</span></span>|<span data-ttu-id="4c39f-218">"信頼されていません" というメッセージが表示され、失敗する</span><span class="sxs-lookup"><span data-stu-id="4c39f-218">Fails with "Trust Not Granted"</span></span>|<span data-ttu-id="4c39f-219">証明書を使用して XBAP に署名します。</span><span class="sxs-lookup"><span data-stu-id="4c39f-219">Sign the XBAP with a certificate.</span></span>|

> [!NOTE]
> <span data-ttu-id="4c39f-220">前の表で説明した動作は、ClickOnce 信頼済み配置モデルに従っていない完全な信頼の XBAP の動作です。</span><span class="sxs-lookup"><span data-stu-id="4c39f-220">The behavior described in the previous table is for full-trust XBAPs that do not follow the ClickOnce Trusted Deployment model.</span></span>

 <span data-ttu-id="4c39f-221">完全な信頼の XBAP を配置する場合は、ClickOnce 信頼済み配置モデルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4c39f-221">It is recommended that you use the ClickOnce Trusted Deployment model for deploying a full-trust XBAP.</span></span> <span data-ttu-id="4c39f-222">このモデルにより、セキュリティ ゾーンに関係なく、完全な信頼を XBAP に自動的に付与できるため、ユーザーにプロンプトが表示されることはありません。</span><span class="sxs-lookup"><span data-stu-id="4c39f-222">This model allows your XBAP to be granted full trust automatically, regardless of the security zone, so that the user is not prompted.</span></span> <span data-ttu-id="4c39f-223">このモデルの一部として、信頼された発行元からの証明書を使用して、アプリケーションに署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-223">As part of this model, you must sign your application with a certificate from a trusted publisher.</span></span> <span data-ttu-id="4c39f-224">細については、「[信頼されたアプリケーションの配置の概要](/visualstudio/deployment/trusted-application-deployment-overview)」および「[Introduction to Code Signing (コード署名の概要)](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c39f-224">For more information, see [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) and [Introduction to Code Signing](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85)).</span></span>

<a name="xbap_start_time_performance_considerations"></a>
## <a name="xbap-start-time-performance-considerations"></a><span data-ttu-id="4c39f-225">XBAP 起動時のパフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="4c39f-225">XBAP Start Time Performance Considerations</span></span>
 <span data-ttu-id="4c39f-226">XBAP のパフォーマンスにとって重要なのは、その起動時にあります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-226">An important aspect of XBAP performance is its start time.</span></span> <span data-ttu-id="4c39f-227">最初に読み込む WPF アプリケーションが XBAP である場合は、"*コールド スタート*" に 10 秒以上かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="4c39f-227">If an XBAP is the first WPF application to load, the *cold start* time can be ten seconds or more.</span></span> <span data-ttu-id="4c39f-228">これは、進行状況ページは WPF によってレンダリングされますが、アプリケーションを表示するには CLR と WPF の両方をコールド スタートする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="4c39f-228">This is because the progress page is rendered by WPF, and both the CLR and WPF must be cold-started to display the application.</span></span>

 <span data-ttu-id="4c39f-229">.NET Framework 3.5 SP1 以降、XBAP のコールド スタート時間は、アンマネージ進行状況ページを配置サイクルの初期に表示することで短縮されています。</span><span class="sxs-lookup"><span data-stu-id="4c39f-229">Starting in .NET Framework 3.5 SP1, XBAP cold-start time is mitigated by displaying an unmanaged progress page early in the deployment cycle.</span></span> <span data-ttu-id="4c39f-230">進行状況ページは、ネイティブ ホスティング コードによって表示され、HTML でレンダリングされます。このため、ほぼアプリケーションの起動直後に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-230">The progress page appears almost immediately after the application is started, because it is displayed by native hosting code and rendered in HTML.</span></span>

 <span data-ttu-id="4c39f-231">さらに、ClickOnce のダウンロード シーケンスのコンカレンシーの改良によって、開始時間は最大 10% 短縮されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-231">In addition, improved concurrency of the ClickOnce download sequence improves start time by up to ten percent.</span></span> <span data-ttu-id="4c39f-232">ClickOnce でマニフェストがダウンロードされて評価された後、アプリケーションのダウンロードが始まり、進行状況バーの更新が開始されます。</span><span class="sxs-lookup"><span data-stu-id="4c39f-232">After ClickOnce downloads and validates manifests, the application download starts, and the progress bar starts to update.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c39f-233">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c39f-233">See also</span></span>

- [<span data-ttu-id="4c39f-234">Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="4c39f-234">Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>](configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)
- [<span data-ttu-id="4c39f-235">WPF アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="4c39f-235">Deploying a WPF Application</span></span>](deploying-a-wpf-application-wpf.md)
