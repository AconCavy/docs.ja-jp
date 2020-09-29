---
title: チュートリアルと技術的な概要
description: Azure クラウドおよび Windows コンテナーを使用して既存の .NET アプリケーションを最新化する | チュートリアルと技術的な概要
ms.date: 04/28/2018
ms.openlocfilehash: 98d33b13d2b28bfe1c35894df45e525cff0520c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172145"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="f6f38-103">チュートリアルと技術的な概要</span><span class="sxs-lookup"><span data-stu-id="f6f38-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="f6f38-104">この電子書籍のサイズを制限するために、追加の技術ドキュメントと完全なチュートリアルが GitHub リポジトリで利用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f6f38-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="f6f38-105">この章で説明する一連のオンライン チュートリアルでは、Windows コンテナーに基づく複数の環境の設定、および Azure へのデプロイに関する詳細な手順が網羅されています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="f6f38-106">次のセクションでは、各チュートリアルの内容、その目的、およびおおまかなビジョンについて説明し、必要とされるタスクを図示しています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="f6f38-107">チュートリアル自体は、<https://github.com/dotnet-architecture/eShopModernizing/wiki> にある *eShopModernizing* アプリ GitHub リポジトリ Wiki で入手できます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="f6f38-108">テクニカル チュートリアルの一覧</span><span class="sxs-lookup"><span data-stu-id="f6f38-108">Technical walkthrough list</span></span>

<span data-ttu-id="f6f38-109">以下の入門チュートリアルでは、コンテナーを使用してリフト アンド シフトしてから Azure で複数のデプロイ オプションを使用して移動することができ、サンプル アプリについて一貫性のある包括的な技術ガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="f6f38-110">以下の各チュートリアルでは、<https://github.com/dotnet-architecture/eShopModernizing> の GitHub で入手可能な新しいサンプル アプリ eShopLegacy および eShopModernizing を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="f6f38-111">**eShop レガシ アプリのツアー (最新化するベースライン アプリ)**</span><span class="sxs-lookup"><span data-stu-id="f6f38-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="f6f38-112">**Windows コンテナーを使用して既存の ASP.NET Web アプリ (WebForms & MVC) をコンテナー化する**</span><span class="sxs-lookup"><span data-stu-id="f6f38-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="f6f38-113">**Windows コンテナーを使用して既存の WCF サービス (N 層アプリ) をコンテナー化する**</span><span class="sxs-lookup"><span data-stu-id="f6f38-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="f6f38-114">**Windows コンテナーベースのアプリを Azure VM にデプロイする**</span><span class="sxs-lookup"><span data-stu-id="f6f38-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="f6f38-115">**Windows コンテナーベースのアプリを Azure Container Service の Kubernetes にデプロイする**</span><span class="sxs-lookup"><span data-stu-id="f6f38-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="f6f38-116">チュートリアル 1: eShop レガシ アプリのツアー</span><span class="sxs-lookup"><span data-stu-id="f6f38-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="f6f38-117">テクニカル チュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="f6f38-117">Technical walkthrough availability</span></span>

<span data-ttu-id="f6f38-118">完全なテクニカル チュートリアルについては、eShopModernizing GitHub リポジトリ Wiki を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6f38-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="f6f38-119">eShopModernizing Wiki のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="f6f38-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="f6f38-120">概要</span><span class="sxs-lookup"><span data-stu-id="f6f38-120">Overview</span></span>

<span data-ttu-id="f6f38-121">このチュートリアルでは、3 つのサンプル レガシ アプリケーションの初期実装について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="f6f38-122">最初の 2 つのサンプル Web アプリは、モノリシック アーキテクチャを備えており、従来の ASP.NET を使用して作成されています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="f6f38-123">1 つのアプリケーションは ASP.NET 4.x MVC をベースにしています。2 番目のアプリケーションは、ASP.NET 4.x Web Forms をベースにしています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="f6f38-124">3 番目のアプリケーションは、クライアントの WinForms アプリとサーバー側の [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) サービスによって構成される 3 層のアプリです。</span><span class="sxs-lookup"><span data-stu-id="f6f38-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="f6f38-125">これらのアプリケーションはすべて、[eShopModernizing GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="f6f38-126">目的</span><span class="sxs-lookup"><span data-stu-id="f6f38-126">Goals</span></span>

