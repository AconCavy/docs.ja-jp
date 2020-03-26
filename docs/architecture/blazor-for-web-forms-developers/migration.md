---
title: Web フォームからブラゾールへの移行ASP.NET
description: 既存の ASP.NET Web フォーム アプリを Blazor に移行する方法について説明します。
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 0a10a9a3d5ab32e16cb59a68da57116e20c53e49
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134090"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="16c9b-103">Web フォームからブラゾールへの移行ASP.NET</span><span class="sxs-lookup"><span data-stu-id="16c9b-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="16c9b-104">コード ベースを ASP.NET Web フォームから Blazor に移行することは、計画を立てる必要がある時間のかかる作業です。</span><span class="sxs-lookup"><span data-stu-id="16c9b-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="16c9b-105">この章では、プロセスの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-105">This chapter outlines the process.</span></span> <span data-ttu-id="16c9b-106">移行を容易にする方法は、アプリが*N 層*アーキテクチャに準拠していることを確認することです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="16c9b-107">このようにレイヤを論理的に分離することで、.NET Core と Blazor に移行する必要がある内容が明確になります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="16c9b-108">この例では[、GitHub](https://github.com/dotnet-architecture/eShopOnBlazor)で利用可能な eShop アプリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="16c9b-109">eShop は、フォームの入力と検証を介して CRUD 機能を提供するカタログ サービスです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="16c9b-110">作業アプリを Blazor に移行する必要がある理由</span><span class="sxs-lookup"><span data-stu-id="16c9b-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="16c9b-111">何度も、必要はありません。</span><span class="sxs-lookup"><span data-stu-id="16c9b-111">Many times, there's no need.</span></span> <span data-ttu-id="16c9b-112">ASP.NET Web フォームは長年にわたってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="16c9b-113">ただし、Blazor が提供する機能の多くは、移行されたアプリでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="16c9b-114">このような機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-114">Such features include:</span></span>

- <span data-ttu-id="16c9b-115">フレームワークのパフォーマンスの向上など`Span<T>`</span><span class="sxs-lookup"><span data-stu-id="16c9b-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="16c9b-116">Web アセンブリとして実行する機能</span><span class="sxs-lookup"><span data-stu-id="16c9b-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="16c9b-117">Linux と macOS のクロスプラットフォームサポート</span><span class="sxs-lookup"><span data-stu-id="16c9b-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="16c9b-118">他のアプリに影響を与えることなく、アプリローカル展開または共有フレームワーク展開</span><span class="sxs-lookup"><span data-stu-id="16c9b-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="16c9b-119">これらの新機能やその他の新機能が十分に魅力的な場合は、アプリの移行に価値がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="16c9b-120">移行は異なる形状をとることができます。これは、アプリ全体、または変更を必要とする特定のエンドポイントのみです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="16c9b-121">移行の決定は、最終的には、開発者が解決するビジネス上の問題に基づいています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="16c9b-122">サーバー側とクライアント側のホスティング</span><span class="sxs-lookup"><span data-stu-id="16c9b-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="16c9b-123">[ホスティング モデル](hosting-models.md)の章で説明したように、Blazor アプリは、サーバー側とクライアント側の 2 つの異なる方法でホストできます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="16c9b-124">サーバー側モデルでは、コア SignalR 接続ASP.NET使用して、サーバー上で実際のコードを実行しながら DOM の更新を管理します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="16c9b-125">クライアント側モデルはブラウザ内で WebAssembly として動作し、サーバー接続は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="16c9b-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="16c9b-126">特定のアプリに最適な影響を及ぼす可能性のある相違点がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="16c9b-127">WebAssembly として実行はまだ開発中であり、現在の時点ですべての機能 (スレッドなど) をサポートしていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="16c9b-128">クライアントとサーバー間の通信が通信を行うと、サーバー側モードで遅延の問題が発生する場合がある</span><span class="sxs-lookup"><span data-stu-id="16c9b-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="16c9b-129">データベースおよび内部サービスまたは保護されたサービスへのアクセスには、クライアント側のホスティングを伴う個別のサービスが必要です。</span><span class="sxs-lookup"><span data-stu-id="16c9b-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="16c9b-130">執筆時点では、サーバー側モデルは Web フォームに似ています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="16c9b-131">この章の大部分は、運用準備が整っているサーバー側のホスティング モデルに焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="16c9b-132">新しいプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="16c9b-132">Create a new project</span></span>

<span data-ttu-id="16c9b-133">この移行の最初の手順では、新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="16c9b-134">このプロジェクトの種類は、.NET Core の SDK スタイル プロジェクトに基づいており、以前のプロジェクト形式で使用されていた定型の大部分を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="16c9b-135">詳細については、「[プロジェクト構造](project-structure.md)」の章を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="16c9b-136">プロジェクトを作成したら、前のプロジェクトで使用されていたライブラリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="16c9b-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="16c9b-137">以前のバージョンの Web フォーム プロジェクトでは *、packages.config*ファイルを使用して必要な NuGet パッケージを一覧表示している場合があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="16c9b-138">新しい SDK スタイルのプロジェクトでは *、packages.config*が`<PackageReference>`プロジェクト ファイル内の要素に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="16c9b-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="16c9b-139">この方法の利点は、すべての依存関係が推移的にインストールされるということです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="16c9b-140">関心がある最上位の依存関係のみを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="16c9b-141">使用している依存関係の多くは、Entity Framework 6 と log4net を含む .NET Core で使用できます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="16c9b-142">.NET Core または .NET 標準バージョンが利用できない場合は、.NET Framework バージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="16c9b-143">実際のメリットはケースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-143">Your mileage may vary.</span></span> <span data-ttu-id="16c9b-144">NET Core で使用できない API を使用すると、ランタイム エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="16c9b-145">このようなパッケージが通知されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="16c9b-146">**ソリューション エクスプローラ**のプロジェクトの **[参照]** ノードに黄色のアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="16c9b-147">Blazor ベースの eShop プロジェクトでは、インストールされているパッケージを確認できます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="16c9b-148">以前は *、packages.config*ファイルには、プロジェクトで使用されるすべてのパッケージが一覧表示され、ファイルの長さは 50 行近くになります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="16c9b-149">*パッケージ.config*のスニペットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-149">A snippet of *packages.config* is:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

<span data-ttu-id="16c9b-150">要素`<packages>`には、必要なすべての依存関係が含まれます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="16c9b-151">これらのパッケージの中に含まれているパッケージは、パッケージが必要なため、識別するのが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="16c9b-152">必要`<package>`な依存関係のニーズを満たすために、一部の要素が単純に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="16c9b-153">Blazor プロジェクトには、プロジェクト ファイル内の要素`<ItemGroup>`内で必要な依存関係が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="16c9b-154">Web フォーム開発者の生活を簡素化する NuGet パッケージの 1 つに[、 Windows 互換機能パック](../../core/porting/windows-compat-pack.md)があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="16c9b-155">.NET Core はクロスプラットフォームですが、一部の機能は Windows でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="16c9b-156">Windows 固有の機能は、互換機能パックをインストールすることによって利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="16c9b-157">このような機能の例としては、レジストリ、WMI、ディレクトリ サービスなどがあります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="16c9b-158">このパッケージは約 20,000 の API を追加し、すでに使い慣れた多くのサービスをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="16c9b-159">eShop プロジェクトには互換パックは必要ありません。ただし、プロジェクトで Windows 固有の機能を使用している場合、パッケージは移行作業を容易にします。</span><span class="sxs-lookup"><span data-stu-id="16c9b-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="16c9b-160">スタートアップ プロセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="16c9b-160">Enable startup process</span></span>

<span data-ttu-id="16c9b-161">Blazor の起動プロセスは Web フォームから変更され、他の ASP.NET コア サービスでも同様の設定に従っています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="16c9b-162">ホストされたサーバー側の場合、Blazor コンポーネントは通常の ASP.NET Core アプリの一部として実行されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="16c9b-163">WebAssembly を使用してブラウザでホストする場合、Blazor コンポーネントは同様のホスティング モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="16c9b-164">違いは、コンポーネントがバックエンドプロセスとは別のサービスとして実行される点です。</span><span class="sxs-lookup"><span data-stu-id="16c9b-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="16c9b-165">いずれにせよ、スタートアップは似ています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="16c9b-166">*Global.asax.cs*ファイルは、Web フォーム プロジェクトの既定のスタートアップ ページです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="16c9b-167">eShop プロジェクトでは、このファイルは制御の反転 (IoC) コンテナーを構成し、アプリまたは要求のさまざまなライフ サイクル イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="16c9b-168">これらのイベントの一部はミドルウェア (など`Application_BeginRequest`) で処理されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="16c9b-169">その他のイベントでは、依存関係注入 (DI) を介して特定のサービスをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="16c9b-170">例として、eShop の*Global.asax.cs*ファイルには、次のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// http://docs.autofac.org/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

<span data-ttu-id="16c9b-171">上記のファイルは、`Startup`サーバー側の Blazor のクラスになります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

<span data-ttu-id="16c9b-172">Web フォームから見た重要な変更点の 1 つは、DI の顕著さです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="16c9b-173">DIは、ASP.NETコア設計の指針となっています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="16c9b-174">コア フレームワークのほぼすべての側面のカスタマイズASP.NETサポートします。</span><span class="sxs-lookup"><span data-stu-id="16c9b-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="16c9b-175">多くのシナリオで使用できる組み込みのサービス プロバイダーもあります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="16c9b-176">さらにカスタマイズが必要な場合は、多くのコミュニティ プロジェクトでサポートできます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="16c9b-177">たとえば、サードパーティの DI ライブラリへの投資を繰り越すことができます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="16c9b-178">元の eShop アプリでは、セッション管理のためのいくつかの構成があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="16c9b-179">サーバー側の Blazor は通信にASP.NETコア SignalR を使用するため、HTTP コンテキストとは無関係に接続が発生する可能性があるため、セッション状態はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="16c9b-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="16c9b-180">セッション状態を使用するアプリでは、Blazor アプリとして実行する前に再設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="16c9b-181">アプリの起動の詳細については、「[アプリの起動](app-startup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="16c9b-182">HTTP モジュールとハンドラをミドルウェアに移行する</span><span class="sxs-lookup"><span data-stu-id="16c9b-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="16c9b-183">HTTP モジュールとハンドラーは、HTTP 要求パイプラインを制御する Web フォームの一般的なパターンです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="16c9b-184">受信要求を`IHttpModule`実装`IHttpHandler`または登録して処理できるクラス。</span><span class="sxs-lookup"><span data-stu-id="16c9b-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="16c9b-185">Web フォームは *、web.config*ファイル内のモジュールとハンドラーを構成します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="16c9b-186">Web フォームは、アプリのライフサイクル イベント処理にも大きく依存しています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="16c9b-187">ASP.NETコアはミドルウェアを代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="16c9b-188">ミドルウェアはクラスの`Configure`メソッドに登録されます`Startup`。</span><span class="sxs-lookup"><span data-stu-id="16c9b-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="16c9b-189">ミドルウェアの実行順序は、登録順によって決まります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="16c9b-190">[[スタートアップ プロセスを有効にする](#enable-startup-process)] セクションで、Web フォームによって`Application_BeginRequest`メソッドとしてライフサイクル イベントが発生しました。</span><span class="sxs-lookup"><span data-stu-id="16c9b-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="16c9b-191">このイベントは、ASP.NET Core では使用できません。</span><span class="sxs-lookup"><span data-stu-id="16c9b-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="16c9b-192">この動作を実現する 1 つの方法は *、Startup.cs*ファイルの例に示すようにミドルウェアを実装することです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="16c9b-193">このミドルウェアは同じロジックを実行し、その後、ミドルウェア パイプラインの次のハンドラーに制御を転送します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="16c9b-194">モジュールとハンドラーの移行の詳細については、「 [HTTP ハンドラーとモジュールを core ミドルウェアに移行する 」ASP.NET](/aspnet/core/migration/http-modules)参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="16c9b-195">静的ファイルの移行</span><span class="sxs-lookup"><span data-stu-id="16c9b-195">Migrate static files</span></span>

<span data-ttu-id="16c9b-196">静的ファイル (HTML、CSS、画像、JavaScript など) を提供するには、ミドルウェアによってファイルを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="16c9b-197">メソッドを`UseStaticFiles`呼び出すと、Web ルート パスから静的ファイルを提供できるようになります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="16c9b-198">デフォルトの web ルート ディレクトリは*wwwroot*ですが、カスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="16c9b-199">eShopの`Configure``Startup`クラスのメソッドに含まれているように:</span><span class="sxs-lookup"><span data-stu-id="16c9b-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="16c9b-200">eShop プロジェクトでは、基本的な静的ファイルアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="16c9b-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="16c9b-201">静的ファイル アクセスには、多くのカスタマイズを使用できます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="16c9b-202">デフォルトファイルまたはファイルブラウザを有効にする方法については[、「ASP.NETコアの静的ファイル](/aspnet/core/fundamentals/static-files)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="16c9b-203">ランタイムのバンドルと縮小の設定を移行する</span><span class="sxs-lookup"><span data-stu-id="16c9b-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="16c9b-204">バンドルと縮小は、特定のファイルの種類を取得するサーバー要求の数とサイズを減らすためのパフォーマンスの最適化手法です。</span><span class="sxs-lookup"><span data-stu-id="16c9b-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="16c9b-205">JavaScript と CSS は、クライアントに送信される前に、何らかの形のバンドルまたは縮小を受けることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="16c9b-206">ASP.NET Web フォームでは、これらの最適化は実行時に処理されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="16c9b-207">最適化規則は *、App_Start/バンドルConfig.cs*ファイルとして定義されています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="16c9b-208">ASP.NET Core では、より宣言的なアプローチが採用されています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="16c9b-209">ファイルには、特定の縮小設定と共に、縮小するファイルが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="16c9b-210">バンドルと縮小の詳細については[、「ASP.NET Core で静的アセットをバンドルおよび縮小](/aspnet/core/client-side/bundling-and-minification)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="16c9b-211">ASPX ページの移行</span><span class="sxs-lookup"><span data-stu-id="16c9b-211">Migrate ASPX pages</span></span>

<span data-ttu-id="16c9b-212">Web フォーム アプリのページは、*拡張子 .aspx*を持つファイルです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="16c9b-213">Web フォーム ページは、多くの場合、Blazor のコンポーネントにマップできます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="16c9b-214">Blazor コンポーネントは、*拡張子 .razor*を持つファイルで作成されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="16c9b-215">eShop プロジェクトでは、5 ページが Razor ページに変換されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="16c9b-216">たとえば、詳細ビューは、Web フォーム プロジェクト内の*Details.aspx* *、Details.aspx.cs、* および*Details.aspx.designer.cs*の 3 つのファイルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="16c9b-217">Blazor に変換する場合、分離コードとマークアップは*Details.razor*に結合されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="16c9b-218">Razor コンパイル *(.designer.cs*ファイルに含まれるものと同等) は*obj*ディレクトリに格納され、既定ではソリューション**エクスプローラー**で表示できません。</span><span class="sxs-lookup"><span data-stu-id="16c9b-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="16c9b-219">Web フォーム ページは、次のマークアップで構成されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-219">The Web Forms page consists of the following markup:</span></span>

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

<span data-ttu-id="16c9b-220">上記のマークアップの分離コードには、次のコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-220">The preceding markup's code-behind includes the following code:</span></span>

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

<span data-ttu-id="16c9b-221">Blazor に変換すると、Web フォーム ページは次のコードに変換されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

<span data-ttu-id="16c9b-222">コードとマークアップが同じファイルに含まれているのに注意してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="16c9b-223">必要なサービスはすべて、`@inject`属性を使用してアクセス可能になります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="16c9b-224">ディレクティブに`@page`従って、このページは`Catalog/Details/{id}`ルートでアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="16c9b-225">ルートのプレースホルダの`{id}`値は、整数に制限されています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="16c9b-226">Web フォームとは異なり、[ルーティング](pages-routing-layouts.md)セクションで説明されているように、Razor コンポーネントは、そのルートと含まれているパラメーターを明示的に示します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="16c9b-227">多くの Web フォーム コントロールは、Blazor に対応するものを持たない場合があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="16c9b-228">同じ目的を果たす同等の HTML スニペットが存在することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="16c9b-229">たとえば、コントロールを`<asp:Label />`HTML`<label>`要素に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="16c9b-230">ブラゾールでのモデル検証</span><span class="sxs-lookup"><span data-stu-id="16c9b-230">Model validation in Blazor</span></span>

<span data-ttu-id="16c9b-231">Web フォーム コードに検証が含まれている場合は、ほとんど変更を加えなくても、多くの情報を転送できます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="16c9b-232">Blazor で実行する利点は、カスタム JavaScript を必要とせずに同じ検証ロジックを実行できることです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="16c9b-233">データ注釈を使用すると、モデルの検証が容易になります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="16c9b-234">たとえば *、Create.aspx*ページには検証を含むデータ入力フォームがあります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="16c9b-235">スニペットの例は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-235">An example snippet would look like this:</span></span>

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

<span data-ttu-id="16c9b-236">Blazor では、同等のマークアップが*Create.razor*ファイルで提供されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>

    ...
</EditForm>
```

<span data-ttu-id="16c9b-237">コンテキスト`EditForm`には検証サポートが含まれており、入力をラップできます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="16c9b-238">データ注釈は、検証を追加する一般的な方法です。</span><span class="sxs-lookup"><span data-stu-id="16c9b-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="16c9b-239">このような検証サポートは、コンポーネントを`DataAnnotationsValidator`介して追加できます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="16c9b-240">このメカニズムの詳細については[、「core Blazor のフォームと検証ASP.NET」](/aspnet/core/blazor/forms-validation)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="16c9b-241">組み込みの Web フォーム コントロールを移行する</span><span class="sxs-lookup"><span data-stu-id="16c9b-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="16c9b-242">*このコンテンツはまもなく公開されます。*</span><span class="sxs-lookup"><span data-stu-id="16c9b-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="16c9b-243">構成の移行</span><span class="sxs-lookup"><span data-stu-id="16c9b-243">Migrate configuration</span></span>

<span data-ttu-id="16c9b-244">Web フォーム プロジェクトでは、構成データは *、web.config*ファイルに格納されるのが最も一般的です。</span><span class="sxs-lookup"><span data-stu-id="16c9b-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="16c9b-245">構成データには、 を`ConfigurationManager`使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="16c9b-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="16c9b-246">オブジェクトを解析するためには、サービスがしばしば必要でした。</span><span class="sxs-lookup"><span data-stu-id="16c9b-246">Services were often required to parse objects.</span></span> <span data-ttu-id="16c9b-247">NET Framework 4.7.2 では、構成可能性が を使用`ConfigurationBuilders`して構成に追加されました。</span><span class="sxs-lookup"><span data-stu-id="16c9b-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="16c9b-248">これらのビルダーを使用すると、開発者は、必要な値を取得するために実行時に構成された構成のさまざまなソースを追加することができました。</span><span class="sxs-lookup"><span data-stu-id="16c9b-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="16c9b-249">ASP.NET Core では、アプリとデプロイで使用される構成ソースを定義できる柔軟な構成システムが導入されました。</span><span class="sxs-lookup"><span data-stu-id="16c9b-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="16c9b-250">Web`ConfigurationBuilder`フォーム アプリで使用できるインフラストラクチャは、ASP.NET コア構成システムで使用される概念に基づきます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="16c9b-251">次のスニペットは、Web フォーム eShop プロジェクトが*web.config*を使用して構成値を格納する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
</configuration>
```

<span data-ttu-id="16c9b-252">データベース接続文字列などのシークレットは、 *web.config*内に格納されるのが一般的です。シークレットは、ソース管理などのセキュリティで保護されていない場所に保持されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="16c9b-253">ASP.NETコア上の Blazor を使用すると、上記の XML ベースの構成は次の JSON に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="16c9b-254">JSON はデフォルトの設定形式です。ただし、ASP.NET Core では、XML など、他の多くの形式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="16c9b-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="16c9b-255">コミュニティでサポートされている形式もいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="16c9b-256">Blazor プロジェクトのクラスの`Startup`コンストラクターは、コンストラクターインジェ`IConfiguration`クションと呼ばれる DI テクニックを使用してインスタンスを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

<span data-ttu-id="16c9b-257">デフォルトでは、環境変数、JSON ファイル (*appsettings.json*および*appsettings.{environment}.json)、* およびコマンドラインオプションは、有効な構成ソースとして設定オブジェクトに登録されます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="16c9b-258">構成ソースには、 を介`Configuration[key]`してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="16c9b-259">より高度な手法は、オプション パターンを使用して構成データをオブジェクトにバインドすることです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="16c9b-260">構成とオプション パターンの詳細については、ASP.NET[コアの ASP.NET コア](/aspnet/core/fundamentals/configuration/)および[オプション パターンの](/aspnet/core/fundamentals/configuration/options)構成をそれぞれ参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="16c9b-261">データ アクセスの移行</span><span class="sxs-lookup"><span data-stu-id="16c9b-261">Migrate data access</span></span>

<span data-ttu-id="16c9b-262">データ アクセスは、アプリの重要な側面です。</span><span class="sxs-lookup"><span data-stu-id="16c9b-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="16c9b-263">eShop プロジェクトは、カタログ情報をデータベースに格納し、エンティティ フレームワーク (EF) 6 を使用してデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="16c9b-264">EF 6 は .NET Core 3.0 でサポートされているため、プロジェクトは引き続き EF 6 を使用できます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="16c9b-265">eShop には、次の EF 関連の変更が必要でした。</span><span class="sxs-lookup"><span data-stu-id="16c9b-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="16c9b-266">.NET Framework では`DbContext`、オブジェクトは*name=ConnectionString*という形式の文字列`ConfigurationManager.AppSettings[ConnectionString]`を受け取り、接続文字列を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="16c9b-267">NET Core では、これはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="16c9b-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="16c9b-268">接続文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="16c9b-269">データベースは同期的にアクセスされました。</span><span class="sxs-lookup"><span data-stu-id="16c9b-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="16c9b-270">この方法は機能しますが、スケーラビリティが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="16c9b-271">このロジックは、非同期パターンに移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="16c9b-272">データセットのバインドに対して同じネイティブ サポートはありませんが、Blazor は、Razor ページでの C# サポートで柔軟性と機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="16c9b-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="16c9b-273">たとえば、計算を実行して結果を表示できます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="16c9b-274">Blazor のデータパターンの詳細については、[データアクセス](data.md)の章を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="16c9b-275">アーキテクチャの変更</span><span class="sxs-lookup"><span data-stu-id="16c9b-275">Architectural changes</span></span>

<span data-ttu-id="16c9b-276">最後に、Blazor への移行時に考慮すべき重要なアーキテクチャの違いがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="16c9b-277">これらの変更の多くは、.NET Core または ASP.NET コアに基づくすべての機能に適用できます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="16c9b-278">Blazor は .NET Core 上で構築されているため、.NET Core でのサポートを確保する際に考慮すべき点があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="16c9b-279">主な変更点には、次の機能の削除が含まれます。</span><span class="sxs-lookup"><span data-stu-id="16c9b-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="16c9b-280">複数のアプリケーションドメイン</span><span class="sxs-lookup"><span data-stu-id="16c9b-280">Multiple AppDomains</span></span>
- <span data-ttu-id="16c9b-281">リモート処理</span><span class="sxs-lookup"><span data-stu-id="16c9b-281">Remoting</span></span>
- <span data-ttu-id="16c9b-282">CAS (コード アクセス セキュリティ)</span><span class="sxs-lookup"><span data-stu-id="16c9b-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="16c9b-283">セキュリティ透過性</span><span class="sxs-lookup"><span data-stu-id="16c9b-283">Security Transparency</span></span>

<span data-ttu-id="16c9b-284">NET Core での実行をサポートするために必要な変更を特定する方法の詳細については[、「.NET Framework から .NET Core へのコードの移植](/dotnet/core/porting)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="16c9b-285">ASP.NET Core は、ASP.NETの再考されたバージョンであり、最初は明らかに見えない変更があります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="16c9b-286">主な変更点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="16c9b-286">The main changes are:</span></span>

- <span data-ttu-id="16c9b-287">同期コンテキストがないため、、、、または`HttpContext.Current``Thread.CurrentPrincipal`他の静的アクセサーが存在しません。</span><span class="sxs-lookup"><span data-stu-id="16c9b-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="16c9b-288">シャドウ コピーなし</span><span class="sxs-lookup"><span data-stu-id="16c9b-288">No shadow copying</span></span>
- <span data-ttu-id="16c9b-289">要求キューがありません</span><span class="sxs-lookup"><span data-stu-id="16c9b-289">No request queue</span></span>

<span data-ttu-id="16c9b-290">ASP.NET Core の操作の多くは非同期であり、I/O バインド タスクの読み込みが容易になります。</span><span class="sxs-lookup"><span data-stu-id="16c9b-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="16c9b-291">を`Task.Wait()``Task.GetResult()`使用してブロックすることは重要です。</span><span class="sxs-lookup"><span data-stu-id="16c9b-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="16c9b-292">移行の結論</span><span class="sxs-lookup"><span data-stu-id="16c9b-292">Migration conclusion</span></span>

<span data-ttu-id="16c9b-293">この時点で、Web フォーム プロジェクトを Blazor に移動するために必要な例が数多く見られました。</span><span class="sxs-lookup"><span data-stu-id="16c9b-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="16c9b-294">完全な例については[、eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor)プロジェクトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="16c9b-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="16c9b-295">前へ</span><span class="sxs-lookup"><span data-stu-id="16c9b-295">Previous</span></span>](security-authentication-authorization.md)
