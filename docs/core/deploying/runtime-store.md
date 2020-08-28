---
title: ランタイム パッケージ ストア
description: .NET Core で使用されるランタイム パッケージ ストアとターゲット マニフェストの使用方法について説明します。
ms.date: 08/12/2017
ms.openlocfilehash: e9e27ef535dbd9e7197c323f7e49a9960aeff0f9
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608349"
---
# <a name="runtime-package-store"></a><span data-ttu-id="1d9ce-103">ランタイム パッケージ ストア</span><span class="sxs-lookup"><span data-stu-id="1d9ce-103">Runtime package store</span></span>

<span data-ttu-id="1d9ce-104">NET Core 2.0 以降、ターゲット環境に存在する既知のパッケージのセットに対して、アプリをパッケージ化して展開できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="1d9ce-105">この利点は、展開を高速化し、ディスク領域の使用を減らし、場合によっては起動時のパフォーマンスを向上させることです。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="1d9ce-106">この機能は、パッケージが保存されているディスク上のディレクトリ (通常は、macOS/Linux では */usr/local/share/dotnet/store*、Windows では *C:/Program Files/dotnet/store*) である、*ランタイム パッケージ ストア*として実装されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="1d9ce-107">このディレクトリには、アーキテクチャと[ターゲット フレームワーク](../../standard/frameworks.md)のサブディレクトリがあります。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="1d9ce-108">ファイル レイアウトは、[NuGet アセットがディスク上に配置される](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure)方法と同様です。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

```
\dotnet
    \store
        \x64
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
        \x86
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
```

<span data-ttu-id="1d9ce-109">*ターゲット マニフェスト* ファイルには、ランタイム パッケージ ストアのパッケージが一覧されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="1d9ce-110">開発者は、自社のアプリを発行するときに、このマニフェストをターゲットにすることができます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="1d9ce-111">ターゲット マニフェストは通常、対象となる運用環境の所有者によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="1d9ce-112">ランタイム環境を準備する</span><span class="sxs-lookup"><span data-stu-id="1d9ce-112">Preparing a runtime environment</span></span>

<span data-ttu-id="1d9ce-113">ランタイム環境の管理者は、ランタイム パッケージ ストアとそれに対応するターゲット マニフェストを作成して、アプリを最適化し、展開を高速化してディスク領域の使用を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="1d9ce-114">最初のステップは、ランタイム パッケージ ストアを構成するパッケージを一覧した*パッケージ ストア マニフェスト*を作成することです。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="1d9ce-115">このファイル形式は、プロジェクトのファイル形式 (*csproj*) と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="1d9ce-116">**例**</span><span class="sxs-lookup"><span data-stu-id="1d9ce-116">**Example**</span></span>

<span data-ttu-id="1d9ce-117">次のパッケージ ストア マニフェスト (*packages.csproj*) の例は、[`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) と [`Moq`](https://www.nuget.org/packages/moq/) をランタイム パッケージ ストアに追加するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="1d9ce-118">パッケージ ストア マニフェスト、ランタイム、フレームワークと共に `dotnet store` を実行して、ランタイム パッケージ ストアをプロビジョニングします。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="1d9ce-119">**例**</span><span class="sxs-lookup"><span data-stu-id="1d9ce-119">**Example**</span></span>

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="1d9ce-120">複数のターゲット パッケージ ストアのマニフェストのパスは、コマンドにオプションとパスを繰り返すことで、単一の [`dotnet store`](../tools/dotnet-store.md) コマンドで渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="1d9ce-121">既定では、コマンドの出力は、ユーザーのプロファイルの *.dotnet/store* サブディレクトリにあるパッケージ ストアに出力されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="1d9ce-122">`--output <OUTPUT_DIRECTORY>` オプションを使って、別の場所を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="1d9ce-123">ストアのルート ディレクトリには、ターゲット マニフェストの *artifact.xml* ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="1d9ce-124">このファイルは、ダウンロードに使用でき、発行時にはこのストアをターゲットにするアプリの作成者が使用できます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="1d9ce-125">**例**</span><span class="sxs-lookup"><span data-stu-id="1d9ce-125">**Example**</span></span>

<span data-ttu-id="1d9ce-126">次の *artifact.xml* ファイルは、前の例を実行した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="1d9ce-127">[`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) は `Moq` の依存関係であるため、自動的に *artifacts.xml* マニフェスト ファイルに含められ、表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="1d9ce-128">ターゲット マニフェストに対してアプリを発行する</span><span class="sxs-lookup"><span data-stu-id="1d9ce-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="1d9ce-129">ディスクにターゲット マニフェスト ファイルがある場合、[`dotnet publish`](../tools/dotnet-publish.md) コマンドでアプリを発行するときに、ファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="1d9ce-130">**例**</span><span class="sxs-lookup"><span data-stu-id="1d9ce-130">**Example**</span></span>

