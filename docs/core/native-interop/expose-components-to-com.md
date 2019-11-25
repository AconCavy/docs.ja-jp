---
title: COM への .NET Core コンポーネントの公開
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 8d9b8eb274777a0ed019a207c6e8610cc73ec390
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973310"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="e70b0-102">COM への .NET Core コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="e70b0-102">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="e70b0-103">.NET Core では、.NET Framework と比較し、.NET オブジェクトを COM に公開する工程が大幅に簡素化されています。</span><span class="sxs-lookup"><span data-stu-id="e70b0-103">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="e70b0-104">次の手順では、クラスを COM に公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-104">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="e70b0-105">このチュートリアルでは、次の方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="e70b0-106">.NET Core から COM にクラスを公開します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-106">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="e70b0-107">使用する .NET Core ライブラリをビルドする一環として、COM サーバーを生成します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-107">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="e70b0-108">レジストリを使用しない COM 用の side-by-side サーバー マニフェストを自動生成します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-108">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e70b0-109">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e70b0-109">Prerequisites</span></span>

- <span data-ttu-id="e70b0-110">[NET Core 3.0 SDK](https://dotnet.microsoft.com/download) 以降のバージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="e70b0-110">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="e70b0-111">ライブラリを作成する</span><span class="sxs-lookup"><span data-stu-id="e70b0-111">Create the library</span></span>

<span data-ttu-id="e70b0-112">最初の手順では、ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-112">The first step is to create the library.</span></span>

1. <span data-ttu-id="e70b0-113">新しいフォルダーを作成し、そのフォルダーで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-113">Create a new folder, and in that folder run the following command:</span></span>
    
    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="e70b0-114">`Class1.cs`を開きます。</span><span class="sxs-lookup"><span data-stu-id="e70b0-114">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="e70b0-115">ファイルの先頭に、`using System.Runtime.InteropServices;` を追加します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-115">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="e70b0-116">`IServer` という名前のインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-116">Create an interface named `IServer`.</span></span> <span data-ttu-id="e70b0-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-117">For example:</span></span>

   [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]

5. <span data-ttu-id="e70b0-118">このインターフェイスに、実装する COM インターフェイス用のインターフェイス GUID を使用して、`[Guid("<IID>")]` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-118">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="e70b0-119">たとえば、`[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]` のようにします。</span><span class="sxs-lookup"><span data-stu-id="e70b0-119">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="e70b0-120">この GUID は、COM 用のこのインターフェイスの唯一の識別子であるため、一意である必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e70b0-120">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="e70b0-121">Visual Studio で GUID を作成するには、[ツール] > [GUID の作成] の順に移動して GUI の作成ツールを開きます。</span><span class="sxs-lookup"><span data-stu-id="e70b0-121">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="e70b0-122">インターフェイスに `[InterfaceType]` 属性を追加し、お使いのインターフェイスで実装すべき基本 COM インターフェイスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-122">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="e70b0-123">`IServer` を実装する、`Server` という名前のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-123">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="e70b0-124">クラスに、実装する COM クラス用のクラス識別子 GUID を使用して、`[Guid("<CLSID>")]` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-124">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="e70b0-125">たとえば、`[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]` のようにします。</span><span class="sxs-lookup"><span data-stu-id="e70b0-125">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="e70b0-126">インターフェイス GUID でこの GUID は、COM ではこのインターフェイスの唯一の識別子であるため、一意である必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e70b0-126">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="e70b0-127">インターフェイスとクラスの両方に `[ComVisible(true)]` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-127">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e70b0-128">.NET Framework とは異なり、.NET Core では COM を使用してアクティブ化したいすべてのクラスの CLSID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e70b0-128">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="e70b0-129">COM ホストを生成する</span><span class="sxs-lookup"><span data-stu-id="e70b0-129">Generate the COM host</span></span>

1. <span data-ttu-id="e70b0-130">`.csproj` プロジェクト ファイルを開き、`<PropertyGroup></PropertyGroup>` タグの内側に `<EnableComHosting>true</EnableComHosting>` を追加します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-130">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="e70b0-131">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="e70b0-131">Build the project.</span></span>

<span data-ttu-id="e70b0-132">結果として、`ProjectName.dll`、`ProjectName.runtimeconfig.json`、`ProjectName.deps.json`、および`ProjectName.comhost.dll` ファイルが出力されます。</span><span class="sxs-lookup"><span data-stu-id="e70b0-132">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="e70b0-133">COM 用の COM ホストを登録する</span><span class="sxs-lookup"><span data-stu-id="e70b0-133">Register the COM host for COM</span></span>

<span data-ttu-id="e70b0-134">管理者特権でのコマンド プロンプトを開き、`regsvr32 ProjectName.comhost.dll` を実行します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-134">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="e70b0-135">これにより、公開されているすべての .NET オブジェクトが COM に登録されます。</span><span class="sxs-lookup"><span data-stu-id="e70b0-135">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="e70b0-136">Regfree COM を有効にする</span><span class="sxs-lookup"><span data-stu-id="e70b0-136">Enabling RegFree COM</span></span>

1. <span data-ttu-id="e70b0-137">`.csproj` プロジェクト ファイルを開き、`<PropertyGroup></PropertyGroup>` タグの内側に `<EnableRegFreeCom>true</EnableRegFreeCom>` を追加します。</span><span class="sxs-lookup"><span data-stu-id="e70b0-137">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="e70b0-138">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="e70b0-138">Build the project.</span></span>

<span data-ttu-id="e70b0-139">これで結果として、`ProjectName.X.manifest` ファイルも出力されます。</span><span class="sxs-lookup"><span data-stu-id="e70b0-139">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="e70b0-140">このファイルが、Registry-Free COM で使用される side-by-side マニフェストです。</span><span class="sxs-lookup"><span data-stu-id="e70b0-140">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="e70b0-141">サンプル</span><span class="sxs-lookup"><span data-stu-id="e70b0-141">Sample</span></span>

<span data-ttu-id="e70b0-142">GitHub の dotnet/samples リポジトリには、完全に機能する [COM サーバーのサンプル](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)があります。</span><span class="sxs-lookup"><span data-stu-id="e70b0-142">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="e70b0-143">補足メモ</span><span class="sxs-lookup"><span data-stu-id="e70b0-143">Additional notes</span></span>

<span data-ttu-id="e70b0-144">.NET Core では、.NET Framework とは異なり、.NET Core アセンブリからの COM タイプ ライブラリ (TLB) の生成はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e70b0-144">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="e70b0-145">このガイダンスは、COM インターフェイスのネイティブ宣言のために、IDL ファイルまたは C/C++ ヘッダーを手動で記述する方法について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="e70b0-145">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="e70b0-146">また、.NET Framework と .NET Core の両方を同じプロセスに読み込むと、診断が制限されます。</span><span class="sxs-lookup"><span data-stu-id="e70b0-146">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="e70b0-147">主にマネージド コンポーネントのデバッグが制限されます。これは、.NET Framework と .NET Core の両方を同時にデバッグすることはできないためです。</span><span class="sxs-lookup"><span data-stu-id="e70b0-147">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="e70b0-148">また、2 つのランタイム インスタンスはマネージド アセンブリを共有しません。</span><span class="sxs-lookup"><span data-stu-id="e70b0-148">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="e70b0-149">つまり、2 つのランタイム間で実際の .NET 型を共有することはできません。代わりに、すべての対話を、公開されている COM インターフェイス コントラクトに制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e70b0-149">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