<span data-ttu-id="f6f38-127">このチュートリアルの主な目的は、これらのアプリと、そのコードおよび構成についてよく理解することです。</span><span class="sxs-lookup"><span data-stu-id="f6f38-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="f6f38-128">テスト目的で、SQL データベースを使用せずに、モック データを生成および使用するようにアプリを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="f6f38-129">この省略可能な構成は、分離された方法での依存関係の挿入に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="f6f38-130">シナリオ 1:ASP.NET Web アプリ</span><span class="sxs-lookup"><span data-stu-id="f6f38-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="f6f38-131">次の図は、元のレガシ ASP.NET Web アプリケーションのシンプルなシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![元のレガシ ASP.NET Web アプリケーションのシンプルなアーキテクチャ シナリオ](./media/image5-1.png)

<span data-ttu-id="f6f38-133">ビジネス ドメインの観点から見ると、どちらのアプリも同じカタログ管理機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="f6f38-134">eShop エンタープライズ チームのメンバーの場合は、アプリを使用して、製品カタログを表示および編集します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="f6f38-135">次の図は、初期のアプリのスクリーンショットを示しています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC と ASP.NET Web Forms アプリケーション (既存/レガシ テクノロジ)](./media/image5-2.png)

<span data-ttu-id="f6f38-137">ASP.NET 4.x またはそれ以前のバージョンでの依存関係 (MVC または Web Forms に対する) は、ASP.NET Core MVC を使用してコードを完全に書き直さない限り、これらのアプリケーションが .NET Core 上で実行されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="f6f38-138">シナリオ 2: WCF サービスと WinForms クライアント アプリ (3 層アプリ)</span><span class="sxs-lookup"><span data-stu-id="f6f38-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="f6f38-139">次の図は、元の 3 層レガシ アプリケーションのシンプルなシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![WCF サービスと WinForms クライアント アプリを含む元のレガシ 3 層アプリのシンプルなアーキテクチャ シナリオ](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="f6f38-141">利点</span><span class="sxs-lookup"><span data-stu-id="f6f38-141">Benefits</span></span>

<span data-ttu-id="f6f38-142">このチュートリアルの利点は、シンプルです。コードと初期アプリについて理解を深めることができます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="f6f38-143">次の手順</span><span class="sxs-lookup"><span data-stu-id="f6f38-143">Next steps</span></span>

<span data-ttu-id="f6f38-144">このコンテンツの詳細については、GitHub Wiki をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f6f38-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="f6f38-145">ベースライン ASP.NET MVC と Web Forms "レガシ" アプリに関するツアー</span><span class="sxs-lookup"><span data-stu-id="f6f38-145">Tour on the baseline ASP.NET MVC and Web Forms "legacy" apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="f6f38-146">ベースライン WCF サービスと WinForms (3 層) "レガシ" アプリに関するツアー</span><span class="sxs-lookup"><span data-stu-id="f6f38-146">Tour on the baseline WCF service and WinForms (3-Tier) "legacy" app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="f6f38-147">チュートリアル 2: Windows コンテナーを使用して既存の .NET アプリケーションをコンテナー化する</span><span class="sxs-lookup"><span data-stu-id="f6f38-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="f6f38-148">概要</span><span class="sxs-lookup"><span data-stu-id="f6f38-148">Overview</span></span>

<span data-ttu-id="f6f38-149">Windows コンテナーを使用して、運用環境、開発環境、テスト環境への既存の .NET アプリケーション (MVC、Web Forms、WCF に基づくものなど) のデプロイを改善します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="f6f38-150">目的</span><span class="sxs-lookup"><span data-stu-id="f6f38-150">Goals</span></span>

<span data-ttu-id="f6f38-151">このチュートリアルの目的は、既存の .NET Framework アプリケーションをコンテナー化するためのいくつかのオプションを示すことです。</span><span class="sxs-lookup"><span data-stu-id="f6f38-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="f6f38-152">次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-152">You can:</span></span>

