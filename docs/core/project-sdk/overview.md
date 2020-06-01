---
title: .NET Core プロジェクト SDK の概要
titleSuffix: ''
description: .NET Core プロジェクト SDK について説明します。
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 67dede3caabd2967adca22e7563376c761829655
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144240"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="5363a-103">.NET Core プロジェクト SDK</span><span class="sxs-lookup"><span data-stu-id="5363a-103">.NET Core project SDKs</span></span>

<span data-ttu-id="5363a-104">.NET Core プロジェクトは、ソフトウェア開発キット (SDK) に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="5363a-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="5363a-105">各 "*プロジェクト SDK*" は、MSBuild [ターゲット](/visualstudio/msbuild/msbuild-targets)と、コードのコンパイル、パッキング、発行を行う関連する[タスク](/visualstudio/msbuild/msbuild-tasks)のセットです。</span><span class="sxs-lookup"><span data-stu-id="5363a-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="5363a-106">プロジェクト SDK を参照するプロジェクトは、"*SDK スタイルのプロジェクト*" と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="5363a-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="5363a-107">使用可能な SDK</span><span class="sxs-lookup"><span data-stu-id="5363a-107">Available SDKs</span></span>

<span data-ttu-id="5363a-108">.NET Core では、次の SDK を利用できます。</span><span class="sxs-lookup"><span data-stu-id="5363a-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="5363a-109">ID</span><span class="sxs-lookup"><span data-stu-id="5363a-109">ID</span></span> | <span data-ttu-id="5363a-110">説明</span><span class="sxs-lookup"><span data-stu-id="5363a-110">Description</span></span> | <span data-ttu-id="5363a-111">リポジトリ</span><span class="sxs-lookup"><span data-stu-id="5363a-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="5363a-112">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="5363a-112">The .NET Core SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="5363a-113">.NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="5363a-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/aspnet/websdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="5363a-114">.NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="5363a-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="5363a-115">.NET Core Worker Service SDK</span><span class="sxs-lookup"><span data-stu-id="5363a-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="5363a-116">.NET Core WinForms と WPF SDK</span><span class="sxs-lookup"><span data-stu-id="5363a-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="5363a-117">.NET Core SDK は、.NET Core の基本 SDK です。</span><span class="sxs-lookup"><span data-stu-id="5363a-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="5363a-118">他の SDK から .NET Core SDK が参照され、他の SDK に関連付けられているプロジェクトで、すべての .NET Core SDK プロパティが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="5363a-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="5363a-119">たとえば、Web SDK は、.NET Core SDK と Razor SDK の両方に依存しています。</span><span class="sxs-lookup"><span data-stu-id="5363a-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="5363a-120">NuGet を使用して配布できる独自の SDK を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="5363a-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="5363a-121">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="5363a-121">Project files</span></span>