```dotnetcli
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="1d9ce-131">結果として発行されるアプリを、ターゲット マニフェストに示されているパッケージがある環境に展開します。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="1d9ce-132">この操作に失敗すると、アプリの起動に失敗することになります。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="1d9ce-133">オプションとパス (例: `--manifest manifest1.xml --manifest manifest2.xml`) を繰り返して、アプリを発行するときに複数のターゲット マニフェストを指定します。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="1d9ce-134">この操作を行うときに、アプリはコマンドに指定されたターゲット マニフェスト ファイルで指定されたパッケージの和集合に対してトリミングされます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

<span data-ttu-id="1d9ce-135">展開に存在するマニフェストの依存関係を持つアプリケーションを展開する場合は (アセンブリは *bin* フォルダーに存在します)、ランタイム パッケージ ストアはそのアセンブリ用のホスト上では*使用されません*。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-135">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="1d9ce-136">ホスト上のランタイム パッケージ ストアに存在するかに関係なく、*bin* フォルダーのアセンブリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-136">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="1d9ce-137">マニフェストに示された依存関係のバージョンは、ランタイム パッケージ ストアの依存関係のバージョンに一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-137">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="1d9ce-138">ターゲット マニフェストの依存関係とランタイム パッケージ ストアに存在するバージョンの間に一致しないバージョンがあり、アプリにその展開に必要なバージョンのパッケージが含まれていない場合、アプリを開始することはできません。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-138">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="1d9ce-139">この例外には、ランタイム パッケージ ストアのアセンブリを呼び出したターゲット マニフェストの名前があり、これは、この不一致のトラブルシューティングに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-139">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="1d9ce-140">展開が発行時に*トリミング*されると、指定した特定のバージョンのマニフェスト パッケージのみが、発行された出力から引かれます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-140">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="1d9ce-141">アプリを開始するには、指定されたバージョンのパッケージがホスト上に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-141">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="1d9ce-142">プロジェクト ファイルでターゲット マニフェストを指定する</span><span class="sxs-lookup"><span data-stu-id="1d9ce-142">Specifying target manifests in the project file</span></span>

<span data-ttu-id="1d9ce-143">[`dotnet publish`](../tools/dotnet-publish.md) コマンドでターゲット マニフェストを指定する代わりに、 **\<TargetManifestFiles>** タグにセミコロンで区切られたパスのリストとして、プロジェクト ファイルに指定することができます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-143">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="1d9ce-144">アプリのターゲット環境が .Net Core プロジェクトのようによく知られている場合にのみ、プロジェクト ファイルにターゲット マニフェストを指定します。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-144">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="1d9ce-145">これは、オープンソース プロジェクトには該当しません。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-145">This isn't the case for open-source projects.</span></span> <span data-ttu-id="1d9ce-146">オープンソース プロジェクトのユーザーは通常、さまざまな運用環境にアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-146">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="1d9ce-147">一般的に、これらの運用環境には、さまざまなインストール済みのパッケージのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-147">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="1d9ce-148">このような環境でターゲット マニフェストについて想定することができないため、[`dotnet publish`](../tools/dotnet-publish.md) の `--manifest` オプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-148">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store-net-core-20-only"></a><span data-ttu-id="1d9ce-149">ASP.NET Core の暗黙的なストア (.NET Core 2.0 のみ)</span><span class="sxs-lookup"><span data-stu-id="1d9ce-149">ASP.NET Core implicit store (.NET Core 2.0 only)</span></span>

<span data-ttu-id="1d9ce-150">ASP.NET Core の暗黙的なストアは、ASP.NET Core 2.0 にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-150">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="1d9ce-151">暗黙的なストアを使用**しない** ASP.NET Core 2.1 以降を、アプリケーションで使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-151">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="1d9ce-152">ASP.NET Core 2.1 以降では、共有フレームワークを使用します。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-152">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="1d9ce-153">.NET Core 2.0 では、このランタイム パッケージ ストア機能は、アプリが[フレームワークに依存する配置](index.md#publish-framework-dependent)のアプリとして配置されるときに、ASP.NET Core アプリによって暗黙的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-153">For .NET Core 2.0, the runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment](index.md#publish-framework-dependent) app.</span></span> <span data-ttu-id="1d9ce-154">[`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) のターゲットには、ターゲット システムの暗黙的なパッケージ ストアを参照しているマニフェストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-154">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="1d9ce-155">さらに、`Microsoft.AspNetCore.All` パッケージに依存するフレームワークに依存するアプリは、アプリとそのアセットのみが含まれ、`Microsoft.AspNetCore.All` メタパッケージにリストされているパッケージは含まれないアプリとして発行されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-155">Additionally, any framework-dependent app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="1d9ce-156">それらのパッケージは、ターゲット システムに存在すると想定されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-156">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="1d9ce-157">ランタイム パッケージ ストアは、.NET Core SDK がインストールされるときに、ホストにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-157">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="1d9ce-158">その他のインストーラーでは、Zip/tarball インストールの .NET Core SDK、`apt-get`、Red Hat Yum、.NET Core Windows Server Hosting バンドル、および手動のランタイム パッケージ ストアのインストールなど、ランタイム パッケージ ストアを提供する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-158">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="1d9ce-159">[フレームワークに依存する配置](index.md#publish-framework-dependent)のアプリを配置するときに、ターゲット環境に .NET Core SDK がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-159">When deploying a [framework-dependent deployment](index.md#publish-framework-dependent) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="1d9ce-160">アプリが ASP.NET Core を含まない環境に配置される場合、次の例のように、プロジェクト ファイルで **\<PublishWithAspNetCoreTargetManifest>** を `false` に指定して、暗黙的なストアを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-160">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="1d9ce-161">[自己完結型の展開](index.md#publish-self-contained)アプリの場合、ターゲット システムには必ずしも必要なマニフェスト パッケージが含まれないと想定されます。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-161">For [self-contained deployment](index.md#publish-self-contained) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="1d9ce-162">そのため、自己完結型アプリの場合、 **\<PublishWithAspNetCoreTargetManifest>** を `true` に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="1d9ce-162">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an self-contained app.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d9ce-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d9ce-163">See also</span></span>

- [<span data-ttu-id="1d9ce-164">dotnet-publish</span><span class="sxs-lookup"><span data-stu-id="1d9ce-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="1d9ce-165">dotnet-store</span><span class="sxs-lookup"><span data-stu-id="1d9ce-165">dotnet-store</span></span>](../tools/dotnet-store.md)