- <span data-ttu-id="f6f38-153">[Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 以降のバージョン) を使用して、ご利用のアプリケーションをコンテナー化します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="f6f38-154">[Dockerfile](https://docs.docker.com/engine/reference/builder/) を手動で追加してから、[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/) を使用することで、ご利用のアプリケーションをコンテナー化します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="f6f38-155">[Image2Docker](https://github.com/docker/communitytools-image2docker-win) ツール (Docker からのオープンソース ツール) を使用して、ご利用のアプリケーションをコンテナー化します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="f6f38-156">このチュートリアルでは、Visual Studio 2017 Tools for Docker による手法に焦点を当てていますが、Dockerfile の使用に関しては他の 2 つの手法もよく似ています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="f6f38-157">シナリオ 1:コンテナー化された ASP.NET Web アプリ</span><span class="sxs-lookup"><span data-stu-id="f6f38-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="f6f38-158">次の図は、コンテナー化された eShop レガシ Web Apps アプリケーションのシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![開発環境でのコンテナー化された ASP.NET アプリケーションのアーキテクチャの概略図](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="f6f38-160">シナリオ 2: コンテナー化された WCF サービス</span><span class="sxs-lookup"><span data-stu-id="f6f38-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="f6f38-161">次の図は、コンテナー化された WCF サービスを使用した 3 層アプリケーションのシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![開発環境でのコンテナー化された WCF サービスのアーキテクチャの概略図](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="f6f38-163">利点</span><span class="sxs-lookup"><span data-stu-id="f6f38-163">Benefits</span></span>

<span data-ttu-id="f6f38-164">ご利用のモノシリック アプリケーションをコンテナー内で実行する利点があります。</span><span class="sxs-lookup"><span data-stu-id="f6f38-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="f6f38-165">まず、アプリケーションのイメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-165">First, you create an image for the application.</span></span> <span data-ttu-id="f6f38-166">その時点から、すべてのデプロイが同じ環境で実行されます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="f6f38-167">すべてのコンテナーは、同じ OS バージョンが使用され、同じバージョンの依存関係がインストールされており、同じ .NET フレームワーク バージョンが使用されることに加え、同じプロセスを使用してビルドされます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="f6f38-168">基本的に、ご利用のアプリケーションの依存関係は、Docker イメージを使用して制御します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="f6f38-169">コンテナーを展開すると、依存関係はアプリケーションと共に移動します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="f6f38-170">さらに、開発者は Windows コンテナーによって提供される一貫性のある環境でアプリケーションを実行できるという利点もあります。</span><span class="sxs-lookup"><span data-stu-id="f6f38-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="f6f38-171">特定のバージョンでのみ発生する問題は、ステージング環境または運用環境で表面化するのではなく、すぐに発見できます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="f6f38-172">アプリケーションをコンテナーで実行する場合、開発チームのメンバーが使用する開発環境の違いは、あまり問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="f6f38-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="f6f38-173">また、コンテナー化されたアプリケーションではスケールアウトのカーブは、より平坦です。</span><span class="sxs-lookup"><span data-stu-id="f6f38-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="f6f38-174">コンテナー化されたアプリを使用すると、コンピューターごとに行われる通常のアプリケーションのデプロイと比較して、VM または物理マシンに、より多くの (コンテナーに基づく) アプリケーションとサービスのインスタンスを用意できます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="f6f38-175">このことは、特に Kubernetes のようなオーケストレーター使用する場合に、密度がより高くなり、必要なリソースが減少することを意味します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="f6f38-176">コンテナー化の場合、理想的な状況では、アプリケーション コード (C\#) に変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f6f38-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="f6f38-177">ほとんどのシナリオでは、Docker デプロイ メタデータ ファイル (Dockerfile および Docker Compose ファイル) が必要なだけです。</span><span class="sxs-lookup"><span data-stu-id="f6f38-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="f6f38-178">次の手順</span><span class="sxs-lookup"><span data-stu-id="f6f38-178">Next steps</span></span>

<span data-ttu-id="f6f38-179">このコンテンツの詳細については、GitHub Wiki をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f6f38-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="f6f38-180">Windows コンテナーと Docker を使用して .NET Framework Web アプリをコンテナー化する方法</span><span class="sxs-lookup"><span data-stu-id="f6f38-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="f6f38-181">WCF サービスへの Docker サポートの追加</span><span class="sxs-lookup"><span data-stu-id="f6f38-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="f6f38-182">チュートリアル 3: Windows コンテナーベースのアプリを Azure VM にデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="f6f38-183">テクニカル チュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="f6f38-183">Technical walkthrough availability</span></span>

<span data-ttu-id="f6f38-184">完全なテクニカル チュートリアルについては、eShopModernizing GitHub リポジトリ Wiki (<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6f38-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="f6f38-185">概要</span><span class="sxs-lookup"><span data-stu-id="f6f38-185">Overview</span></span>

<span data-ttu-id="f6f38-186">Azure 内の Windows Server 2016 仮想マシン (VM) 上の Docker ホストにデプロイすると、開発/テスト/ステージングの環境をすばやく設定することができます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="f6f38-187">また、それによって、テスト担当者またはビジネス ユーザーがアプリを検証するための共通の場所も提供されます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="f6f38-188">VM は、サービスとしてのインフラストラクチャ (IaaS) 運用環境としても有効です。</span><span class="sxs-lookup"><span data-stu-id="f6f38-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="f6f38-189">目的</span><span class="sxs-lookup"><span data-stu-id="f6f38-189">Goals</span></span>

<span data-ttu-id="f6f38-190">このチュートリアルの目的は、Windows Server 2016 以降のバージョンに基づく Azure VM に Windows コンテナーをデプロイする場合に使用できる複数の選択肢を紹介することです。</span><span class="sxs-lookup"><span data-stu-id="f6f38-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="f6f38-191">シナリオ</span><span class="sxs-lookup"><span data-stu-id="f6f38-191">Scenarios</span></span>

<span data-ttu-id="f6f38-192">このチュートリアルでは、いくつかのシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="f6f38-193">シナリオ A: Docker エンジン接続を介して開発用 PC から Azure VM にデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Docker エンジン接続を介して開発用 PC から Azure VM にデプロイする](./media/image5-4.png)

<span data-ttu-id="f6f38-195">**図 5-4**</span><span class="sxs-lookup"><span data-stu-id="f6f38-195">**Figure 5-4.**</span></span> <span data-ttu-id="f6f38-196">Docker エンジン接続を介して開発用 PC から Azure VM にデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="f6f38-197">シナリオ B: Docker レジストリを介して Azure VM にデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Docker レジストリを介して Azure VM にデプロイする](./media/image5-5.png)

