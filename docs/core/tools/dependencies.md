---
title: .NET Core ツールでの依存関係の管理
description: .NET Core ツールで依存関係を管理する方法について説明します。
ms.date: 03/06/2017
ms.openlocfilehash: 9c088829ce3d5197198b7ff22a1331b8baba41d7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714208"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="1f1ce-103">.NET Core SDK 1.0 での依存関係の管理</span><span class="sxs-lookup"><span data-stu-id="1f1ce-103">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="1f1ce-104">.NET Core プロジェクトでの project.json から csproj と MSBuild への移行では、多額の投資も行われ、その結果、プロジェクト ファイルとアセットが統合され、依存関係を追跡できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="1f1ce-105">.NET Core プロジェクトでの依存関係の追跡は、project.json と似ています。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-105">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="1f1ce-106">NuGet の依存関係を追跡するための独立した JSON または XML ファイルはありません。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="1f1ce-107">この変更により、`<PackageReference>` と呼ばれる別の*参照*の型も csproj 構文に導入されました。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="1f1ce-108">ここでは、新しい参照型について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-108">This document describes the new reference type.</span></span> <span data-ttu-id="1f1ce-109">また、この新しい参照型を使ってプロジェクトにパッケージの依存関係を追加する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-109">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="1f1ce-110">新しい \<PackageReference> 要素</span><span class="sxs-lookup"><span data-stu-id="1f1ce-110">The new \<PackageReference> element</span></span>
<span data-ttu-id="1f1ce-111">`<PackageReference>` の基本的な構造は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="1f1ce-112">MSBuild に詳しい場合は、既に存在する他の参照型と似ていることが分かります。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="1f1ce-113">重要なのは、`Include` ステートメントではプロジェクトに追加するパッケージ ID を指定することです。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-113">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="1f1ce-114">`<Version>` 子要素は取得するバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="1f1ce-115">バージョンは、[NuGet のバージョン ルール](/nuget/create-packages/dependency-versions#version-ranges)に従って指定します。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="1f1ce-116">`csproj` の構文に詳しくない場合は、詳細について、[MSBuild プロジェクトのリファレンス](/visualstudio/msbuild/msbuild-project-file-schema-reference) ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="1f1ce-117">特定のターゲットでのみ使用可能な依存関係を追加するには、次の例のような条件を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="1f1ce-118">これは、ビルドがその特定のターゲットに対して行われる場合にのみ依存関係が有効であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="1f1ce-119">条件の `$(TargetFramework)` は、プロジェクトで設定されている MSBuild プロパティです。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-119">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="1f1ce-120">最も一般的な .NET Core アプリケーションの場合、これを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-120">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="1f1ce-121">プロジェクトへの依存関係の追加</span><span class="sxs-lookup"><span data-stu-id="1f1ce-121">Adding a dependency to your project</span></span>
<span data-ttu-id="1f1ce-122">簡単に依存関係をプロジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="1f1ce-123">ここでは、Json.NET バージョン `9.0.1` をプロジェクトに追加する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="1f1ce-124">もちろん、NuGet の他の依存関係にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-124">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="1f1ce-125">プロジェクト ファイルを開くと、2 つ以上の `<ItemGroup>` ノードがあります。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="1f1ce-126">ノードの 1 つには `<PackageReference>` 要素が既にあります。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="1f1ce-127">このノードに新しい依存関係を追加することも、新しいノードを追加することもできます。結果は同じなので開発者次第です。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-127">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="1f1ce-128">この例では、`dotnet new console` によって削除される既定のテンプレートを使います。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-128">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="1f1ce-129">これは、簡単なコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-129">This is a simple console application.</span></span> <span data-ttu-id="1f1ce-130">プロジェクトを開き、最初に `<PackageReference>` が既に存在する `<ItemGroup>` を探します。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-130">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="1f1ce-131">次に、以下のコードをそれに追加します。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-131">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="1f1ce-132">その後、プロジェクトを保存し、`dotnet restore` コマンドを実行して依存関係をインストールします。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-132">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="1f1ce-133">完全なプロジェクトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-133">The full project looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="1f1ce-134">プロジェクトからの依存関係の削除</span><span class="sxs-lookup"><span data-stu-id="1f1ce-134">Removing a dependency from the project</span></span>
<span data-ttu-id="1f1ce-135">プロジェクト ファイルから依存関係を削除するには、プロジェクト ファイルから `<PackageReference>` を削除するだけです。</span><span class="sxs-lookup"><span data-stu-id="1f1ce-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