<span data-ttu-id="5363a-122">.NET Core プロジェクトは、[MSBuild](/visualstudio/msbuild/msbuild) 形式に基づいています。</span><span class="sxs-lookup"><span data-stu-id="5363a-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="5363a-123">プロジェクト ファイルは、C# プロジェクトでは *.csproj*、F# プロジェクトでは *.fsproj* のような拡張子が付いていて、XML 形式です。</span><span class="sxs-lookup"><span data-stu-id="5363a-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="5363a-124">MSBuild プロジェクト ファイルのルート要素は、[Project](/visualstudio/msbuild/project-element-msbuild) 要素です。</span><span class="sxs-lookup"><span data-stu-id="5363a-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="5363a-125">`Project` 要素には、使用する SDK (およびバージョン) を指定する省略可能な `Sdk` 属性があります。</span><span class="sxs-lookup"><span data-stu-id="5363a-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="5363a-126">.NET Core ツールを使用してコードをビルドするには、`Sdk` 属性を、「[使用可能な SDK](#available-sdks)」の表にあるいずれかの ID に設定します。</span><span class="sxs-lookup"><span data-stu-id="5363a-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="5363a-127">NuGet から取得した SDK を指定するには、名前の末尾にバージョンを含めるか、*global.json* ファイルに名前とバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="5363a-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="5363a-128">SDK を指定する別の方法として、トップレベルの [SDK](/visualstudio/msbuild/sdk-element-msbuild) 要素を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="5363a-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="5363a-129">これらの方法のいずれかで SDK を参照すると、.NET Core のプロジェクト ファイルが大幅に簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="5363a-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="5363a-130">プロジェクトの評価中に、MSBuild によってプロジェクト ファイルの先頭に `Sdk.props` の暗黙的なインポートと、末尾に `Sdk.targets` の暗黙的なインポートが追加されます。</span><span class="sxs-lookup"><span data-stu-id="5363a-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="5363a-131">Windows コンピューターでは、*Sdk.props* ファイルと *Sdk.targets* ファイルは *%ProgramFiles%\dotnet\sdk\\[バージョン]\Sdks\Microsoft.NET.Sdk\Sdk* フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="5363a-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="5363a-132">プロジェクト ファイルの前処理</span><span class="sxs-lookup"><span data-stu-id="5363a-132">Preprocess the project file</span></span>

<span data-ttu-id="5363a-133">MSBuild では、`dotnet msbuild -preprocess` コマンドを使用して、SDK とそのターゲットが取り込まれた後の完全に展開されたプロジェクトがどのようになるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="5363a-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="5363a-134">[`dotnet msbuild`](../tools/dotnet-msbuild.md) コマンドの [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) スイッチによって、インポートされるファイル、そのソース、ビルドに対するそのコントリビューションが、実際にプロジェクトをビルドすることなく、表示されます。</span><span class="sxs-lookup"><span data-stu-id="5363a-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="5363a-135">プロジェクトにターゲット フレームワークが複数存在する場合は、1 つのフレームワークだけにコマンドの結果を集中させてください。そのためには、そのフレームワークを MSBuild プロパティとして指定します。</span><span class="sxs-lookup"><span data-stu-id="5363a-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="5363a-136">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5363a-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="5363a-137">コンパイルへの既定の組み込み</span><span class="sxs-lookup"><span data-stu-id="5363a-137">Default compilation includes</span></span>

<span data-ttu-id="5363a-138">コンパイル項目、埋め込みリソース、および `None` 項目の既定の組み込みと除外が SDK で定義されています。</span><span class="sxs-lookup"><span data-stu-id="5363a-138">The default includes and excludes for compile items, embedded resources, and `None` items are defined in the SDK.</span></span> <span data-ttu-id="5363a-139">SDK 以外の .NET Framework プロジェクトとは異なり、既定値がほとんどの一般的なユース ケースに対応しているため、これらの項目をプロジェクト ファイルで指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5363a-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="5363a-140">これにより、プロジェクト ファイルのサイズがより小さく、より簡単に理解できるようになり、必要に応じて手作業で編集できます。</span><span class="sxs-lookup"><span data-stu-id="5363a-140">This makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="5363a-141">次の表は、.NET Core SDK に組み込まれる、および除外される要素と [glob](https://en.wikipedia.org/wiki/Glob_(programming)) の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="5363a-141">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="5363a-142">要素</span><span class="sxs-lookup"><span data-stu-id="5363a-142">Element</span></span>           | <span data-ttu-id="5363a-143">含まれる glob</span><span class="sxs-lookup"><span data-stu-id="5363a-143">Include glob</span></span>                              | <span data-ttu-id="5363a-144">除外される glob</span><span class="sxs-lookup"><span data-stu-id="5363a-144">Exclude glob</span></span>                                                  | <span data-ttu-id="5363a-145">glob の削除</span><span class="sxs-lookup"><span data-stu-id="5363a-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="5363a-146">Compile</span><span class="sxs-lookup"><span data-stu-id="5363a-146">Compile</span></span>           | <span data-ttu-id="5363a-147">\*\*/\*.cs (または他の言語拡張機能)</span><span class="sxs-lookup"><span data-stu-id="5363a-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="5363a-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="5363a-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="5363a-149">N/A</span><span class="sxs-lookup"><span data-stu-id="5363a-149">N/A</span></span>                      |
| <span data-ttu-id="5363a-150">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="5363a-150">EmbeddedResource</span></span>  | <span data-ttu-id="5363a-151">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="5363a-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="5363a-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="5363a-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="5363a-153">N/A</span><span class="sxs-lookup"><span data-stu-id="5363a-153">N/A</span></span>                      |
| <span data-ttu-id="5363a-154">None</span><span class="sxs-lookup"><span data-stu-id="5363a-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="5363a-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="5363a-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="5363a-156">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="5363a-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="5363a-157">`./bin` フォルダーと `./obj` フォルダーは、`$(BaseOutputPath)` と `$(BaseIntermediateOutputPath)` の MSBuild プロパティによって表され、既定で glob から除外されます。</span><span class="sxs-lookup"><span data-stu-id="5363a-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="5363a-158">除外は `$(DefaultItemExcludes)` プロパティによって表されます。</span><span class="sxs-lookup"><span data-stu-id="5363a-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

#### <a name="build-errors"></a><span data-ttu-id="5363a-159">ビルド エラー</span><span class="sxs-lookup"><span data-stu-id="5363a-159">Build errors</span></span>

<span data-ttu-id="5363a-160">これらの項目をプロジェクト ファイルに明示的に定義すると、次のような "NETSDK1022" ビルド エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5363a-160">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="5363a-161">重複する 'Compile' 項目が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="5363a-161">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="5363a-162">.NET SDK には、既定でプロジェクト ディレクトリの 'Compile' 項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5363a-162">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="5363a-163">これらの項目をプロジェクト ファイルから削除するか、プロジェクト ファイルに明示的に含める場合は 'EnableDefaultCompileItems' プロパティを 'false' に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="5363a-163">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="5363a-164">重複する 'EmbeddedResource' 項目が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="5363a-164">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="5363a-165">.NET SDK には、既定でプロジェクト ディレクトリの 'EmbeddedResource' 項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5363a-165">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="5363a-166">これらの項目をプロジェクト ファイルから削除するか、プロジェクト ファイルに明示的に含める場合は 'EnableDefaultEmbeddedResourceItems' プロパティを 'false' に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="5363a-166">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="5363a-167">このエラーを解決するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="5363a-167">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="5363a-168">前の表に列挙されている暗黙的な項目と一致する明示的な `Compile`、`EmbeddedResource`、または `None` の項目を削除します。</span><span class="sxs-lookup"><span data-stu-id="5363a-168">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="5363a-169">次のように `EnableDefaultItems` プロパティを `false` に設定して、暗黙的なファイルの組み込みをすべて無効にします。</span><span class="sxs-lookup"><span data-stu-id="5363a-169">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="5363a-170">アプリで発行する一部のファイルを指定する必要がある場合は、そのために既知の MSBuild のしくみ (たとえば `Content` 要素) を引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="5363a-170">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="5363a-171">`EnableDefaultCompileItems`、`EnableDefaultEmbeddedResourceItems`、または `EnableDefaultNoneItems` プロパティを `false` に設定することによって、`Compile`、`EmbeddedResource`、または `None` glob のみを選択的に無効にします。</span><span class="sxs-lookup"><span data-stu-id="5363a-171">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the `EnableDefaultCompileItems`, `EnableDefaultEmbeddedResourceItems`, or `EnableDefaultNoneItems` property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="5363a-172">`Compile` glob のみを無効にすると、Visual Studio のソリューション エクスプローラーに \*.cs 項目がプロジェクトの一部として (`None` 項目として組み込まれて) 引き続き表示されます。</span><span class="sxs-lookup"><span data-stu-id="5363a-172">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="5363a-173">暗黙的な `None` glob を無効にするには、`EnableDefaultNoneItems` も `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="5363a-173">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="customize-the-build"></a><span data-ttu-id="5363a-174">ビルドのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="5363a-174">Customize the build</span></span>

<span data-ttu-id="5363a-175">[ビルドをカスタマイズする](/visualstudio/msbuild/customize-your-build)には、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="5363a-175">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="5363a-176">プロパティを引数として [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) または [dotnet](../tools/index.md) コマンドに渡すことによって、プロパティをオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="5363a-176">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="5363a-177">また、プロパティをプロジェクト ファイルに追加することや、*Directory.Build.props* ファイルに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="5363a-177">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="5363a-178">.NET Core プロジェクトの便利なプロパティの一覧については、「[.NET Core SDK プロジェクトの MSBuild リファレンス](msbuild-props.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5363a-178">For a list of useful properties for .NET Core projects, see [MSBuild reference for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="5363a-179">カスタム ターゲット</span><span class="sxs-lookup"><span data-stu-id="5363a-179">Custom targets</span></span>

<span data-ttu-id="5363a-180">.NET Core プロジェクトでは、プロジェクトで使用するカスタムの MSBuild ターゲットとプロパティをパッケージ化し、そのパッケージをプロジェクトで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5363a-180">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="5363a-181">この種の拡張機能を使用するのは、次の場合です。</span><span class="sxs-lookup"><span data-stu-id="5363a-181">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="5363a-182">ビルド処理を拡張する。</span><span class="sxs-lookup"><span data-stu-id="5363a-182">Extend the build process.</span></span>
- <span data-ttu-id="5363a-183">ビルド プロセスの成果物 (生成されたファイルなど) にアクセスする。</span><span class="sxs-lookup"><span data-stu-id="5363a-183">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="5363a-184">どのような構成でビルドが呼び出されるかを検査する。</span><span class="sxs-lookup"><span data-stu-id="5363a-184">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="5363a-185">カスタムのビルド ターゲットまたはプロパティを追加するには、プロジェクトの *build* フォルダーに `<package_id>.targets` または `<package_id>.props` の形式のファイル (たとえば `Contoso.Utility.UsefulStuff.targets`) を配置します。</span><span class="sxs-lookup"><span data-stu-id="5363a-185">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="5363a-186">次の XML は *.csproj* ファイルからのスニペットです。パッケージ化する対象を [`dotnet pack`](../tools/dotnet-pack.md) コマンドに指示しています。</span><span class="sxs-lookup"><span data-stu-id="5363a-186">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="5363a-187">`<ItemGroup Label="dotnet pack instructions">` 要素で、パッケージ内の *build* フォルダーにターゲット ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="5363a-187">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="5363a-188">`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` 要素で、アセンブリと *.json* ファイルを *build* フォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="5363a-188">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

<span data-ttu-id="5363a-189">プロジェクトでカスタム ターゲットを使用するには、パッケージとそのバージョンを指す `PackageReference` 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="5363a-189">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="5363a-190">ツールとは異なり、カスタム ターゲットのパッケージは、それを使用するプロジェクトの依存関係クロージャに含まれます。</span><span class="sxs-lookup"><span data-stu-id="5363a-190">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="5363a-191">カスタム ターゲットの使用方法を構成できます。</span><span class="sxs-lookup"><span data-stu-id="5363a-191">You can configure how to use the custom target.</span></span> <span data-ttu-id="5363a-192">それは MSBuild ターゲットであるため、指定されたターゲットに依存することや、別のターゲットの後に実行したり、`dotnet msbuild -t:<target-name>` コマンドを使用して手動で呼び出したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="5363a-192">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="5363a-193">ただし、優れたユーザー エクスペリエンスを提供するために、プロジェクトごとのツールとカスタム ターゲットを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="5363a-193">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="5363a-194">このシナリオでは、必要なすべてのパラメーターをプロジェクトごとのツールで受け取り、受け取ったパラメーターを、ターゲットを実行する必要な [`dotnet msbuild`](../tools/dotnet-msbuild.md) の呼び出しに変換します。</span><span class="sxs-lookup"><span data-stu-id="5363a-194">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="5363a-195">このような相乗効果のサンプルは、[`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) プロジェクトの「[MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016)」 (MVP Summit 2016 ハッカソンのサンプル) レポートで参照することができます。</span><span class="sxs-lookup"><span data-stu-id="5363a-195">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="5363a-196">関連項目</span><span class="sxs-lookup"><span data-stu-id="5363a-196">See also</span></span>

- [<span data-ttu-id="5363a-197">.NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="5363a-197">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="5363a-198">MSBuild プロジェクト SDK の使用方法</span><span class="sxs-lookup"><span data-stu-id="5363a-198">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="5363a-199">カスタムの MSBuild ターゲットとプロパティを NuGet でパッケージ化する</span><span class="sxs-lookup"><span data-stu-id="5363a-199">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
