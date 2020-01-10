---
title: .NET Framework およびアプリケーションの配置
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: b1ba9810b4b0d5a1688318db1093a9ce9bdf8fda
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716460"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="cb195-102">.NET Framework およびアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="cb195-102">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="cb195-103">ここでは、アプリケーションと共に .NET Framework を配置する方法についての概要を示します。</span><span class="sxs-lookup"><span data-stu-id="cb195-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="cb195-104">情報のほとんどは、開発者、OEM、およびエンタープライズ管理者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="cb195-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="cb195-105">コンピュータに .NET Framework をインストールするユーザーは、「[.NET Framework のインストール](../install/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cb195-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="cb195-106">主な配置リソース</span><span class="sxs-lookup"><span data-stu-id="cb195-106">Key Deployment Resources</span></span>

<span data-ttu-id="cb195-107">.NET Framework の配置とサービスの詳細については、次に示す他の MSDN トピックへのリンク先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb195-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="cb195-108">**セットアップと配置**</span><span class="sxs-lookup"><span data-stu-id="cb195-108">**Setup and deployment**</span></span>

- <span data-ttu-id="cb195-109">インストーラーと配置についての一般的な情報:</span><span class="sxs-lookup"><span data-stu-id="cb195-109">General installer and deployment information:</span></span>

  - <span data-ttu-id="cb195-110">インストーラー オプション:</span><span class="sxs-lookup"><span data-stu-id="cb195-110">Installer options:</span></span>

    - [<span data-ttu-id="cb195-111">Web インストーラー</span><span class="sxs-lookup"><span data-stu-id="cb195-111">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="cb195-112">オフライン インストーラー</span><span class="sxs-lookup"><span data-stu-id="cb195-112">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="cb195-113">インストール モード:</span><span class="sxs-lookup"><span data-stu-id="cb195-113">Installation modes:</span></span>

    - [<span data-ttu-id="cb195-114">サイレント インストール</span><span class="sxs-lookup"><span data-stu-id="cb195-114">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="cb195-115">UI の表示</span><span class="sxs-lookup"><span data-stu-id="cb195-115">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="cb195-116">.NET Framework 4.5 のインストール中のシステム再起動の削減</span><span class="sxs-lookup"><span data-stu-id="cb195-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="cb195-117">.NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="cb195-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="cb195-118">.NET Framework とクライアント アプリケーションの配置 (開発者向け):</span><span class="sxs-lookup"><span data-stu-id="cb195-118">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="cb195-119">セットアップと配置プロジェクトでの [InstallShield の使用](deployment-guide-for-developers.md#installshield-deployment)</span><span class="sxs-lookup"><span data-stu-id="cb195-119">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="cb195-120">Visual Studio の ClickOnce アプリケーションの使用</span><span class="sxs-lookup"><span data-stu-id="cb195-120">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="cb195-121">WiX インストール パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="cb195-121">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="cb195-122">カスタム インストーラーの使用</span><span class="sxs-lookup"><span data-stu-id="cb195-122">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="cb195-123">開発者向けの[追加情報](deployment-guide-for-developers.md)</span><span class="sxs-lookup"><span data-stu-id="cb195-123">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="cb195-124">.NET Framework の配置 (OEM と管理者向け):</span><span class="sxs-lookup"><span data-stu-id="cb195-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="cb195-125">Windows アセスメント & デプロイメント キット (ADK)</span><span class="sxs-lookup"><span data-stu-id="cb195-125">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [<span data-ttu-id="cb195-126">管理者ガイド</span><span class="sxs-lookup"><span data-stu-id="cb195-126">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="cb195-127">**サービス**</span><span class="sxs-lookup"><span data-stu-id="cb195-127">**Servicing**</span></span>

- <span data-ttu-id="cb195-128">一般的な情報については、[.NET Framework に関するブログ](https://devblogs.microsoft.com/dotnet/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cb195-128">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="cb195-129">バージョンの検出</span><span class="sxs-lookup"><span data-stu-id="cb195-129">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="cb195-130">Service Pack と更新プログラムの検出</span><span class="sxs-lookup"><span data-stu-id="cb195-130">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="cb195-131">配置を簡素化する機能</span><span class="sxs-lookup"><span data-stu-id="cb195-131">Features That Simplify Deployment</span></span>

<span data-ttu-id="cb195-132">.NET Framework には、アプリケーションを簡単に配置できるようにするための基本機能が数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="cb195-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="cb195-133">ゼロインパクト アプリケーション</span><span class="sxs-lookup"><span data-stu-id="cb195-133">No-impact applications.</span></span>

     <span data-ttu-id="cb195-134">この機能は、アプリケーションを分離し、DLL の競合を解消します。</span><span class="sxs-lookup"><span data-stu-id="cb195-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="cb195-135">既定では、コンポーネントはほかのアプリケーションに影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="cb195-135">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="cb195-136">プライベート コンポーネント (既定)</span><span class="sxs-lookup"><span data-stu-id="cb195-136">Private components by default.</span></span>

     <span data-ttu-id="cb195-137">既定では、コンポーネントはアプリケーション ディレクトリに配置され、コンテナー アプリケーションだけで参照できます。</span><span class="sxs-lookup"><span data-stu-id="cb195-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="cb195-138">制御コードの共有</span><span class="sxs-lookup"><span data-stu-id="cb195-138">Controlled code sharing.</span></span>

     <span data-ttu-id="cb195-139">コードを共有するには、既定の動作を実行する代わりに、共有するためのコードを明示的に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb195-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="cb195-140">side-by-side でのバージョン管理。</span><span class="sxs-lookup"><span data-stu-id="cb195-140">Side-by-side versioning.</span></span>

     <span data-ttu-id="cb195-141">コンポーネントまたはアプリケーションの複数のバージョンを共存させ、使用するバージョンを選択できます。共通言語ランタイムによって、バージョン管理ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="cb195-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="cb195-142">XCOPY による配置およびレプリケーション</span><span class="sxs-lookup"><span data-stu-id="cb195-142">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="cb195-143">自己言及的な、単体で使用できるコンポーネントやアプリケーションは、レジストリ エントリや依存関係を設定せずに配置できます。</span><span class="sxs-lookup"><span data-stu-id="cb195-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="cb195-144">実行時更新</span><span class="sxs-lookup"><span data-stu-id="cb195-144">On-the-fly updates.</span></span>

     <span data-ttu-id="cb195-145">管理者は、ASP.NET などのホストを使用してプログラムの DLL を更新できます。リモート コンピューター上の DLL も更新できます。</span><span class="sxs-lookup"><span data-stu-id="cb195-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="cb195-146">Windows インストーラーとの統合</span><span class="sxs-lookup"><span data-stu-id="cb195-146">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="cb195-147">アプリケーションを配置するときに、通知、発行、修復、およびオンデマンド インストールのすべてを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb195-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="cb195-148">エンタープライズ配置</span><span class="sxs-lookup"><span data-stu-id="cb195-148">Enterprise deployment.</span></span>

     <span data-ttu-id="cb195-149">この機能を使用すると、Active Directory を使用する場合など、ソフトウェアの配布を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="cb195-149">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="cb195-150">ダウンロードとキャッシュ</span><span class="sxs-lookup"><span data-stu-id="cb195-150">Downloading and caching.</span></span>

     <span data-ttu-id="cb195-151">インクリメンタル ダウンロードにより、ダウンロードのサイズを小さくすることができます。また、コンポーネントを分離して、そのアプリケーションだけで使用されるようにし、配置の影響を抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="cb195-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="cb195-152">完全な権利を与えられていないコード</span><span class="sxs-lookup"><span data-stu-id="cb195-152">Partially trusted code.</span></span>

     <span data-ttu-id="cb195-153">ID は、ユーザーではなく、コードに基づきます。証明書関連のダイアログ ボックスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="cb195-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="cb195-154">.NET Framework アプリケーションのパッケージ化と配布</span><span class="sxs-lookup"><span data-stu-id="cb195-154">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="cb195-155">.NET Framework でのパッケージ化および配置についての情報の一部は、ドキュメントの別のトピックで説明します。</span><span class="sxs-lookup"><span data-stu-id="cb195-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="cb195-156">それらのトピックでは、レジストリ エントリを必要としない[アセンブリ](../../standard/assembly/index.md)と呼ばれる自己言及的な単位、名前の一意性を保証し、名前の悪用を防止する[厳密な名前付きアセンブリ](../../standard/assembly/strong-named.md)、DLL 競合に関連した問題の多くを解決する[アセンブリのバージョン管理](../../standard/assembly/versioning.md)についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="cb195-156">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="cb195-157">以下のセクションでは、.NET Framework アプリケーションのパッケージ化および配布について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb195-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="cb195-158">パッケージ化</span><span class="sxs-lookup"><span data-stu-id="cb195-158">Packaging</span></span>

<span data-ttu-id="cb195-159">.NET Framework は、アプリケーション パッケージ化のために、次のオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="cb195-159">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="cb195-160">単一のアセンブリまたはアセンブリのコレクションとしてパッケージ化する。</span><span class="sxs-lookup"><span data-stu-id="cb195-160">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="cb195-161">このオプションでは、.dll ファイルまたは .exe ファイルは既に作成されているため、単に使用するだけです。</span><span class="sxs-lookup"><span data-stu-id="cb195-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="cb195-162">キャビネット (CAB) ファイルとしてパッケージ化する。</span><span class="sxs-lookup"><span data-stu-id="cb195-162">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="cb195-163">このオプションでは、配布やダウンロードの時間を短縮するために、ファイルを .cab ファイルに圧縮します。</span><span class="sxs-lookup"><span data-stu-id="cb195-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="cb195-164">Windows インストーラー パッケージとして、またはその他のインストーラー フォーマットでパッケージ化する。</span><span class="sxs-lookup"><span data-stu-id="cb195-164">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="cb195-165">このオプションでは、Windows インストーラーで使用する .msi ファイルを作成するか、または他のインストーラー用としてアプリケーションをパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="cb195-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="cb195-166">配布</span><span class="sxs-lookup"><span data-stu-id="cb195-166">Distribution</span></span>

<span data-ttu-id="cb195-167">.NET Framework には、アプリケーション配布のために、次のオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="cb195-167">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="cb195-168">XCOPY または FTP を使用する。</span><span class="sxs-lookup"><span data-stu-id="cb195-168">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="cb195-169">共通言語ランタイム アプリケーションは、自己言及的で、レジストリ エントリを必要としないため、XCOPY または FTP を使用して適切なディレクトリに単純にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="cb195-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="cb195-170">その後、そのディレクトリでアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cb195-170">The application can then be run from that directory.</span></span>

- <span data-ttu-id="cb195-171">コードのダウンロードを使用する。</span><span class="sxs-lookup"><span data-stu-id="cb195-171">Use code download.</span></span>

     <span data-ttu-id="cb195-172">アプリケーションをインターネットや企業のイントラネットに配布する場合は、コードをコンピューターにダウンロードし、そこでアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cb195-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="cb195-173">Windows Installer 2.0 などのインストーラー プログラムを使用する。</span><span class="sxs-lookup"><span data-stu-id="cb195-173">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="cb195-174">Windows インストーラー 2.0 を使用して、グローバル アセンブリ キャッシュおよびプライベート ディレクトリへの .NET Framework アセンブリのインストール、修復、または削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="cb195-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="cb195-175">インストール場所</span><span class="sxs-lookup"><span data-stu-id="cb195-175">Installation Location</span></span>

<span data-ttu-id="cb195-176">ランタイムがアプリケーションのアセンブリを検索できるようなアセンブリの配置先については、「[ランタイムがアセンブリを検索する方法](how-the-runtime-locates-assemblies.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cb195-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="cb195-177">アプリケーションの配置方法には、セキュリティの考慮事項も関係します。</span><span class="sxs-lookup"><span data-stu-id="cb195-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="cb195-178">コードが存在する場所に基づいて、マネージド コードにセキュリティ アクセス許可が付与されます。</span><span class="sxs-lookup"><span data-stu-id="cb195-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="cb195-179">インターネットなど、信頼度の低い場所にアプリケーションやコンポーネントを配置すると、そのアプリケーションやコンポーネントが実行できることは制限されます。</span><span class="sxs-lookup"><span data-stu-id="cb195-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="cb195-180">配置とセキュリティ上の考慮事項については、「[コード アクセス セキュリティの基礎](../misc/code-access-security-basics.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cb195-180">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="cb195-181">関連トピック</span><span class="sxs-lookup"><span data-stu-id="cb195-181">Related Topics</span></span>

|<span data-ttu-id="cb195-182">Title</span><span class="sxs-lookup"><span data-stu-id="cb195-182">Title</span></span>|<span data-ttu-id="cb195-183">説明</span><span class="sxs-lookup"><span data-stu-id="cb195-183">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="cb195-184">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="cb195-184">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="cb195-185">共通言語ランタイムが、バインド要求を満たすために、使用するアセンブリをどのように特定するかを説明します。</span><span class="sxs-lookup"><span data-stu-id="cb195-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="cb195-186">アセンブリの読み込みのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="cb195-186">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="cb195-187"><xref:System.InvalidCastException>、<xref:System.MissingMethodException>、およびその他のエラーの原因となることがある型 ID の問題を回避する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb195-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="cb195-188">.NET Framework 4.5 のインストール中のシステム再起動の削減</span><span class="sxs-lookup"><span data-stu-id="cb195-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="cb195-189">再起動をできる限り回避する再起動マネージャーと、.NET Framework をインストールするアプリケーションがそれをどのように利用できるかを説明しています。</span><span class="sxs-lookup"><span data-stu-id="cb195-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="cb195-190">配置ガイド (管理者向け)</span><span class="sxs-lookup"><span data-stu-id="cb195-190">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="cb195-191">システム管理者が、Microsoft Endpoint Configuration Manager を使用して、ネットワーク全体に .NET Framework とその依存関係を配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb195-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="cb195-192">配置ガイド (開発者向け)</span><span class="sxs-lookup"><span data-stu-id="cb195-192">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="cb195-193">開発者による .NET Framework とアプリケーションのユーザーのコンピューターへのインストール方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb195-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="cb195-194">アプリケーション、サービス、およびコンポーネントの配置</span><span class="sxs-lookup"><span data-stu-id="cb195-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="cb195-195">ClickOnce を使用したアプリケーションの発行手順や、Windows インストーラー テクノロジなど、Visual Studio の配置オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cb195-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="cb195-196">ClickOnce アプリケーションの発行</span><span class="sxs-lookup"><span data-stu-id="cb195-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="cb195-197">Windows フォーム アプリケーションをパッケージ化し、これを ClickOnce でネットワーク上のクライアント コンピューターに配置する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="cb195-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="cb195-198">リソースのパッケージ化と配置</span><span class="sxs-lookup"><span data-stu-id="cb195-198">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="cb195-199">.NET Framework でリソースのパッケージ化と配置に使用する、ハブ アンド スポーク モデルについて説明します。リソースの名前付け規則、フォールバック プロセス、およびパッケージ化の代替策についても説明します。</span><span class="sxs-lookup"><span data-stu-id="cb195-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="cb195-200">相互運用アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="cb195-200">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="cb195-201">相互運用アプリケーションの出荷方法とインストール方法について説明します。通常、相互運用アプリケーションには、.NET Framework クライアント アセンブリ、個別の COM タイプ ライブラリを表す 1 つ以上の相互運用機能アセンブリ、および 1 つ以上の登録済み COM コンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cb195-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="cb195-202">方法: .NET Framework 4.5 インストーラーの進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="cb195-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="cb195-203">進行状況のビューを独自に表示する一方で、.NET Framework セットアップ プロセスをサイレントで起動および追跡する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="cb195-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="cb195-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb195-204">See also</span></span>

- [<span data-ttu-id="cb195-205">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="cb195-205">Development Guide</span></span>](../development-guide.md)