<span data-ttu-id="f6f38-199">**図 5-5**</span><span class="sxs-lookup"><span data-stu-id="f6f38-199">**Figure 5-5.**</span></span> <span data-ttu-id="f6f38-200">Docker レジストリを介して Azure VM にデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="f6f38-201">シナリオ C: Azure DevOps Services の CI/CD パイプラインから Azure VM にデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Azure DevOps Services の CI/CD パイプラインから Azure VM にデプロイする](./media/image5-6.png)

<span data-ttu-id="f6f38-203">**図 5-6**</span><span class="sxs-lookup"><span data-stu-id="f6f38-203">**Figure 5-6.**</span></span> <span data-ttu-id="f6f38-204">Azure DevOps Services の CI/CD パイプラインから Azure VM にデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="f6f38-205">Windows コンテナー用の Azure VM</span><span class="sxs-lookup"><span data-stu-id="f6f38-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="f6f38-206">Windows コンテナー用の Azure VM は、Windows Server 2016 以降または Windows 10 以降のバージョン (両方とも Docker エンジンが設定されている) に基づく VM です。</span><span class="sxs-lookup"><span data-stu-id="f6f38-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="f6f38-207">ほとんどの場合、Azure VM では Windows Server 2016 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="f6f38-208">Azure では現在、**Windows Server 2016 with Containers** という名前の VM が提供されています。</span><span class="sxs-lookup"><span data-stu-id="f6f38-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="f6f38-209">この VM を使用すれば、Windows Server Core または Windows Nano Server のいずれかで、新しい Windows Server コンテナー機能を試すことができます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="f6f38-210">コンテナー OS イメージがインストールされると、VM を Docker で使用する準備が整います。</span><span class="sxs-lookup"><span data-stu-id="f6f38-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="f6f38-211">利点</span><span class="sxs-lookup"><span data-stu-id="f6f38-211">Benefits</span></span>

<span data-ttu-id="f6f38-212">Windows コンテナーはオンプレミスの Windows Server 2016 VM にもデプロイできますが、Azure にデプロイすれば、すぐに使用できる Windows Server コンテナー VM で簡単に作業を開始することができます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="f6f38-213">また、テスト担当者がアクセスできる共通のオンライン場所や、Azure 仮想マシン スケール セットを介した自動スケーラビリティも得られます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-213">You also get a common online location that's accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="f6f38-214">次の手順</span><span class="sxs-lookup"><span data-stu-id="f6f38-214">Next steps</span></span>

