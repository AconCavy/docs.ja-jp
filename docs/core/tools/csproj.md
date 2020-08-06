---
title: .NET Core の csproj 形式に追加されたもの
description: 既存の csproj ファイルと .NET Core の csproj ファイルの違いについて説明します
ms.date: 04/08/2019
ms.openlocfilehash: a0cbead27e52af3114d9c44fd19c966e665a2850
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2020
ms.locfileid: "87427009"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="4b679-103">.NET Core の csproj 形式に追加されたもの</span><span class="sxs-lookup"><span data-stu-id="4b679-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="4b679-104">ここでは、*project.json* から *csproj* および [MSBuild](https://github.com/Microsoft/MSBuild) への移行に伴ってプロジェクト ファイルに追加された変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b679-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="4b679-105">一般的なプロジェクト ファイルの構文とリファレンスの詳細については、[MSBuild プロジェクト ファイル](/visualstudio/msbuild/msbuild-project-file-schema-reference)のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b679-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="4b679-106">暗黙的なパッケージ参照</span><span class="sxs-lookup"><span data-stu-id="4b679-106">Implicit package references</span></span>

<span data-ttu-id="4b679-107">メタパッケージは、プロジェクト ファイルの `<TargetFramework>` または `<TargetFrameworks>` プロパティに指定されている対象フレームワークに基づいて暗黙的に参照されています。</span><span class="sxs-lookup"><span data-stu-id="4b679-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="4b679-108">`<TargetFramework>` を指定すると、順序に関係なく `<TargetFrameworks>` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="4b679-109">推奨事項</span><span class="sxs-lookup"><span data-stu-id="4b679-109">Recommendations</span></span>

<span data-ttu-id="4b679-110">`Microsoft.NETCore.App` または `NETStandard.Library` メタパッケージは暗黙的に参照されるので、ベスト プラクティスとして以下が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-110">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="4b679-111">.NET Core または .NET Standard を対象とするとき、プロジェクト ファイルの `<PackageReference>` アイテム経由で `Microsoft.NETCore.App` または `NETStandard.Library` メタパッケージを明示的に参照しないようにします。</span><span class="sxs-lookup"><span data-stu-id="4b679-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="4b679-112">.NET Core を対象にするとき、特定バージョンのランタイムが必要な場合、メタパッケージを参照するのではなく、プロジェクト内で `<RuntimeFrameworkVersion>` プロパティを使用します (`1.0.4` など)。</span><span class="sxs-lookup"><span data-stu-id="4b679-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="4b679-113">[自己完結型の展開](../deploying/index.md#publish-self-contained)を使用し、特定のパッチ バージョンの 1.0.0 LTS ランタイムが必要な場合などにこの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4b679-113">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="4b679-114">.NET Standard を対象にするとき、特定バージョンの `NETStandard.Library` メタパッケージが必要な場合、`<NetStandardImplicitPackageVersion>` プロパティを使用し、必要なバージョンを設定できます。</span><span class="sxs-lookup"><span data-stu-id="4b679-114">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="4b679-115">.NET Framework プロジェクトでは、`Microsoft.NETCore.App` または `NETStandard.Library` メタパッケージに参照を明示的に追加したり、更新したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="4b679-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="4b679-116">.NET Standard ベースの NuGet パッケージを使用するとき、何らかのバージョンの `NETStandard.Library` が必要であれば、NuGet はそのバージョンを自動的にインストールします。</span><span class="sxs-lookup"><span data-stu-id="4b679-116">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="4b679-117">一部のパッケージ参照に対する暗黙的なバージョン</span><span class="sxs-lookup"><span data-stu-id="4b679-117">Implicit version for some package references</span></span>

