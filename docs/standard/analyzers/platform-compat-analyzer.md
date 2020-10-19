---
title: プラットフォーム互換性アナライザー
description: クロスプラットフォームのアプリとライブラリにおいてプラットフォームの互換性に関する問題を検出するのに役立つ Roslyn アナライザーです。
author: buyaa-n
ms.date: 09/17/2020
ms.openlocfilehash: 44c2c2d9674b13f314a057f847df2d4d474cc2be
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805299"
---
# <a name="platform-compatibility-analyzer"></a><span data-ttu-id="b0009-103">プラットフォーム互換性アナライザー</span><span class="sxs-lookup"><span data-stu-id="b0009-103">Platform compatibility analyzer</span></span>

<span data-ttu-id="b0009-104">"One .NET" という標語をお聞きになったことがあるかもしれません。あらゆる種類のアプリケーションを構築するための、1 つの統一プラットフォームという意味です。</span><span class="sxs-lookup"><span data-stu-id="b0009-104">You've probably heard the motto of "One .NET": a single, unified platform for building any type of application.</span></span> <span data-ttu-id="b0009-105">.NET 5.0 SDK には、ASP.NET Core、Entity Framework Core、WinForms、WPF、Xamarin、ML.NET が含まれています。また、時間の経過と共にさらなるプラットフォームのサポートが追加されます。</span><span class="sxs-lookup"><span data-stu-id="b0009-105">The .NET 5.0 SDK includes ASP.NET Core, Entity Framework Core, WinForms, WPF, Xamarin, and ML.NET, and will add support for more platforms over time.</span></span> <span data-ttu-id="b0009-106">.NET 5.0 では、.NET のさまざまなフレーバーを判断する必要がないエクスペリエンスの提供を目指していますが、基になるオペレーティング システム (OS) を完全に抽象化しようとしているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="b0009-106">.NET 5.0 strives to provide an experience where you don't have to reason about the different flavors of .NET, but doesn't attempt to fully abstract away the underlying operating system (OS).</span></span> <span data-ttu-id="b0009-107">ユーザーは引き続き、P/Invoke、WinRT、または iOS および Android 用の Xamarin バインドなど、プラットフォーム固有の API を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b0009-107">You'll continue to be able to call platform-specific APIs, for example, P/Invokes, WinRT, or the Xamarin bindings for iOS and Android.</span></span>

<span data-ttu-id="b0009-108">ただし、コンポーネント上でプラットフォーム固有の API を使用すると、一部のプラットフォームでそのコードが動作しなくなります。</span><span class="sxs-lookup"><span data-stu-id="b0009-108">But using platform-specific APIs on a component means the code no longer works across all platforms.</span></span> <span data-ttu-id="b0009-109">デザイン時にこれを検出して、開発者が誤ってプラットフォーム固有の API を使用したときに診断を取得できるようにするための方法が必要でした。</span><span class="sxs-lookup"><span data-stu-id="b0009-109">We needed a way to detect this at design time so developers get diagnostics when they inadvertently use platform-specific APIs.</span></span> <span data-ttu-id="b0009-110">この目標を達成するために、.NET 5.0 では[プラットフォーム互換性アナライザー](/visualstudio/code-quality/ca1416)と、開発者がプラットフォーム固有の API を特定して適切な場所で使用できるようにするための、補完的な API が導入されます。</span><span class="sxs-lookup"><span data-stu-id="b0009-110">To achieve this goal, .NET 5.0 introduces the [platform compatibility analyzer](/visualstudio/code-quality/ca1416) and complementary APIs to help developers identify and use platform-specific APIs where appropriate.</span></span>
<span data-ttu-id="b0009-111">新しい API には以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b0009-111">The new APIs include:</span></span>