<span data-ttu-id="f6f38-215">このコンテンツの詳細については、GitHub Wiki をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f6f38-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="f6f38-216">チュートリアル 4: ご利用の Windows コンテナーベースのアプリを Azure Container Instances (ACI) にデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="f6f38-217">テクニカル チュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="f6f38-217">Technical walkthrough availability</span></span>

<span data-ttu-id="f6f38-218">完全なテクニカル チュートリアルについては、eShopModernizing GitHub リポジトリ Wiki を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6f38-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="f6f38-219">[ACI (Azure Container Instances) へのアプリのデプロイ](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="f6f38-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="f6f38-220">概要</span><span class="sxs-lookup"><span data-stu-id="f6f38-220">Overview</span></span>

<span data-ttu-id="f6f38-221">[Azure Container Instances (ACI)](/azure/container-instances/) は、コンテナーの単一インスタンスをデプロイできるコンテナー開発/テスト/ステージング環境を作成する上で最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="f6f38-221">[Azure Container Instances (ACI)](/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="f6f38-222">目的</span><span class="sxs-lookup"><span data-stu-id="f6f38-222">Goals</span></span>

<span data-ttu-id="f6f38-223">このチュートリアルでは、Windows コンテナーを Azure Container Instances (ACI) にデプロイする場合の主なシナリオと、eShopModernizing アプリを ACI にデプロイする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="f6f38-224">シナリオ</span><span class="sxs-lookup"><span data-stu-id="f6f38-224">Scenarios</span></span>

<span data-ttu-id="f6f38-225">ACI への eShopModernizing アプリのデプロイについては、1 つだけ、またはすべてのアプリ (MVC アプリ、WebForms アプリ、WCF サービス) のデプロイなど、さまざまなバリエーションが考えられます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="f6f38-226">次に示すシナリオでは、ASP.NET MVC アプリと SQL Server コンテナーの両方が、コンテナーとして ACI (Azure Container Instances) にデプロイされるのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![開発環境から ACI にデプロイする](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="f6f38-228">利点</span><span class="sxs-lookup"><span data-stu-id="f6f38-228">Benefits</span></span>

<span data-ttu-id="f6f38-229">Azure Container Instances を使用すると、仮想マシンをプロビジョニングしたり、より高度なレベルのサービスを採用したりしなくても、Azure の Docker コンテナーを簡単に作成、管理できます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="f6f38-230">ACI を使用すると、Windows コンテナーを Azure に直接デプロイし、完全修飾ドメイン名 (FQDN) を使用して数秒でインターネットに公開することができます (Docker Hub などの Docker レジストリまたは Azure Container Registry 内に Windows コンテナー イメージが用意されている場合)。</span><span class="sxs-lookup"><span data-stu-id="f6f38-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="f6f38-231">注意事項</span><span class="sxs-lookup"><span data-stu-id="f6f38-231">Considerations</span></span>

<span data-ttu-id="f6f38-232">完全な .NET Framework/ASP.NET または SQL Server のいずれかを使用した Windows コンテナーの Azure Container Instances (ACI) へのデプロイは、通常の Docker ホスト (Windows コンテナーを備えた Windows Server 2016 など) へのデプロイほど高速ではありません。これは、Docker イメージを毎回ダウンロード (Docker レジストリから取得) する必要があり、SQL コンテナー イメージ (15.1 GB) と ASP.NET コンテナー イメージ (13.9 GB) のサイズが非常に大きいためです。しかし前者は、独自の Docker ホスト (Azure 内の Windows コンテナー VM を使用した永続的なオンライン Windows Server 2016)、あるいは Azure 内の Kubernetes (AKS) のような全体的なオーケストレーターを維持するよりもはるかに安価であることは言うまでもありません (ただし、AKS は運用環境のデプロイには最適です)。</span><span class="sxs-lookup"><span data-stu-id="f6f38-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="f6f38-233">主な結論として、Azure Container Instances を使用することは、開発/テスト シナリオおよび CI/CD パイプラインにおいて非常に魅力的なオプションです。</span><span class="sxs-lookup"><span data-stu-id="f6f38-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

### <a name="next-steps"></a><span data-ttu-id="f6f38-234">次の手順</span><span class="sxs-lookup"><span data-stu-id="f6f38-234">Next steps</span></span>

<span data-ttu-id="f6f38-235">このコンテンツの詳細については、GitHub Wiki をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f6f38-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="f6f38-236">チュートリアル 5: Windows コンテナーベースのアプリを Azure Container Service の Kubernetes にデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="f6f38-237">テクニカル チュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="f6f38-237">Technical walkthrough availability</span></span>

<span data-ttu-id="f6f38-238">完全なテクニカル チュートリアルについては、eShopModernizing GitHub リポジトリ Wiki を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6f38-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="f6f38-239">概要</span><span class="sxs-lookup"><span data-stu-id="f6f38-239">Overview</span></span>

<span data-ttu-id="f6f38-240">Windows コンテナーに基づくアプリケーションでは、IaaS VM からさらに離れた場所でも、プラットフォームをすばやく使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6f38-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="f6f38-241">これは、高いスケーラビリティと自動化された優れたスケーラビリティを容易に実現するため、さらに自動化されたデプロイとバージョン管理を大幅に改善するために必要です。</span><span class="sxs-lookup"><span data-stu-id="f6f38-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="f6f38-242">これらの目的を達成するには、[Azure Container Services](https://azure.microsoft.com/services/container-service/) で利用できるオーケストレーター [Kubernetes](https://kubernetes.io/) を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6f38-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="f6f38-243">目的</span><span class="sxs-lookup"><span data-stu-id="f6f38-243">Goals</span></span>

<span data-ttu-id="f6f38-244">このチュートリアルの目的は、Windows コンテナーベースのアプリケーションを、Azure Container Service の Kubernetes (*K8s* とも呼ばれます) にデプロイする方法について説明することです。</span><span class="sxs-lookup"><span data-stu-id="f6f38-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="f6f38-245">一からの Kubernetes へのデプロイは、次の 2 段階のプロセスとなります。</span><span class="sxs-lookup"><span data-stu-id="f6f38-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="f6f38-246">Azure Container Service に Kubernetes クラスターをデプロイする。</span><span class="sxs-lookup"><span data-stu-id="f6f38-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="f6f38-247">アプリケーションおよび関連リソースを Kubernetes クラスターにデプロイする。</span><span class="sxs-lookup"><span data-stu-id="f6f38-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="f6f38-248">シナリオ</span><span class="sxs-lookup"><span data-stu-id="f6f38-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="f6f38-249">シナリオ A: 開発環境から Kubernetes クラスターに直接デプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![開発環境から Kubernetes クラスターに直接デプロイする](./media/image5-7.png)

<span data-ttu-id="f6f38-251">**図 5-7**</span><span class="sxs-lookup"><span data-stu-id="f6f38-251">**Figure 5-7.**</span></span> <span data-ttu-id="f6f38-252">開発環境から Kubernetes クラスターに直接デプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="f6f38-253">シナリオ B: Azure DevOps Services の CI/CD パイプラインから Kubernetes クラスターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Azure DevOps Services の CI/CD パイプラインから Kubernetes クラスターにデプロイする](./media/image5-8.png)

<span data-ttu-id="f6f38-255">**図 5-8**</span><span class="sxs-lookup"><span data-stu-id="f6f38-255">**Figure 5-8.**</span></span> <span data-ttu-id="f6f38-256">Azure DevOps Services の CI/CD パイプラインから Kubernetes クラスターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="f6f38-257">利点</span><span class="sxs-lookup"><span data-stu-id="f6f38-257">Benefits</span></span>

<span data-ttu-id="f6f38-258">Kubernetes のクラスターにデプロイすることには多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="f6f38-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="f6f38-259">最大の利点は、使用するコンテナー インスタンスの数 (既存のノードの内部スケーラビリティ) に基づいて、およびクラスター内のノードまたは VM の数 (クラスターのグローバルなスケーラビリティ) に基づいてアプリケーションをスケールアウトできる実稼働可能な環境が得られることです。</span><span class="sxs-lookup"><span data-stu-id="f6f38-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="f6f38-260">Azure Container Service では、広く普及しているオープンソース ツールとテクノロジが Azure 専用に最適化されます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="f6f38-261">コンテナーとアプリケーションの構成の両方に移植性を提供するオープン ソリューションが得られます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="f6f38-262">サイズ、ホストの数、オーケストレーター ツールを選択すると、Container Service によって他のすべてが処理されます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="f6f38-263">Kubernetes を使用することで、開発者は物理マシンおよび仮想マシンについて考えることから、特に次の機能を容易にするコンテナー中心のインフラストラクチャを計画することへと進歩をはかることができます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="f6f38-264">複数のコンテナーに基づくアプリケーション</span><span class="sxs-lookup"><span data-stu-id="f6f38-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="f6f38-265">コンテナー インスタンスのレプリケーションと水平方向の自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="f6f38-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="f6f38-266">名前付けと検出 (たとえば、内部 DNS)</span><span class="sxs-lookup"><span data-stu-id="f6f38-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="f6f38-267">負荷分散</span><span class="sxs-lookup"><span data-stu-id="f6f38-267">Balancing loads</span></span>

- <span data-ttu-id="f6f38-268">ローリング アップデート</span><span class="sxs-lookup"><span data-stu-id="f6f38-268">Rolling updates</span></span>

- <span data-ttu-id="f6f38-269">シークレットの配布</span><span class="sxs-lookup"><span data-stu-id="f6f38-269">Distributing secrets</span></span>

- <span data-ttu-id="f6f38-270">アプリケーションの正常性チェック</span><span class="sxs-lookup"><span data-stu-id="f6f38-270">Application health checks</span></span>

### <a name="next-steps"></a><span data-ttu-id="f6f38-271">次の手順</span><span class="sxs-lookup"><span data-stu-id="f6f38-271">Next steps</span></span>

<span data-ttu-id="f6f38-272">このコンテンツの詳細については、GitHub Wiki をご覧ください: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="f6f38-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="f6f38-273">チュートリアル 6: ご利用の Windows コンテナーベースのアプリをコンテナー用の Azure App Service にデプロイする</span><span class="sxs-lookup"><span data-stu-id="f6f38-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="f6f38-274">テクニカル チュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="f6f38-274">Technical walkthrough availability</span></span>

<span data-ttu-id="f6f38-275">完全なテクニカル チュートリアルについては、eShopModernizing GitHub リポジトリ Wiki を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6f38-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="f6f38-276">概要</span><span class="sxs-lookup"><span data-stu-id="f6f38-276">Overview</span></span>

<span data-ttu-id="f6f38-277">Windows コンテナーを使用してコンテナー化されたシンプルなアプリケーションは、コンテナー用の Azure App Service に容易にデプロイできます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="f6f38-278">これは、ほとんどの Windows コンテナーベースのアプリケーションに推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="f6f38-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="f6f38-279">目的</span><span class="sxs-lookup"><span data-stu-id="f6f38-279">Goals</span></span>

<span data-ttu-id="f6f38-280">このチュートリアルの目的は、Windows コンテナーベースのアプリケーションを、レジストリ (Docker Hub または Azure Container Registry) からコンテナー用の Azure App Service にデプロイする方法について説明することです。</span><span class="sxs-lookup"><span data-stu-id="f6f38-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="f6f38-281">シナリオ</span><span class="sxs-lookup"><span data-stu-id="f6f38-281">Scenario</span></span>

![コンテナー用の Azure App Service に Windows コンテナーベースのアプリをデプロイする](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="f6f38-283">利点</span><span class="sxs-lookup"><span data-stu-id="f6f38-283">Benefits</span></span>

<span data-ttu-id="f6f38-284">コンテナー用の Azure App Service にデプロイすると、コンテナーの利点と Azure App Service の PaaS の利点とが組み合わされます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="f6f38-285">アプリ サービスを、垂直方向と水平方向の両方に簡単にスケーリングできると共に、変化する需要に合わせて自動スケーリングが行われるように構成することができます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="f6f38-286">更新はダウンタイムなしで実行することができます。レジストリからの継続的デプロイの構成も簡単に構成することができます。</span><span class="sxs-lookup"><span data-stu-id="f6f38-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

### <a name="next-steps"></a><span data-ttu-id="f6f38-287">次の手順</span><span class="sxs-lookup"><span data-stu-id="f6f38-287">Next steps</span></span>

<span data-ttu-id="f6f38-288">このコンテンツの詳細については、GitHub Wiki をご覧ください: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="f6f38-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="f6f38-289">[前へ](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [次へ](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="f6f38-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