<span data-ttu-id="4b679-118">[`<PackageReference>`](#packagereference) を使用するほとんどの場合に、`Version` 属性を設定して、使用する NuGet パッケージのバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b679-118">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="4b679-119">ただし、.NET Core 2.1 または 2.2 を使用し、[Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) または [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage) を参照するときは、その属性は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4b679-119">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="4b679-120">.NET Core SDK では、使用する必要があるこれらのパッケージのバージョンを自動的に選択できます。</span><span class="sxs-lookup"><span data-stu-id="4b679-120">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="4b679-121">推奨事項</span><span class="sxs-lookup"><span data-stu-id="4b679-121">Recommendation</span></span>

<span data-ttu-id="4b679-122">`Microsoft.AspNetCore.App` または `Microsoft.AspNetCore.All` パッケージを参照するときは、それらのバージョンを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="4b679-122">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="4b679-123">バージョンを指定すると、SDK で警告 NETSDK1071 が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4b679-123">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="4b679-124">この警告を解決するには、次の例のようなパッケージのバージョンを削除します。</span><span class="sxs-lookup"><span data-stu-id="4b679-124">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="4b679-125">既知の問題: .NET Core 2.1 SDK では、プロジェクトでも Microsoft.NET.Sdk.Web が使用されている場合にのみ、この構文がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="4b679-125">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="4b679-126">これは、.NET Core 2.2 SDK で解決されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-126">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="4b679-127">ASP.NET Core メタパッケージに対するこれらの参照では、ほとんどの通常の NuGet パッケージとは動作が若干異なります。</span><span class="sxs-lookup"><span data-stu-id="4b679-127">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="4b679-128">これらのメタパッケージを使用するアプリケーションの[フレームワーク依存の展開](../deploying/index.md#publish-runtime-dependent)では、ASP.NET Core 共有フレームワークが自動的に利用されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-128">[Framework-dependent deployments](../deploying/index.md#publish-runtime-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="4b679-129">メタパッケージを使用する場合、参照される ASP.NET Core NuGet パッケージの資産は、アプリケーションと共に展開**されません**。ASP.NET Core 共有フレームワークにはこれらの資産が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b679-129">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="4b679-130">共有フレームワーク内の資産は、アプリケーションの起動時間を向上させるため、ターゲット プラットフォームに対して最適化されています。</span><span class="sxs-lookup"><span data-stu-id="4b679-130">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="4b679-131">共有フレームワークについて詳しくは、「[.NET Core の配布パッケージ](../distribution-packaging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b679-131">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="4b679-132">バージョンを "*指定する*" と、フレームワーク依存の展開では ASP.NET Core の共有フレームワークの "*最小*" バージョンとして扱われ、自己完結型の展開では "*厳密な*" バージョンとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="4b679-132">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="4b679-133">これには、次のような影響があります。</span><span class="sxs-lookup"><span data-stu-id="4b679-133">This can have the following consequences:</span></span>

- <span data-ttu-id="4b679-134">サーバーにインストールされている ASP.NET Core のバージョンが、PackageReference で指定されているバージョンより小さい場合、.NET Core プロセスの起動は失敗します。</span><span class="sxs-lookup"><span data-stu-id="4b679-134">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="4b679-135">Azure などのホスティング環境でメタパッケージの更新プログラムが使用できるようになる前に、NuGet.org で更新プログラムが利用可能になることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="4b679-135">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="4b679-136">PackageReference でのバージョンを ASP.NET Core に更新すると、展開されているアプリケーションが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4b679-136">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="4b679-137">アプリケーションが[自己完結型の展開](../deploying/index.md#publish-self-contained)として展開されている場合、アプリケーションに .NET Core の最新のセキュリティ更新プログラムが含まれていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4b679-137">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="4b679-138">バージョンを指定しないと、SDK は自己完結型の展開に ASP.NET Core の最新バージョンを自動的に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4b679-138">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="4b679-139">.NET Core プロジェクトの既定のコンパイルの include</span><span class="sxs-lookup"><span data-stu-id="4b679-139">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="4b679-140">最新バージョンの SDK の *csproj* 形式に移行すると共に、コンパイル項目と、SDK プロパティ ファイルに埋め込みリソースの既定の include と exclude を SDK プロパティ ファイルに移行しました。</span><span class="sxs-lookup"><span data-stu-id="4b679-140">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="4b679-141">つまり、これらの項目をプロジェクト ファイルに指定する必要はなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4b679-141">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="4b679-142">これを行う主な理由は、プロジェクト ファイルを見やすくするためです。</span><span class="sxs-lookup"><span data-stu-id="4b679-142">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="4b679-143">SDK の既定値は、最も一般的な使用例に対応しているので、作成するプロジェクトごとに繰り返す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4b679-143">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="4b679-144">その結果、プロジェクト ファイルが小さくなり、わかりやすく、編集が必要な場合に編集しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="4b679-144">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="4b679-145">次の表は、SDK に含まれる、および除外される要素と [glob](https://en.wikipedia.org/wiki/Glob_(programming)) の一覧です。</span><span class="sxs-lookup"><span data-stu-id="4b679-145">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="4b679-146">要素</span><span class="sxs-lookup"><span data-stu-id="4b679-146">Element</span></span>           | <span data-ttu-id="4b679-147">含まれる glob</span><span class="sxs-lookup"><span data-stu-id="4b679-147">Include glob</span></span>                              | <span data-ttu-id="4b679-148">除外される glob</span><span class="sxs-lookup"><span data-stu-id="4b679-148">Exclude glob</span></span>                                                  | <span data-ttu-id="4b679-149">glob の削除</span><span class="sxs-lookup"><span data-stu-id="4b679-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="4b679-150">Compile</span><span class="sxs-lookup"><span data-stu-id="4b679-150">Compile</span></span>           | <span data-ttu-id="4b679-151">\*\*/\*.cs (または他の言語拡張機能)</span><span class="sxs-lookup"><span data-stu-id="4b679-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="4b679-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="4b679-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="4b679-153">N/A</span><span class="sxs-lookup"><span data-stu-id="4b679-153">N/A</span></span>                      |
| <span data-ttu-id="4b679-154">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="4b679-154">EmbeddedResource</span></span>  | <span data-ttu-id="4b679-155">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="4b679-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="4b679-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="4b679-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="4b679-157">N/A</span><span class="sxs-lookup"><span data-stu-id="4b679-157">N/A</span></span>                      |
| <span data-ttu-id="4b679-158">None</span><span class="sxs-lookup"><span data-stu-id="4b679-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="4b679-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="4b679-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="4b679-160">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="4b679-160">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="4b679-161">**除外される glob** では、`./bin` と `./obj` フォルダーが常に除外されます。これらはそれぞれ MSBuild プロパティ `$(BaseOutputPath)` と `$(BaseIntermediateOutputPath)` で表されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-161">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="4b679-162">全体として、すべての除外は `$(DefaultItemExcludes)` で表されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-162">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="4b679-163">プロジェクトに glob があり、最新の SDK を使用してビルドしようとすると、次のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4b679-163">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="4b679-164">重複するコンパイル項目が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="4b679-164">Duplicate Compile items were included.</span></span> <span data-ttu-id="4b679-165">.NET SDK には、既定でプロジェクト ディレクトリのコンパイル項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b679-165">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="4b679-166">これらの項目をプロジェクト ファイルから削除するか、プロジェクト ファイルに明示的に含める場合は 'EnableDefaultCompileItems' プロパティを 'false' に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="4b679-166">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="4b679-167">このエラーを回避するには、前の表にあるものと一致する明示的な `Compile` 項目を削除するか、次のように `<EnableDefaultCompileItems>` プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-167">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="4b679-168">このプロパティを `false` に設定すると、暗黙的に含める動作が無効になり、以前の SDK の動作に戻り、プロジェクトに既定の glob が指定されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-168">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="4b679-169">この変更で、他の include の主なしくみは変わりません。</span><span class="sxs-lookup"><span data-stu-id="4b679-169">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="4b679-170">ただし、たとえばアプリで発行する一部のファイルを指定する場合は、*csproj* で既知のしくみ (たとえば `<Content>` 要素) を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4b679-170">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="4b679-171">`<EnableDefaultCompileItems>` は `Compile` glob のみを無効にし、\*.cs 項目にも適用される暗黙的 `None` glob など、他の Glob には影響しません。</span><span class="sxs-lookup"><span data-stu-id="4b679-171">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="4b679-172">そのため、**ソリューション エクスプローラー**は \*.cs 項目を `None` 項目として含まれた、プロジェクトの一部として引き続き表示します。</span><span class="sxs-lookup"><span data-stu-id="4b679-172">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="4b679-173">同様に、次のように `<EnableDefaultNoneItems>` を false に設定し、暗黙的 `None` glob を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="4b679-173">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="4b679-174">**暗黙的 glob をすべて**無効にするには、`<EnableDefaultItems>` プロパティを `false` に設定します。次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b679-174">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="4b679-175">MSBuild と同じようにプロジェクト全体を表示する方法</span><span class="sxs-lookup"><span data-stu-id="4b679-175">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="4b679-176">これらの csproj 変更でプロジェクト ファイルが大幅に簡素化されますが、SDK とそのターゲットが追加されたとき、MSBuild と同様にプロジェクト全体を表示すると便利なことがあります。</span><span class="sxs-lookup"><span data-stu-id="4b679-176">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="4b679-177">[`dotnet msbuild`](dotnet-msbuild.md) コマンドの [`/pp` スイッチ](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)でプロジェクトを事前処理します。インポートされるファイル、そのソース、ビルドに対するその貢献が、実際にプロジェクトをビルドすることなく、表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-177">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="4b679-178">プロジェクトにターゲット フレームワークが複数存在する場合、MSBuild プロパティとして指定し、1 つだけにコマンドの結果を集中させてください。</span><span class="sxs-lookup"><span data-stu-id="4b679-178">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="4b679-179">追加</span><span class="sxs-lookup"><span data-stu-id="4b679-179">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="4b679-180">SDK 属性</span><span class="sxs-lookup"><span data-stu-id="4b679-180">Sdk attribute</span></span>

<span data-ttu-id="4b679-181">*.csproj* ファイルのルート `<Project>` 要素には、`Sdk` という新しい属性があります。</span><span class="sxs-lookup"><span data-stu-id="4b679-181">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="4b679-182">`Sdk` は、プロジェクトで使用される SDK を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-182">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="4b679-183">[レイヤー化のドキュメント](cli-msbuild-architecture.md)で説明されているように、SDK は、.NET Core コードをビルドできる MSBuild [タスク](/visualstudio/msbuild/msbuild-tasks)および[ターゲット](/visualstudio/msbuild/msbuild-targets)のセットです。</span><span class="sxs-lookup"><span data-stu-id="4b679-183">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="4b679-184">.NET Core では、次の SDK を利用できます。</span><span class="sxs-lookup"><span data-stu-id="4b679-184">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="4b679-185">ID が `Microsoft.NET.Sdk` の .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="4b679-185">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="4b679-186">ID が `Microsoft.NET.Sdk.Web` の .NET Core Web SDK</span><span class="sxs-lookup"><span data-stu-id="4b679-186">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="4b679-187">ID が `Microsoft.NET.Sdk.Razor` の .NET Core Razor クラス ライブラリ SDK</span><span class="sxs-lookup"><span data-stu-id="4b679-187">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="4b679-188">ID が `Microsoft.NET.Sdk.Worker` の .NET Core Worker Service (.NET Core 3.0 以降)</span><span class="sxs-lookup"><span data-stu-id="4b679-188">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="4b679-189">ID が `Microsoft.NET.Sdk.WindowsDesktop` の .NET Core WinForms および WPF (.NET Core 3.0 以降)</span><span class="sxs-lookup"><span data-stu-id="4b679-189">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="4b679-190">.NET Core ツールを使用し、コードをビルドするには、`Sdk` 属性を `<Project>` 要素の ID のいずれかに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b679-190">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="4b679-191">PackageReference</span><span class="sxs-lookup"><span data-stu-id="4b679-191">PackageReference</span></span>

<span data-ttu-id="4b679-192">`<PackageReference>` 項目要素では、[プロジェクトでの NuGet の依存関係](/nuget/consume-packages/package-references-in-project-files)を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-192">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="4b679-193">`Include` 属性は、パッケージ ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-193">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="4b679-194">バージョン</span><span class="sxs-lookup"><span data-stu-id="4b679-194">Version</span></span>

<span data-ttu-id="4b679-195">必須の `Version` 属性では、復元するパッケージのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-195">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="4b679-196">この属性は、[NuGet バージョンの範囲](/nuget/concepts/package-versioning#version-ranges)スキームの規則に従います。</span><span class="sxs-lookup"><span data-stu-id="4b679-196">The attribute respects the rules of the [NuGet version range](/nuget/concepts/package-versioning#version-ranges) scheme.</span></span> <span data-ttu-id="4b679-197">既定の動作は、最小一致バージョンです。</span><span class="sxs-lookup"><span data-stu-id="4b679-197">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="4b679-198">たとえば、`Version="1.2.3"` を指定すると、NuGet 表記の `[1.2.3, )` と同等になります。つまり、パッケージのバージョンは、使用できる場合は 1.2.3 になり、使用できない場合はその後のバージョンになります。</span><span class="sxs-lookup"><span data-stu-id="4b679-198">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="4b679-199">IncludeAssets、ExcludeAssets、PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="4b679-199">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="4b679-200">`IncludeAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットのうち、使う必要があるものを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-200">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="4b679-201">既定では、パッケージのすべてのアセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b679-201">By default, all package assets are included.</span></span>

<span data-ttu-id="4b679-202">`ExcludeAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットのうち、使う必要がないものを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-202">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="4b679-203">`PrivateAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットで、使う必要はあるが、次のプロジェクトに渡してはならないものを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-203">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="4b679-204">この属性が存在しない場合、`Analyzers`、`Build`、`ContentFiles` アセットは既定でプライベートになります。</span><span class="sxs-lookup"><span data-stu-id="4b679-204">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="4b679-205">`PrivateAssets` は *project.json*/*xproj* `SuppressParent` 要素と同等です。</span><span class="sxs-lookup"><span data-stu-id="4b679-205">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="4b679-206">これらの属性には以下の項目を 1 つ以上含めることができ、複数ある場合はセミコロン `;` 文字で区切ります。</span><span class="sxs-lookup"><span data-stu-id="4b679-206">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="4b679-207">`Compile` - コンパイルで使用できる *lib* フォルダーの内容です。</span><span class="sxs-lookup"><span data-stu-id="4b679-207">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="4b679-208">`Runtime` - 配布する *runtime* フォルダーの内容です。</span><span class="sxs-lookup"><span data-stu-id="4b679-208">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="4b679-209">`ContentFiles` - 使用する *contentfiles* フォルダーの内容です。</span><span class="sxs-lookup"><span data-stu-id="4b679-209">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="4b679-210">`Build` - 使用する *build* フォルダーのプロパティ/ターゲットです。</span><span class="sxs-lookup"><span data-stu-id="4b679-210">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="4b679-211">`Native` - ランタイムの *output* フォルダーにコピーするネイティブ アセットの内容です。</span><span class="sxs-lookup"><span data-stu-id="4b679-211">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="4b679-212">`Analyzers` - アナライザーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-212">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="4b679-213">代わりに、次の値を属性に含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="4b679-213">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="4b679-214">`None` - いずれのアセットも使用されません。</span><span class="sxs-lookup"><span data-stu-id="4b679-214">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="4b679-215">`All` - すべてのアセットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-215">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="4b679-216">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="4b679-216">DotNetCliToolReference</span></span>

<span data-ttu-id="4b679-217">`<DotNetCliToolReference>` 項目要素は、プロジェクトのコンテキストでユーザーが復元を望む CLI ツールを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-217">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="4b679-218">*project.json* の `tools` ノードに代わるものです。</span><span class="sxs-lookup"><span data-stu-id="4b679-218">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="4b679-219">`DotNetCliToolReference` は[現在非推奨であり](https://github.com/dotnet/announcements/issues/107)、[.NET Core Local Tools](./global-tools.md#install-a-local-tool) の使用が推奨されています。</span><span class="sxs-lookup"><span data-stu-id="4b679-219">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](./global-tools.md#install-a-local-tool).</span></span>

#### <a name="version"></a><span data-ttu-id="4b679-220">バージョン</span><span class="sxs-lookup"><span data-stu-id="4b679-220">Version</span></span>

<span data-ttu-id="4b679-221">`Version` は、復元するパッケージのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="4b679-222">この属性は、[NuGet バージョン管理](/nuget/create-packages/dependency-versions#version-ranges)スキームの規則に従います。</span><span class="sxs-lookup"><span data-stu-id="4b679-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="4b679-223">既定の動作は、最小一致バージョンです。</span><span class="sxs-lookup"><span data-stu-id="4b679-223">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="4b679-224">たとえば、`Version="1.2.3"` を指定すると、NuGet 表記の `[1.2.3, )` と同等になります。つまり、パッケージのバージョンは、使用できる場合は 1.2.3 になり、使用できない場合はその後のバージョンになります。</span><span class="sxs-lookup"><span data-stu-id="4b679-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="4b679-225">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="4b679-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="4b679-226">`<RuntimeIdentifiers>` プロパティ要素では、プロジェクトの[ランタイム識別子 (RID)](../rid-catalog.md) のセミコロン区切りリストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4b679-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="4b679-227">RID により、自己完結型の展開を発行できます。</span><span class="sxs-lookup"><span data-stu-id="4b679-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="4b679-228">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="4b679-228">RuntimeIdentifier</span></span>

<span data-ttu-id="4b679-229">`<RuntimeIdentifier>` プロパティ要素では、プロジェクトの[ランタイム識別子 (RID)](../rid-catalog.md) を 1 つだけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="4b679-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="4b679-230">RID により、自己完結型の展開を発行できます。</span><span class="sxs-lookup"><span data-stu-id="4b679-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="4b679-231">複数のランタイムに対して発行する必要がある場合、代わりに `<RuntimeIdentifiers>` (複数) を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b679-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="4b679-232">`<RuntimeIdentifier>` では、必要なランタイムが 1 つだけのとき、ビルドが速くなります。</span><span class="sxs-lookup"><span data-stu-id="4b679-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="4b679-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="4b679-233">PackageTargetFallback</span></span>

<span data-ttu-id="4b679-234">`<PackageTargetFallback>` プロパティ要素では、パッケージの復元時に使用する、互換性のある一連のターゲットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4b679-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="4b679-235">dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) を使用するパッケージに、dotnet TxM を宣言しないパッケージで動作することを許可するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="4b679-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="4b679-236">プロジェクトで dotnet TxM を使用せず、依存するすべてのパッケージに dotnet TxM を与える必要がある場合、非 dotnet プラットフォームを dotnet 対応にするためにプロジェクトに `<PackageTargetFallback>` を追加します。</span><span class="sxs-lookup"><span data-stu-id="4b679-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="4b679-237">次の例では、プロジェクトのすべてのターゲットにフォールバックを提供しています。</span><span class="sxs-lookup"><span data-stu-id="4b679-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="4b679-238">次の例では、`netcoreapp2.1` ターゲットにのみフォールバックを指定しています。</span><span class="sxs-lookup"><span data-stu-id="4b679-238">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="4b679-239">ビルド イベント</span><span class="sxs-lookup"><span data-stu-id="4b679-239">Build events</span></span>

<span data-ttu-id="4b679-240">プロジェクト ファイルでビルド前およびビルド後のイベントを指定する方法が変更されました。</span><span class="sxs-lookup"><span data-stu-id="4b679-240">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="4b679-241">$ (ProjectDir) などのマクロが解決されないため、PreBuildEvent および PostBuildEvent プロパティは SDK スタイルのプロジェクト形式では推奨されません。</span><span class="sxs-lookup"><span data-stu-id="4b679-241">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="4b679-242">たとえば、次のコードはサポートされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4b679-242">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

<span data-ttu-id="4b679-243">SDK スタイルのプロジェクトでは、`PreBuild` または `PostBuild` という名前の MSBuild ターゲットを使用し、`PreBuild` の `BeforeTargets` プロパティまたは `AfterTargets` の `PostBuild` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-243">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="4b679-244">前の例では、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b679-244">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="4b679-245">MSBuild ターゲットには任意の名前を使用できますが、Visual Studio IDE では `PreBuild` と `PostBuild` ターゲットが認識されるため、Visual Studio IDE でコマンドを編集できるようにするには、これらの名前を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4b679-245">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="4b679-246">NuGet メタデータ プロパティ</span><span class="sxs-lookup"><span data-stu-id="4b679-246">NuGet metadata properties</span></span>

<span data-ttu-id="4b679-247">MSBuild への移行に伴い、*project.json* ファイルから *csproj* ファイルに NuGet パッケージをパックするときに使用される入力メタデータを移動しました。</span><span class="sxs-lookup"><span data-stu-id="4b679-247">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="4b679-248">入力は MSBuild プロパティなので、`<PropertyGroup>` グループ内で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b679-248">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="4b679-249">次に示すのは、`dotnet pack` コマンドまたは SDK の一部である `Pack` MSBuild ターゲットを使用するときに、パッキング プロセスへの入力として使用されるプロパティの一覧です。</span><span class="sxs-lookup"><span data-stu-id="4b679-249">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="4b679-250">IsPackable</span><span class="sxs-lookup"><span data-stu-id="4b679-250">IsPackable</span></span>

<span data-ttu-id="4b679-251">プロジェクトをパックできるかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="4b679-251">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="4b679-252">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="4b679-252">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="4b679-253">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="4b679-253">PackageVersion</span></span>

<span data-ttu-id="4b679-254">結果のパッケージのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-254">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="4b679-255">すべてのフォームの NuGet バージョン文字列を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="4b679-255">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="4b679-256">既定値は `$(Version)` です。つまり、プロジェクトのプロパティ `Version` の値です。</span><span class="sxs-lookup"><span data-stu-id="4b679-256">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="4b679-257">PackageId</span><span class="sxs-lookup"><span data-stu-id="4b679-257">PackageId</span></span>

<span data-ttu-id="4b679-258">結果のパッケージの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-258">Specifies the name for the resulting package.</span></span> <span data-ttu-id="4b679-259">指定しない場合、`pack` 操作の既定では、`AssemblyName` またはディレクトリ名をパッケージ名として使用します。</span><span class="sxs-lookup"><span data-stu-id="4b679-259">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="4b679-260">Title</span><span class="sxs-lookup"><span data-stu-id="4b679-260">Title</span></span>

<span data-ttu-id="4b679-261">人が読みやすいパッケージのタイトル。通常、nuget.org と、Visual Studio のパッケージ マネージャーの UI 画面で使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-261">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="4b679-262">指定しない場合、パッケージ ID が代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-262">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="4b679-263">Authors</span><span class="sxs-lookup"><span data-stu-id="4b679-263">Authors</span></span>

<span data-ttu-id="4b679-264">nuget.org のプロファイル名と一致するパッケージ作成者をセミコロンで区切った一覧。これらは nuget.org の NuGet ギャラリーに表示され、同じ作成者によるパッケージの相互参照に使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-264">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="4b679-265">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="4b679-265">PackageDescription</span></span>

<span data-ttu-id="4b679-266">UI 画面用のパッケージの長い説明。</span><span class="sxs-lookup"><span data-stu-id="4b679-266">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="4b679-267">説明</span><span class="sxs-lookup"><span data-stu-id="4b679-267">Description</span></span>

<span data-ttu-id="4b679-268">アセンブリの長い説明。</span><span class="sxs-lookup"><span data-stu-id="4b679-268">A long description for the assembly.</span></span> <span data-ttu-id="4b679-269">`PackageDescription` が指定されていない場合、このプロパティはパッケージの説明としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-269">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="4b679-270">Copyright</span><span class="sxs-lookup"><span data-stu-id="4b679-270">Copyright</span></span>

<span data-ttu-id="4b679-271">パッケージの著作権の詳細。</span><span class="sxs-lookup"><span data-stu-id="4b679-271">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="4b679-272">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="4b679-272">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="4b679-273">クライアントがユーザーに対して、パッケージのインストール前にパッケージ ライセンスに同意することを必須にするかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="4b679-273">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="4b679-274">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="4b679-274">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="4b679-275">DevelopmentDependency</span><span class="sxs-lookup"><span data-stu-id="4b679-275">DevelopmentDependency</span></span>

<span data-ttu-id="4b679-276">開発専用の依存関係としてパッケージをマークするかどうかを指定するブール値。指定すると、そのパッケージは他のパッケージに依存関係として含まれなくなります。</span><span class="sxs-lookup"><span data-stu-id="4b679-276">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="4b679-277">PackageReference (NuGet 4.8 以降) では、このフラグは、コンパイルからコンパイル時アセットが除外されることも意味します。</span><span class="sxs-lookup"><span data-stu-id="4b679-277">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="4b679-278">詳しくは、「[DevelopmentDependency support for PackageReference (PackageReference に対する DevelopmentDependency のサポート)](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b679-278">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="4b679-279">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="4b679-279">PackageLicenseExpression</span></span>

<span data-ttu-id="4b679-280">[SPDX ライセンス識別子](https://spdx.org/licenses/)、または式です。</span><span class="sxs-lookup"><span data-stu-id="4b679-280">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="4b679-281">たとえば、`Apache-2.0` のようにします。</span><span class="sxs-lookup"><span data-stu-id="4b679-281">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="4b679-282">[SPDX ライセンス識別子](https://spdx.org/licenses/)の完全な一覧はこちらをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b679-282">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="4b679-283">ライセンス タイプ式を使用する場合、NuGet.org では OSI または FSF で承認されたライセンスのみが受け付けられます。</span><span class="sxs-lookup"><span data-stu-id="4b679-283">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="4b679-284">ライセンス式の正確な構文については、[ABNF](https://tools.ietf.org/html/rfc5234) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b679-284">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```abnf
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> <span data-ttu-id="4b679-285">一度に指定できるのは、`PackageLicenseExpression`、`PackageLicenseFile`、`PackageLicenseUrl` のどれか 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="4b679-285">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="4b679-286">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="4b679-286">PackageLicenseFile</span></span>

<span data-ttu-id="4b679-287">SPDX 識別子が割り当てられていないライセンス、またはカスタム ライセンスを使用している場合、パッケージ内のライセンス ファイルへのパス (それ以外の場合は、`PackageLicenseExpression` が優先されます)</span><span class="sxs-lookup"><span data-stu-id="4b679-287">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="4b679-288">`PackageLicenseUrl` が置き換えられ、`PackageLicenseExpression` と組み合わせることはできず、Visual Studio バージョン 15.9.4 および.NET SDK 2.1.502 または 2.2.101 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="4b679-288">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="4b679-289">プロジェクトに明示的に追加することによって、ライセンス ファイルをパックする必要があります。使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4b679-289">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="4b679-290">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="4b679-290">PackageLicenseUrl</span></span>

<span data-ttu-id="4b679-291">パッケージに適用されるライセンスの URL。</span><span class="sxs-lookup"><span data-stu-id="4b679-291">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="4b679-292">("_Visual Studio 15.9.4、.NET SDK 2.1.502 および 2.2.101 以降では非推奨_")</span><span class="sxs-lookup"><span data-stu-id="4b679-292">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageicon"></a><span data-ttu-id="4b679-293">PackageIcon</span><span class="sxs-lookup"><span data-stu-id="4b679-293">PackageIcon</span></span>

<span data-ttu-id="4b679-294">パッケージ アイコンとして使用するパッケージ内の画像へのパス。</span><span class="sxs-lookup"><span data-stu-id="4b679-294">A path to an image in the package to use as a package icon.</span></span> <span data-ttu-id="4b679-295">`icon` メタデータの詳細については、[こちら](/nuget/reference/nuspec#icon)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b679-295">Read more about [`icon` metadata](/nuget/reference/nuspec#icon).</span></span> <span data-ttu-id="4b679-296">PackageIcon が優先され、[PackageIconUrl は非推奨とされます](/nuget/reference/msbuild-targets#packageiconurl)。</span><span class="sxs-lookup"><span data-stu-id="4b679-296">[PackageIconUrl is deprecated](/nuget/reference/msbuild-targets#packageiconurl) in favor of PackageIcon.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="4b679-297">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="4b679-297">PackageReleaseNotes</span></span>

<span data-ttu-id="4b679-298">パッケージのリリース ノート。</span><span class="sxs-lookup"><span data-stu-id="4b679-298">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="4b679-299">PackageTags</span><span class="sxs-lookup"><span data-stu-id="4b679-299">PackageTags</span></span>

<span data-ttu-id="4b679-300">パッケージを指定するタグのセミコロン区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="4b679-300">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="4b679-301">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="4b679-301">PackageOutputPath</span></span>

<span data-ttu-id="4b679-302">パックされたパッケージをドロップする出力パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-302">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="4b679-303">既定値は `$(OutputPath)` です。</span><span class="sxs-lookup"><span data-stu-id="4b679-303">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="4b679-304">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="4b679-304">IncludeSymbols</span></span>
<span data-ttu-id="4b679-305">このブール値は、プロジェクトをパックするときに、パッケージが追加のシンボル パッケージを作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-305">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="4b679-306">シンボル パッケージの形式は、`SymbolPackageFormat` プロパティで制御します。</span><span class="sxs-lookup"><span data-stu-id="4b679-306">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="4b679-307">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="4b679-307">SymbolPackageFormat</span></span>
<span data-ttu-id="4b679-308">シンボル パッケージの形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-308">Specifies the format of the symbols package.</span></span> <span data-ttu-id="4b679-309">"symbols.nupkg" では、 *.symbols.nupkg* 拡張子と共に、PDB、DLL、およびその他の出力ファイルを含む従来のシンボル パッケージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-309">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="4b679-310">"snupkg" では、ポータブル PDB を含む snupkg シンボル パッケージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-310">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="4b679-311">既定値は "symbols.nupkg" です。</span><span class="sxs-lookup"><span data-stu-id="4b679-311">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="4b679-312">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="4b679-312">IncludeSource</span></span>

<span data-ttu-id="4b679-313">このブール値は、パック プロセスでソース パッケージを作成するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4b679-313">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="4b679-314">ソース パッケージには、ライブラリのソース コードと PDB ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b679-314">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="4b679-315">ソース ファイルは、結果のパッケージ ファイルの `src/ProjectName` ディレクトリに置かれます。</span><span class="sxs-lookup"><span data-stu-id="4b679-315">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="4b679-316">IsTool</span><span class="sxs-lookup"><span data-stu-id="4b679-316">IsTool</span></span>

<span data-ttu-id="4b679-317">すべての出力ファイルを *lib* フォルダーではなく *tools* フォルダーにコピーするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-317">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="4b679-318">*.csproj* ファイルに `PackageType` を設定することで指定される `DotNetCliTool` とは異なります。</span><span class="sxs-lookup"><span data-stu-id="4b679-318">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="4b679-319">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="4b679-319">RepositoryUrl</span></span>

<span data-ttu-id="4b679-320">パッケージのソース コードがある、またはビルド元のリポジトリの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-320">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="4b679-321">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="4b679-321">RepositoryType</span></span>

<span data-ttu-id="4b679-322">リポジトリの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-322">Specifies the type of the repository.</span></span> <span data-ttu-id="4b679-323">既定値は "git" です。</span><span class="sxs-lookup"><span data-stu-id="4b679-323">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="4b679-324">RepositoryBranch</span><span class="sxs-lookup"><span data-stu-id="4b679-324">RepositoryBranch</span></span>
<span data-ttu-id="4b679-325">リポジトリ内のソース ブランチの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-325">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="4b679-326">プロジェクトが NuGet パッケージにパッケージ化されると、パッケージ メタデータに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-326">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="4b679-327">RepositoryCommit</span><span class="sxs-lookup"><span data-stu-id="4b679-327">RepositoryCommit</span></span>
<span data-ttu-id="4b679-328">任意のリポジトリ コミットまたは変更セット。パッケージがどのソースに対してビルドされたかを示します。</span><span class="sxs-lookup"><span data-stu-id="4b679-328">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="4b679-329">このプロパティを含めるには、`RepositoryUrl` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b679-329">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="4b679-330">プロジェクトが NuGet パッケージにパッケージ化されると、このコミットまたは変更セットがパッケージ メタデータに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-330">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="4b679-331">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="4b679-331">NoPackageAnalysis</span></span>

<span data-ttu-id="4b679-332">パッケージのビルド後に、パックでパッケージの分析を実行しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-332">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="4b679-333">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="4b679-333">MinClientVersion</span></span>

<span data-ttu-id="4b679-334">nuget.exe および Visual Studio パッケージ マネージャーで強制する、このパッケージをインストールできる NuGet クライアントの最小バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-334">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="4b679-335">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="4b679-335">IncludeBuildOutput</span></span>

<span data-ttu-id="4b679-336">このブール値は、ビルド出力アセンブリを *.nupkg* ファイルにパッケージ化するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-336">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="4b679-337">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="4b679-337">IncludeContentInPack</span></span>

<span data-ttu-id="4b679-338">このブール値は、種類が `Content` の項目を結果のパッケージに自動的に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-338">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="4b679-339">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="4b679-339">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="4b679-340">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="4b679-340">BuildOutputTargetFolder</span></span>

<span data-ttu-id="4b679-341">出力アセンブリを配置するフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-341">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="4b679-342">出力アセンブリ (および他の出力ファイル) は、各フレームワーク フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="4b679-342">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="4b679-343">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="4b679-343">ContentTargetFolders</span></span>

<span data-ttu-id="4b679-344">このプロパティには、`PackagePath` が指定されていない場合に、すべてのコンテンツ ファイルを配置する既定の場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b679-344">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="4b679-345">既定値は "content;contentFiles" です。</span><span class="sxs-lookup"><span data-stu-id="4b679-345">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="4b679-346">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="4b679-346">NuspecFile</span></span>

<span data-ttu-id="4b679-347">パックに使用する *.nuspec* ファイルの相対パスまたは絶対パス。</span><span class="sxs-lookup"><span data-stu-id="4b679-347">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="4b679-348">*.nuspec* ファイルを指定すると、情報のパッケージに**のみ**使用され、プロジェクト内の情報は使用されません。</span><span class="sxs-lookup"><span data-stu-id="4b679-348">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="4b679-349">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="4b679-349">NuspecBasePath</span></span>

<span data-ttu-id="4b679-350">*.nuspec* ファイルのベース パス。</span><span class="sxs-lookup"><span data-stu-id="4b679-350">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="4b679-351">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="4b679-351">NuspecProperties</span></span>

<span data-ttu-id="4b679-352">キー=値ペアのセミコロン区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="4b679-352">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="4b679-353">AssemblyInfo プロパティ</span><span class="sxs-lookup"><span data-stu-id="4b679-353">AssemblyInfo properties</span></span>

<span data-ttu-id="4b679-354">通常、*AssemblyInfo* ファイル内に存在していた[アセンブリ属性](../../standard/assembly/set-attributes.md)は、プロパティから自動的に生成されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4b679-354">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="4b679-355">属性ごとのプロパティ</span><span class="sxs-lookup"><span data-stu-id="4b679-355">Properties per attribute</span></span>

<span data-ttu-id="4b679-356">次の表に示すように、各属性にはその内容を制御するプロパティと、その生成を無効にするプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="4b679-356">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="4b679-357">属性</span><span class="sxs-lookup"><span data-stu-id="4b679-357">Attribute</span></span>                                                      | <span data-ttu-id="4b679-358">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4b679-358">Property</span></span>               | <span data-ttu-id="4b679-359">無効にするプロパティ</span><span class="sxs-lookup"><span data-stu-id="4b679-359">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="4b679-360">メモ:</span><span class="sxs-lookup"><span data-stu-id="4b679-360">Notes:</span></span>

- <span data-ttu-id="4b679-361">`AssemblyVersion` と `FileVersion` の既定値は、サフィックスなしで `$(Version)` の値を受け取ることです。</span><span class="sxs-lookup"><span data-stu-id="4b679-361">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="4b679-362">たとえば、`$(Version)` が `1.2.3-beta.4` の場合、値は `1.2.3` です。</span><span class="sxs-lookup"><span data-stu-id="4b679-362">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="4b679-363">`InformationalVersion` の既定値は、`$(Version)` の値です。</span><span class="sxs-lookup"><span data-stu-id="4b679-363">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="4b679-364">プロパティが存在する場合、`InformationalVersion` の末尾には `$(SourceRevisionId)` が付加されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-364">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="4b679-365">`IncludeSourceRevisionInInformationalVersion` を使用して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4b679-365">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="4b679-366">NuGet メタデータには、`Copyright` および `Description` プロパティも使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b679-366">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="4b679-367">`Configuration` はすべてのビルド プロセスで共有され、設定には `dotnet` コマンドの`--configuration` パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b679-367">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="4b679-368">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="4b679-368">GenerateAssemblyInfo</span></span>

<span data-ttu-id="4b679-369">すべての AssemblyInfo 生成を有効または無効にするブール値。</span><span class="sxs-lookup"><span data-stu-id="4b679-369">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="4b679-370">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="4b679-370">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="4b679-371">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="4b679-371">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="4b679-372">生成されたアセンブリ情報ファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="4b679-372">The path of the generated assembly info file.</span></span> <span data-ttu-id="4b679-373">既定値は `$(IntermediateOutputPath)` (obj) ディレクトリ内のファイルです。</span><span class="sxs-lookup"><span data-stu-id="4b679-373">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