- <span data-ttu-id="b0009-112">API にプラットフォーム固有という注釈を付けるための <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> と、API に特定の OS でサポートされていないという注釈を付けるための <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>。</span><span class="sxs-lookup"><span data-stu-id="b0009-112"><xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> to annotate APIs as being platform-specific and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> to annotate APIs as being unsupported on a particular OS.</span></span> <span data-ttu-id="b0009-113">これらの属性には必要に応じてバージョン番号を含めることができます。コア .NET ライブラリに含まれている一部のプラットフォーム固有の API には既に適用されています。</span><span class="sxs-lookup"><span data-stu-id="b0009-113">These attributes can optionally include the version number, and have already been applied to some platform-specific APIs in the core .NET libraries.</span></span>
- <span data-ttu-id="b0009-114">プラットフォーム固有の API を安全に呼び出すための、<xref:System.OperatingSystem?displayProperty=nameWithType> クラスの `Is<Platform>()` および `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` 静的メソッド。</span><span class="sxs-lookup"><span data-stu-id="b0009-114">`Is<Platform>()` and `Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` static methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class for safely calling platform-specific APIs.</span></span> <span data-ttu-id="b0009-115">たとえば、<xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> を使用して Windows 固有の API 呼び出しを保護したり、<xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>() を使用してバージョン付きの Windows 固有の API 呼び出しを保護したりできます。</span><span class="sxs-lookup"><span data-stu-id="b0009-115">For example, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> can be used to guard a call to a Windows-specific API, and <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>() can be used to guard a versioned Windows-specific API call.</span></span> <span data-ttu-id="b0009-116">これらのメソッドを使用してプラットフォーム固有の API 参照を保護する方法については、以下の[例](#guard-platform-specific-apis-with-guard-methods)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b0009-116">See these [examples](#guard-platform-specific-apis-with-guard-methods) of how these methods can be used as guards of platform-specific API references.</span></span>

> [!TIP]
> <span data-ttu-id="b0009-117">プラットフォーム互換性アナライザーによって、[.NET API アナライザー](../../standard/analyzers/api-analyzer.md)の[クロスプラットフォームの問題の検出](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues)機能がアップグレードされ、置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="b0009-117">The platform compatibility analyzer upgrades and replaces the [Discovering cross-platform issues](../../standard/analyzers/api-analyzer.md#discover-cross-platform-issues) feature of the [.NET API analyzer](../../standard/analyzers/api-analyzer.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0009-118">[前提条件]</span><span class="sxs-lookup"><span data-stu-id="b0009-118">Prerequisites</span></span>

<span data-ttu-id="b0009-119">プラットフォーム互換性アナライザーは、Roslyn コード品質アナライザーの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="b0009-119">The platform compatibility analyzer is one of the Roslyn code quality analyzers.</span></span> <span data-ttu-id="b0009-120">.NET 5.0 以降、これらのアナライザーは [.NET SDK に含まれる](../../fundamentals/code-analysis/overview.md)ようになりました。</span><span class="sxs-lookup"><span data-stu-id="b0009-120">Starting in .NET 5.0, these analyzers are [included with the .NET SDK](../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="b0009-121">プラットフォーム互換性アナライザーは、`net5.0` 以降のバージョンをターゲットとするプロジェクトに対してのみ既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="b0009-121">The platform compatibility analyzer is enabled by default only for projects that target `net5.0` or a later version.</span></span> <span data-ttu-id="b0009-122">ただし、他のフレームワークをターゲットとするプロジェクトに対しても[有効にする](/visualstudio/code-quality/ca1416.md#configurability)ことができます。</span><span class="sxs-lookup"><span data-stu-id="b0009-122">However, you can [enable](/visualstudio/code-quality/ca1416.md#configurability) it for projects that target other frameworks.</span></span>

## <a name="how-the-analyzer-determines-platform-dependency"></a><span data-ttu-id="b0009-123">アナライザーによってプラットフォームの依存関係が判断されるしくみ</span><span class="sxs-lookup"><span data-stu-id="b0009-123">How the analyzer determines platform dependency</span></span>

- <span data-ttu-id="b0009-124">**属性なしの API** は**全 OS プラットフォーム**で動作すると見なされます。</span><span class="sxs-lookup"><span data-stu-id="b0009-124">An **unattributed API** is considered to work on **all OS platforms**.</span></span>
- <span data-ttu-id="b0009-125">`[SupportedOSPlatform("platform")]` でマークされた API は、指定された OS `platform` にのみ移植可能であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="b0009-125">An API marked with `[SupportedOSPlatform("platform")]` is considered only portable to the specified OS `platform`.</span></span>
  - <span data-ttu-id="b0009-126">この属性を複数回適用して、**複数プラットフォームのサポート** (`[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]`) を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="b0009-126">The attribute can be applied multiple times to indicate **multiple platform support** (`[SupportedOSPlatform("windows"), SupportedOSPlatform("Android6.0")]`).</span></span>
  - <span data-ttu-id="b0009-127">適切な**プラットフォーム コンテキスト**を使用せずにプラットフォーム固有の API が参照されている場合は、アナライザーによって**警告**が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b0009-127">The analyzer will produce a **warning** if platform-specific APIs are referenced without a proper **platform context**:</span></span>
    - <span data-ttu-id="b0009-128">プロジェクトがサポート対象プラットフォームをターゲットとしていない場合 (たとえば、Windows 固有の API 呼び出しでプロジェクトが `<TargetFramework>net5.0-ios14.0</TargetFramework>` をターゲットとしている場合)、**警告が表示されます**。</span><span class="sxs-lookup"><span data-stu-id="b0009-128">**Warns** if the project doesn't target the supported platform (for example, a Windows-specific API call and the project targets `<TargetFramework>net5.0-ios14.0</TargetFramework>`).</span></span>
    - <span data-ttu-id="b0009-129">プロジェクトに複数のターゲットがある場合 (`<TargetFramework>net5.0</TargetFramework>`)、**警告が表示されます**。</span><span class="sxs-lookup"><span data-stu-id="b0009-129">**Warns** if the project is multi-targeted (`<TargetFramework>net5.0</TargetFramework>`).</span></span>
    - <span data-ttu-id="b0009-130">プラットフォーム固有の API が、**指定されたプラットフォーム**のいずれかをターゲットとしているプロジェクト内で参照される場合、**警告は表示されません** (たとえば、Windows 固有の API 呼び出しでプロジェクトが `<TargetFramework>net5.0-windows</TargetFramework>` をターゲットとしている場合)。</span><span class="sxs-lookup"><span data-stu-id="b0009-130">**Doesn't warn** if the platform-specific API is referenced within a project that targets any of the **specified platforms** (for example, for a Windows-specific API call and the project targets `<TargetFramework>net5.0-windows</TargetFramework>`).</span></span>
    - <span data-ttu-id="b0009-131">プラットフォーム固有の API 呼び出しが、対応するプラットフォーム チェック メソッド (例: `if(OperatingSystem.IsWindows())`) によって保護されている場合、**警告は表示されません**。</span><span class="sxs-lookup"><span data-stu-id="b0009-131">**Doesn't warn** if the platform-specific API call is guarded by corresponding platform-check methods (for example, `if(OperatingSystem.IsWindows())`).</span></span>
    - <span data-ttu-id="b0009-132">プラットフォーム固有の API が、同じプラットフォーム固有のコンテキストから参照されている場合 (**呼び出しサイトにも属性 `[SupportedOSPlatform("platform")` が設定されている場合**)、**警告は表示されません**。</span><span class="sxs-lookup"><span data-stu-id="b0009-132">**Doesn't warn** if the platform-specific API is referenced from the same platform-specific context (**call site also attributed** with `[SupportedOSPlatform("platform")`).</span></span>
- <span data-ttu-id="b0009-133">`[UnsupportedOSPlatform("platform")]` でマークされた API は、指定した OS `platform` でのみサポートされず、他のすべてのプラットフォームでサポートされると見なされます。</span><span class="sxs-lookup"><span data-stu-id="b0009-133">An API marked with `[UnsupportedOSPlatform("platform")]` is considered unsupported only on the specified OS `platform` but supported for all other platforms.</span></span>
  - <span data-ttu-id="b0009-134">この属性は、異なるプラットフォームで複数回適用できます (例: `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]`)。</span><span class="sxs-lookup"><span data-stu-id="b0009-134">The attribute can be applied multiple times with different platforms, for example, `[UnsupportedOSPlatform("iOS"), UnsupportedOSPlatform("Android6.0")]`.</span></span>
  - <span data-ttu-id="b0009-135">アナライザーによって**警告**が生成されるのは、`platform` が呼び出しサイトに対して有効である場合のみです。</span><span class="sxs-lookup"><span data-stu-id="b0009-135">The analyzer produces a **warning** only if the `platform` is effective for the call site:</span></span>
    - <span data-ttu-id="b0009-136">サポート対象外の属性が設定されているプラットフォームをプロジェクトがターゲットとしている場合、**警告が表示されます** (たとえば、API に属性 `[UnsupportedOSPlatform("windows")]` が設定されていて、呼び出しサイトが `<TargetFramework>net5.0-windows</TargetFramework>` をターゲットとしている場合)。</span><span class="sxs-lookup"><span data-stu-id="b0009-136">**Warns** if the project targets the platform that's attributed as unsupported (for example, if the API is attributed with `[UnsupportedOSPlatform("windows")]` and the call site targets `<TargetFramework>net5.0-windows</TargetFramework>`).</span></span>
    - <span data-ttu-id="b0009-137">プロジェクトに複数のターゲットがあり、`platform` が既定の [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) 項目グループに含まれている場合、または `platform` が手動で `MSBuild` \<SupportedPlatform> 項目グループ内に含まれている場合、**警告が表示されます**。</span><span class="sxs-lookup"><span data-stu-id="b0009-137">**Warns** if the project is multi-targeted and the `platform` is included in the default [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) items group, or the `platform` is manually included within the `MSBuild` \<SupportedPlatform> items group:</span></span>

      ```XML
      <ItemGroup>
          <SupportedPlatform Include="platform" />
      </ItemGroup>
      ```

    - <span data-ttu-id="b0009-138">サポート対象外のプラットフォームをターゲットとしていないアプリをビルドする場合、またはビルドするアプリに複数のターゲットがあり、platform が既定の [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) 項目グループに含まれていない場合、**警告は表示されません**。</span><span class="sxs-lookup"><span data-stu-id="b0009-138">**Doesn't warn** if you're building an app that doesn't target the unsupported platform or is multi-targeted and the platform is not included in the default [MSBuild `<SupportedPlatform>`](https://github.com/dotnet/sdk/blob/master/src/Tasks/Microsoft.NET.Build.Tasks/targets/Microsoft.NET.SupportedPlatforms.props) items group.</span></span>
- <span data-ttu-id="b0009-139">どちらの属性も、プラットフォーム名の一部としてバージョン番号を含めても、含めなくてもインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="b0009-139">Both attributes can be instantiated with or without version numbers as part of the platform name.</span></span>
  - <span data-ttu-id="b0009-140">バージョン番号は `major.minor[.build[.revision]]` の形式です。`major.minor` は必須であり、`build` と `revision` の部分は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="b0009-140">Version numbers are in the format of `major.minor[.build[.revision]]`; `major.minor` is required and the `build` and `revision` parts are optional.</span></span> <span data-ttu-id="b0009-141">たとえば、"Windows7.0" は Windows バージョン 7.0 を示しますが、"Windows" は Windows 0.0 として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="b0009-141">For example, "Windows7.0" indicates Windows version 7.0, but "Windows" is interpreted as Windows 0.0.</span></span>

<span data-ttu-id="b0009-142">詳細については、[属性の動作方法とそれらによって発生する診断の例](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce)に関するセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b0009-142">For more information, see [examples of how the attributes work and what diagnostics they cause](#examples-of-how-the-attributes-work-and-what-diagnostics-they-produce).</span></span>

### <a name="advanced-scenarios-for-combining-attributes"></a><span data-ttu-id="b0009-143">属性を組み合わせる高度なシナリオ</span><span class="sxs-lookup"><span data-stu-id="b0009-143">Advanced scenarios for combining attributes</span></span>

- <span data-ttu-id="b0009-144">`[SupportedOSPlatform]` 属性と `[UnsupportedOSPlatform]` 属性の組み合わせが存在する場合、すべての属性は OS プラットフォーム識別子によってグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="b0009-144">If a combination of `[SupportedOSPlatform]` and `[UnsupportedOSPlatform]` attributes are present, all attributes are grouped by OS platform identifier:</span></span>
  - <span data-ttu-id="b0009-145">**サポート対象のみのリスト**。</span><span class="sxs-lookup"><span data-stu-id="b0009-145">**Supported only list**.</span></span> <span data-ttu-id="b0009-146">各 OS プラットフォームの最小バージョンが `[SupportedOSPlatform]` 属性である場合、その API はリストに含まれているプラットフォームでのみサポートされ、他のすべてのプラットフォームではサポートされないと見なされます。</span><span class="sxs-lookup"><span data-stu-id="b0009-146">If the lowest version for each OS platform is a `[SupportedOSPlatform]` attribute, the API is considered to only be supported by the listed platforms and unsupported by all other platforms.</span></span> <span data-ttu-id="b0009-147">各プラットフォームの省略可能な `[UnsupportedOSPlatform]` 属性には、サポートされる最小バージョンより上位のバージョンのみを設定できます。これは、指定されたバージョン以降で API が削除されることを示します。</span><span class="sxs-lookup"><span data-stu-id="b0009-147">The optional `[UnsupportedOSPlatform]` attributes for each platform can only have higher version of the minimum supported version, which denotes that the API is removed starting from the specified version.</span></span>

    ```csharp
    // The API only supported on Windows 8.0 and later, not supported for all other.
    // The API is removed/unsupported from version 10.0.19041.0.
    [SupportedOSPlatform("windows8.0")]
    [UnsupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows80SupportFromCertainVersion();
    ```

  - <span data-ttu-id="b0009-148">**サポート対象外のみのリスト**。</span><span class="sxs-lookup"><span data-stu-id="b0009-148">**Unsupported only list**.</span></span> <span data-ttu-id="b0009-149">各 OS プラットフォームの最小バージョンが `[UnsupportedOSPlatform]` 属性である場合、その API はリストに含まれているプラットフォームでのみサポートされず、他のすべてのプラットフォームではサポートされると見なされます。</span><span class="sxs-lookup"><span data-stu-id="b0009-149">If the lowest version for each OS platform is an `[UnsupportedOSPlatform]` attribute, then the API is considered to only be unsupported by the listed platforms and supported by all other platforms.</span></span> <span data-ttu-id="b0009-150">リストには、同じプラットフォームのより上位のバージョンの `[SupportedOSPlatform]` 属性を含めることができます。これは、そのバージョン以降で API がサポートされることを示します。</span><span class="sxs-lookup"><span data-stu-id="b0009-150">The list could have `[SupportedOSPlatform]` attribute with the same platform but a higher version, which denotes that the API is supported starting from that version.</span></span>

    ```csharp
    // The API was unsupported on Windows until version 10.0.19041.0.
    // The API is considered supported everywhere else without constraints.
    [UnsupportedOSPlatform("windows")]
    [SupportedOSPlatform("windows10.0.19041.0")]
    public void ApiSupportedFromWindows8UnsupportFromWindows10();
    ```

  - <span data-ttu-id="b0009-151">**不整合なリスト**。</span><span class="sxs-lookup"><span data-stu-id="b0009-151">**Inconsistent list**.</span></span> <span data-ttu-id="b0009-152">あるプラットフォームの最小バージョンが `[SupportedOSPlatform]` であり、それが別のプラットフォームでは `[UnsupportedOSPlatform]` であった場合は、不整合と見なされます。これはアナライザーでサポートされません。</span><span class="sxs-lookup"><span data-stu-id="b0009-152">If the lowest version for some platforms is `[SupportedOSPlatform]` while it is `[UnsupportedOSPlatform]` for other platforms, it's considered to be inconsistent, which is not supported for the analyzer.</span></span>
  - <span data-ttu-id="b0009-153">`[SupportedOSPlatform]` 属性と `[UnsupportedOSPlatform]` 属性の最小バージョンが等しい場合、アナライザーではそのプラットフォームが**サポート対象のみのリスト**に含まれていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="b0009-153">If the lowest versions of `[SupportedOSPlatform]` and `[UnsupportedOSPlatform]` attributes are equal, the analyzer considers the platform as part of the **Supported only list**.</span></span>
- <span data-ttu-id="b0009-154">プラットフォーム属性は、型、メンバー (メソッド、フィールド、プロパティ、イベント)、およびプラットフォーム名やバージョンが異なるアセンブリに適用できます。</span><span class="sxs-lookup"><span data-stu-id="b0009-154">Platform attributes can be applied to types, members (methods, fields, properties, and events) and assemblies with different platform names or versions.</span></span>
  - <span data-ttu-id="b0009-155">最上位レベルの `target` に適用される属性は、そのすべてのメンバーと型に影響します。</span><span class="sxs-lookup"><span data-stu-id="b0009-155">Attributes applied at the top level `target` affect all of its members and types.</span></span>
  - <span data-ttu-id="b0009-156">子レベルの属性が適用されるのは、それが "子注釈によってプラットフォームのサポートを絞り込むことはできるが、拡大することはできない" という規則に準拠している場合のみです。</span><span class="sxs-lookup"><span data-stu-id="b0009-156">Child-level attributes only apply if they adhere to the rule "child annotations can narrow the platforms support, but they cannot widen it".</span></span>
    - <span data-ttu-id="b0009-157">親が**サポート対象のみ**のリストを持っている場合、子のメンバー属性で新しいプラットフォームのサポートを追加することはできません。親のサポートが拡大されるためです。</span><span class="sxs-lookup"><span data-stu-id="b0009-157">When parent has **Supported only** list, then child member attributes cannot add a new platform support, as that would be extending parent support.</span></span> <span data-ttu-id="b0009-158">新しいプラットフォームのサポートは、親自体にのみ追加できます。</span><span class="sxs-lookup"><span data-stu-id="b0009-158">Support for a new platform can only be added to the parent itself.</span></span> <span data-ttu-id="b0009-159">ただし、子が同じプラットフォームのそれ以降のバージョンに対して `Supported` 属性を持つことはできます。それによりサポートが絞り込まれるためです。</span><span class="sxs-lookup"><span data-stu-id="b0009-159">But the child can have the `Supported` attribute for the same platform with later versions as that narrows the support.</span></span> <span data-ttu-id="b0009-160">また、子が同じプラットフォームで `Unsupported` 属性を持つこともできます。親のサポートも絞り込まれるためです。</span><span class="sxs-lookup"><span data-stu-id="b0009-160">Also, the child can have the `Unsupported` attribute with the same platform as that also narrows parent support.</span></span>
    - <span data-ttu-id="b0009-161">親が**サポート対象外のみ**のリストを持っている場合、親のサポートを絞り込むために、子のメンバー属性で新しいプラットフォームのサポートを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="b0009-161">When parent has **Unsupported only** list, then child member attributes can add support for a new platform, as that narrows parent support.</span></span> <span data-ttu-id="b0009-162">しかし、親と同じプラットフォームの `Supported` 属性を持つことはできません。親のサポートが拡張されるからです。</span><span class="sxs-lookup"><span data-stu-id="b0009-162">But it cannot have the `Supported` attribute for the same platform as the parent, because that extends parent support.</span></span> <span data-ttu-id="b0009-163">同じプラットフォームのサポートは、元の `Unsupported` 属性が適用された親に対してのみ追加できます。</span><span class="sxs-lookup"><span data-stu-id="b0009-163">Support for the same platform can only be added to the parent where the original `Unsupported` attribute was applied.</span></span>
  - <span data-ttu-id="b0009-164">同じ `platform` 名の API に対して `[SupportedOSPlatform("platformVersion")]` が 2 回以上適用されている場合、最小バージョンのものだけがアナライザーによって考慮されます。</span><span class="sxs-lookup"><span data-stu-id="b0009-164">If `[SupportedOSPlatform("platformVersion")]` is applied more than once for an API with the same `platform` name, the analyzer only considers the one with the minimum version.</span></span>
  - <span data-ttu-id="b0009-165">同じ `platform` 名の API に対して `[UnsupportedOSPlatform("platformVersion")]` が 3 回以上適用されている場合、最も古いバージョンの 2 つだけがアナライザーによって考慮されます。</span><span class="sxs-lookup"><span data-stu-id="b0009-165">If `[UnsupportedOSPlatform("platformVersion")]` is applied more than twice for an API with the same `platform` name, the analyzer only considers the two with the earliest versions.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b0009-166">最初はサポートされていたが後のバージョンではサポートされていない (削除された) API は、さらに後のバージョンで再びサポートされることはないと想定されます。</span><span class="sxs-lookup"><span data-stu-id="b0009-166">An API that was supported initially but unsupported (removed) in a later version is not expected to get resupported in an even later version.</span></span>

### <a name="examples-of-how-the-attributes-work-and-what-diagnostics-they-produce"></a><span data-ttu-id="b0009-167">属性の動作方法とそれらによって生成される診断の例</span><span class="sxs-lookup"><span data-stu-id="b0009-167">Examples of how the attributes work and what diagnostics they produce</span></span>

  ```csharp
  // An API supported only on Windows.
  [SupportedOSPlatform("Windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  public void Caller()
  {
      WindowsOnlyApi(); // warns: 'WindowsOnlyApi' is supported on 'windows'

      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Windows'
      // warns: 'SupportedOnWindowsAndLinuxOnly' is supported on 'Linux'
      SupportedOnWindowsAndLinuxOnly();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 8.0 and later
      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // for same platform analyzer only warn for the latest version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on android but supported on all other.
  [UnsupportedOSPlatform("android")]
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  public void Caller2()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'android'

      // warns:'StartedWindowsSupportFromVersion8' is unsupported on 'windows'
      // warns:'StartedWindowsSupportFromVersion8' is supported on 'windows' 8.0 and later
      StartedWindowsSupportFromVersion8();

      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is unsupported on 'windows'
      // warns:'StartedWindowsSupportFrom8UnsupportedFrom10' is supported on 'windows' 8.0 and later
      // even there were 3 diagnostics found analyzer warn only for the first 2.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

## <a name="handle-reported-warnings"></a><span data-ttu-id="b0009-168">報告された警告の処理</span><span class="sxs-lookup"><span data-stu-id="b0009-168">Handle reported warnings</span></span>

<span data-ttu-id="b0009-169">これらの診断に対処するための推奨される方法は、適切なプラットフォーム上で実行する場合にのみプラットフォーム固有の API を呼び出すようにすることです。</span><span class="sxs-lookup"><span data-stu-id="b0009-169">The recommended way to deal with these diagnostics is to make sure you only call platform-specific APIs when running on an appropriate platform.</span></span> <span data-ttu-id="b0009-170">警告に対処するために使用できるオプションを以下に示します。ご自身の状況に最も適したものを選択してください。</span><span class="sxs-lookup"><span data-stu-id="b0009-170">Following are the options you can use to address the warnings; choose whichever is most appropriate for your situation:</span></span>

- <span data-ttu-id="b0009-171">**呼び出しを保護する**。</span><span class="sxs-lookup"><span data-stu-id="b0009-171">**Guard the call**.</span></span> <span data-ttu-id="b0009-172">これは、実行時にコードを条件付きで呼び出すことによって実現できます。</span><span class="sxs-lookup"><span data-stu-id="b0009-172">You can achieve this by conditionally calling the code at run time.</span></span> <span data-ttu-id="b0009-173">プラットフォーム チェック メソッド (`OperatingSystem.Is<Platform>()`、`OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)` など) のいずれかを使用して、目的の `Platform` で実行しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0009-173">Check whether you're running on a desired `Platform` by using one of platform-check methods, for example, `OperatingSystem.Is<Platform>()` or `OperatingSystem.Is<Platform>VersionAtLeast(int major, int minor = 0, int build = 0, int revision = 0)`.</span></span>

- <span data-ttu-id="b0009-174">**呼び出しサイトをプラットフォーム固有としてマークする**。</span><span class="sxs-lookup"><span data-stu-id="b0009-174">**Mark the call site as platform-specific**.</span></span> <span data-ttu-id="b0009-175">独自の API をプラットフォーム固有としてマークすることもできます。これにより、実質的には要求を呼び出し元に転送するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="b0009-175">You can also choose to mark your own APIs as being platform-specific, thus effectively just forwarding the requirements to your callers.</span></span> <span data-ttu-id="b0009-176">含まれているメソッドや型、またはアセンブリ全体を、参照されているプラットフォーム依存の呼び出しと同じ属性でマークします。</span><span class="sxs-lookup"><span data-stu-id="b0009-176">Mark the containing method or type or the entire assembly with the same attributes as the referenced platform-dependent call.</span></span> <span data-ttu-id="b0009-177">[例](#mark-call-site-as-platform-specific)。</span><span class="sxs-lookup"><span data-stu-id="b0009-177">[Examples](#mark-call-site-as-platform-specific).</span></span>

- <span data-ttu-id="b0009-178">**プラットフォーム チェックを使用して呼び出しサイトをアサートする**。</span><span class="sxs-lookup"><span data-stu-id="b0009-178">**Assert the call site with platform check**.</span></span> <span data-ttu-id="b0009-179">`if` ステートメントを追加して実行時のオーバーヘッドを増やしたくない場合は、<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="b0009-179">If you don't want the overhead of an additional `if` statement at run time, use <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b0009-180">[例](#assert-the-call-site-with-platform-check)。</span><span class="sxs-lookup"><span data-stu-id="b0009-180">[Example](#assert-the-call-site-with-platform-check).</span></span>

- <span data-ttu-id="b0009-181">**コードを削除する**。</span><span class="sxs-lookup"><span data-stu-id="b0009-181">**Delete the code**.</span></span> <span data-ttu-id="b0009-182">通常は望ましい方法ではありません。Windows ユーザーがコードを使用する場合に忠実性が失われることを意味するためです。</span><span class="sxs-lookup"><span data-stu-id="b0009-182">Generally not what you want because it means you lose fidelity when your code is used by Windows users.</span></span> <span data-ttu-id="b0009-183">クロスプラットフォームの代替手段が存在する場合は、プラットフォーム固有の API よりもそちらを使用した方がよい可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b0009-183">For cases where a cross-platform alternative exists, you're likely better off using that over platform-specific APIs.</span></span>

- <span data-ttu-id="b0009-184">**警告を抑制する**。</span><span class="sxs-lookup"><span data-stu-id="b0009-184">**Suppress the warning**.</span></span> <span data-ttu-id="b0009-185">EditorConfig エントリまたは `#pragma warning disable ca1416` を使用して、単に警告を抑制することもできます。</span><span class="sxs-lookup"><span data-stu-id="b0009-185">You can also simply suppress the warning, either via an EditorConfig entry or `#pragma warning disable ca1416`.</span></span> <span data-ttu-id="b0009-186">ただし、プラットフォーム固有の API を使用する場合、このオプションは最後の手段にするべきです。</span><span class="sxs-lookup"><span data-stu-id="b0009-186">However, this option should be a last resort when using platform-specific APIs.</span></span>

### <a name="guard-platform-specific-apis-with-guard-methods"></a><span data-ttu-id="b0009-187">保護メソッドを使用してプラットフォーム固有の API を保護する</span><span class="sxs-lookup"><span data-stu-id="b0009-187">Guard platform-specific APIs with guard methods</span></span>

<span data-ttu-id="b0009-188">保護メソッドのプラットフォーム名は、呼び出し元のプラットフォーム依存 API のプラットフォーム名と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0009-188">The guard method's platform name should match with the calling platform-dependent API platform name.</span></span> <span data-ttu-id="b0009-189">呼び出し元 API のプラットフォーム文字列にバージョンが含まれている場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0009-189">If the platform string of the calling API includes the version:</span></span>

- <span data-ttu-id="b0009-190">`[SupportedOSPlatform("platformVersion")]` 属性の場合、保護メソッドのプラットフォームの `version` は、呼び出し元のプラットフォームの `Version` 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0009-190">For the `[SupportedOSPlatform("platformVersion")]` attribute, the guard method platform `version` should be greater than or equal to the calling platform's `Version`.</span></span>
- <span data-ttu-id="b0009-191">`[UnsupportedOSPlatform("platformVersion")]` 属性の場合、保護メソッドのプラットフォームの `version` は、呼び出し元のプラットフォームの `Version` 以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0009-191">For the `[UnsupportedOSPlatform("platformVersion")]` attribute, the guard method's platform `version` should be less than or equal to the calling platform's `Version`.</span></span>

  ```csharp
  public void CallingSupportedOnlyApis() // Allow list calls
  {
      if (OperatingSystem.IsWindows())
      {
          WindowsOnlyApi(); // will not warn
      }

      if (OperatingSystem.IsLinux())
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn, within one of the supported context
      }

      // Can use &&, || logical operators to guard combined attributes
      if (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10.0.19041)))
      {
          ApiSupportedFromWindows8UnsupportFromWindows10();
      }

      if (OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903))
      {
          AssemblySupportedOnWindowsApiSupportedFromWindows10(); // Only need to check latest supported version
      }
  }

  public void CallingUnsupportedApis()
  {
      if (!OperatingSystem.IsAndroid())
      {
          DoesNotWorkOnAndroid(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || OperatingSystem.IsWindowsVersionAtLeast(8))
      {
          StartedWindowsSupportFromVersion8(); // will not warn
      }

      if (!OperatingSystem.IsWindows() || // supported all other platforms
         (OperatingSystem.IsWindowsVersionAtLeast(8) && !OperatingSystem.IsWindowsVersionAtLeast(10, 0, 1903)))
      {
          StartedWindowsSupportFrom8UnsupportedFrom10(); // will not warn
      }
  }
  ```

- <span data-ttu-id="b0009-192">新しい <xref:System.OperatingSystem> API を使用できない `netstandard` または `netcoreapp` をターゲットとするコードを保護する必要がある場合、<xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> API が使用可能であり、アナライザーによって考慮されます。</span><span class="sxs-lookup"><span data-stu-id="b0009-192">If you need to guard code that targets `netstandard` or `netcoreapp` where new <xref:System.OperatingSystem> APIs are not available, the <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform%2A?displayProperty=nameWithType> API can be used and will be respected by the analyzer.</span></span> <span data-ttu-id="b0009-193">ただし、これは <xref:System.OperatingSystem> に追加された新しい API ほど最適化されていません。</span><span class="sxs-lookup"><span data-stu-id="b0009-193">But it's not as optimized as the new APIs added in <xref:System.OperatingSystem>.</span></span> <span data-ttu-id="b0009-194">プラットフォームが <xref:System.Runtime.InteropServices.OSPlatform> 構造体でサポートされていない場合は、<xref:System.Runtime.InteropServices.OSPlatform.Create(System.String)?displayProperty=nameWithType> を呼び出して、アナライザーでも考慮される、プラットフォーム名を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b0009-194">If the platform is not supported in the <xref:System.Runtime.InteropServices.OSPlatform> struct, you can call <xref:System.Runtime.InteropServices.OSPlatform.Create(System.String)?displayProperty=nameWithType> and pass in the platform name, which the analyzer also respects.</span></span>

  ```csharp
  public void CallingSupportedOnlyApis()
  {
      if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
      {
          SupportedOnWindowsAndLinuxOnly(); // will not warn
      }

      if (RuntimeInformation.IsOSPlatform(OSPlatform.Create("browser")))
      {
          ApiOnlySupportedOnBrowser(); // call of browser specific API
      }
  }
  ```

### <a name="mark-call-site-as-platform-specific"></a><span data-ttu-id="b0009-195">呼び出しサイトをプラットフォーム固有としてマークする</span><span class="sxs-lookup"><span data-stu-id="b0009-195">Mark call site as platform-specific</span></span>

<span data-ttu-id="b0009-196">プラットフォーム名は、呼び出し元のプラットフォームに依存する API と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0009-196">Platform names should match the calling platform-dependent API.</span></span> <span data-ttu-id="b0009-197">プラットフォーム文字列にバージョンが含まれている場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0009-197">If the platform string includes a version:</span></span>

- <span data-ttu-id="b0009-198">`[SupportedOSPlatform("platformVersion")]` 属性の場合、呼び出しサイトのプラットフォームの `version` は、呼び出し元のプラットフォームの `Version` 以上である必要があります</span><span class="sxs-lookup"><span data-stu-id="b0009-198">For the `[SupportedOSPlatform("platformVersion")]` attribute, the call site platform `version` should be greater than or equal to the calling platform's `Version`</span></span>
- <span data-ttu-id="b0009-199">`[UnsupportedOSPlatform("platformVersion")]` 属性の場合、呼び出しサイトのプラットフォームの `version` は、呼び出し元のプラットフォームの `Version` 以下である必要があります</span><span class="sxs-lookup"><span data-stu-id="b0009-199">For the `[UnsupportedOSPlatform("platformVersion")]` attribute, the call site platform `version` should be less than or equal to the calling platform's `Version`</span></span>

  ```csharp
  // an API supported only on Windows.
  [SupportedOSPlatform("windows")]
  public void WindowsOnlyApi() { }

  // an API supported on Windows and Linux.
  [SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("Linux")]
  public void SupportedOnWindowsAndLinuxOnly() { }

  // an API only supported on Windows 8.0 and later, not supported for all other.
  // an API is removed/unsupported from version 10.0.19041.0.
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void ApiSupportedFromWindows8UnsupportFromWindows10() { }

  // an Assembly supported on Windows, the API added from version 10.0.19041.0.
  [assembly: SupportedOSPlatform("Windows")]
  [SupportedOSPlatform("windows10.0.19041.0")]
  public void AssemblySupportedOnWindowsApiSupportedFromWindows10() { }

  [SupportedOSPlatform("windows8.0")] // call site attributed Windows 8.0 or above.
  public void Caller()
  {
      WindowsOnlyApi(); // will not warn as call site is for Windows.

      // will not warn as call site is for Windows.
      SupportedOnWindowsAndLinuxOnly();

      // will not warn for the API's [SupportedOSPlatform("windows8.0")] attribute.
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // as the call site version is lower than calling version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows11.0")] // call site attributed with windows 11.0 or above.
  public void Caller2()
  {
      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is unsupported on 'windows' 10.0.19041.0 and later
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // will not warn as call site version higher than calling API.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")] // call site supports Windows from version 8.0 to 10.0.19041.0.
  public void Caller3()
  {
      // will not warn as caller has exact same attributes.
      ApiSupportedFromWindows8UnsupportFromWindows10();

      // Warns: 'ApiSupportedFromWindows8UnsupportFromWindows10' is supported on 'windows' 10.0.19041.0 and later
      // As call site stopped support from that version.
      AssemblySupportedOnWindowsApiSupportedFromWindows10();
  }

  // an API not supported on Android but supported on all other.
  [UnsupportedOSPlatform("android")]
  public void DoesNotWorkOnAndroid() { }

  // an API was unsupported on Windows until version 8.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  public void StartedWindowsSupportFromVersion8() { }

  // an API was unsupported on Windows until version8.0.
  // Then the API is removed (unsupported) from version 10.0.19041.0.
  // The API is considered supported everywhere else without constraints.
  [UnsupportedOSPlatform("windows")]
  [SupportedOSPlatform("windows8.0")]
  [UnsupportedOSPlatform("windows10.0.19041.0")]
  public void StartedWindowsSupportFrom8UnsupportedFrom10() { }

  [UnsupportedOSPlatform("windows")] // Caller no support Windows for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // warns 'DoesNotWorkOnAndroid' is unsupported on 'Android'.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }

  [UnsupportedOSPlatform("windows")]
  [UnsupportedOSPlatform("android")] // Caller not support Windows and Android for any version.
  public void Caller4()
  {
      DoesNotWorkOnAndroid(); // will not warn as call site not supports Android.

      // will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFromVersion8();

      // same, will not warns as the call site not support Windows at all, but supports all other.
      StartedWindowsSupportFrom8UnsupportedFrom10();
  }
  ```

### <a name="assert-the-call-site-with-platform-check"></a><span data-ttu-id="b0009-200">プラットフォーム チェックを使用して呼び出しサイトをアサートする</span><span class="sxs-lookup"><span data-stu-id="b0009-200">Assert the call-site with platform check</span></span>

<span data-ttu-id="b0009-201">[プラットフォーム保護の例](#guard-platform-specific-apis-with-guard-methods)で使用されているすべての条件チェックは、<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> の条件として使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b0009-201">All the conditional checks used in the [platform guard examples](#guard-platform-specific-apis-with-guard-methods) can also be used as the condition for <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>.</span></span>

  ```csharp
  // An API supported only on Linux.
  [SupportedOSPlatform("linux")]
  public void LinuxOnlyApi() { }

  public void Caller()
  {
      Debug.Assert(OperatingSystem.IsLinux());

      LinuxOnlyApi(); // will not warn
  }
  ```

## <a name="see-also"></a><span data-ttu-id="b0009-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0009-202">See also</span></span>

- [<span data-ttu-id="b0009-203">.NET 5 でのターゲット フレームワーク名</span><span class="sxs-lookup"><span data-stu-id="b0009-203">Target Framework Names in .NET 5</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)
- [<span data-ttu-id="b0009-204">プラットフォーム固有の API に注釈を付け、その使用を検出する</span><span class="sxs-lookup"><span data-stu-id="b0009-204">Annotating platform-specific APIs and detecting its use</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-checks/platform-checks.md)
- [<span data-ttu-id="b0009-205">特定のプラットフォームでサポートされていない API に注釈を付ける</span><span class="sxs-lookup"><span data-stu-id="b0009-205">Annotating APIs as unsupported on specific platforms</span></span>](https://github.com/dotnet/designs/blob/master/accepted/2020/platform-exclusion/platform-exclusion.md)
- [<span data-ttu-id="b0009-206">CA1416 プラットフォーム互換性アナライザー</span><span class="sxs-lookup"><span data-stu-id="b0009-206">CA1416 Platform compatibility analyzer</span></span>](../../fundamentals/code-analysis/quality-rules/ca1416.md)
- [<span data-ttu-id="b0009-207">.NET API アナライザー</span><span class="sxs-lookup"><span data-stu-id="b0009-207">.NET API analyzer</span></span>](../../standard/analyzers/api-analyzer.md)
