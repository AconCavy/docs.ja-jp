---
title: インストールされている .NET Framework バージョンを確認する
description: コード、regedit.exe、または PowerShell を使用して、Windows レジストリに対してクエリを実行することで、コンピューターにインストールされている .NET Framework のバージョンを検出します。
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: d25e4ae97877462b2a3b90e51262fb656921e392
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205498"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="17bd8-103">方法: インストールされている .NET Framework バージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="17bd8-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="17bd8-104">ユーザーはコンピューターに複数のバージョンの .NET Framework を[インストール](../install/index.md)して実行できます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-104">Users can [install](../install/index.md) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="17bd8-105">アプリを開発または配置する場合、どのバージョンの .NET Framework がユーザーのコンピューターにインストールされているかを確認しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="17bd8-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="17bd8-106">レジストリには、コンピューターにインストールされている .NET Framework のバージョンの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-106">The registry contains a list of the .NET Framework versions installed on a computer.</span></span>

<span data-ttu-id="17bd8-107">.NET Framework は、個別にバージョン管理される 2 つの主要コンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-107">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="17bd8-108">アプリに機能を提供する型やリソースのコレクションである一連のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="17bd8-108">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="17bd8-109">.NET Framework とアセンブリは同じバージョン番号を共有します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-109">The .NET Framework and assemblies share the same version number.</span></span> <span data-ttu-id="17bd8-110">たとえば、.NET Framework のバージョンには、4.5、4.6.1、および 4.7.2 が含まれます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-110">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="17bd8-111">アプリのコードを管理および実行する共通言語ランタイム (CLR)。</span><span class="sxs-lookup"><span data-stu-id="17bd8-111">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="17bd8-112">1 つの CLR バージョンは、通常複数の NET Framework バージョンをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-112">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="17bd8-113">たとえば、CLR バージョン 4.0.30319.*xxxxx* で *xxxxx* が 42000 未満の場合、.NET Framework バージョン 4 から 4.5.2 がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-113">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="17bd8-114">4\.0.30319.42000 以上の CLR バージョンでは、.NET Framework 4.6 以降の .NET Framework バージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-114">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="17bd8-115">コミュニティで管理されているツールを使用して、インストールされている .NET Framework バージョンを検出できます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-115">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="17bd8-116">.NET 2.0 コマンド ライン ツール。</span><span class="sxs-lookup"><span data-stu-id="17bd8-116">A .NET 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="17bd8-117">PowerShell 2.0 モジュール。</span><span class="sxs-lookup"><span data-stu-id="17bd8-117">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="17bd8-118">.NET Framework の各バージョン用にインストールされている更新プログラムの検出については、「[方法:インストールされている .NET Framework の更新プログラムを確認する](how-to-determine-which-net-framework-updates-are-installed.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17bd8-118">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="17bd8-119">.NET Framework 4.5 以降のバージョンを検出する</span><span class="sxs-lookup"><span data-stu-id="17bd8-119">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="17bd8-120">コンピューターにインストールされている .NET Framework (4.5 以降) のバージョンは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** のレジストリに一覧されています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-120">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="17bd8-121">**Full** サブキーが見つからない場合、.NET Framework 4.5 以降はインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="17bd8-121">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="17bd8-122">レジストリ パスの **NET Framework Setup** サブキーの先頭は、ピリオドでは "*ありません*"。</span><span class="sxs-lookup"><span data-stu-id="17bd8-122">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="17bd8-123">レジストリの **Release** REG_DWORD の値は、インストールされている .NET Framework のバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-123">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="17bd8-124">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="17bd8-124">.NET Framework version</span></span> | <span data-ttu-id="17bd8-125">**Release** の値</span><span class="sxs-lookup"><span data-stu-id="17bd8-125">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="17bd8-126">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="17bd8-126">.NET Framework 4.5</span></span>     | <span data-ttu-id="17bd8-127">すべての Windows オペレーティング システム:378389</span><span class="sxs-lookup"><span data-stu-id="17bd8-127">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="17bd8-128">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="17bd8-128">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="17bd8-129">Windows 8.1 および Windows Server 2012 R2:378675</span><span class="sxs-lookup"><span data-stu-id="17bd8-129">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="17bd8-130">他のすべての Windows オペレーティング システム:378758</span><span class="sxs-lookup"><span data-stu-id="17bd8-130">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="17bd8-131">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="17bd8-131">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="17bd8-132">すべての Windows オペレーティング システム:379893</span><span class="sxs-lookup"><span data-stu-id="17bd8-132">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="17bd8-133">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="17bd8-133">.NET Framework 4.6</span></span>     | <span data-ttu-id="17bd8-134">Windows 10:393295</span><span class="sxs-lookup"><span data-stu-id="17bd8-134">On Windows 10: 393295</span></span><br /><span data-ttu-id="17bd8-135">他のすべての Windows オペレーティング システム:393297</span><span class="sxs-lookup"><span data-stu-id="17bd8-135">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="17bd8-136">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="17bd8-136">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="17bd8-137">Windows 10 November Update システム:394254</span><span class="sxs-lookup"><span data-stu-id="17bd8-137">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="17bd8-138">他のすべての Windows オペレーティング システム (Windows 10 を含む):394271</span><span class="sxs-lookup"><span data-stu-id="17bd8-138">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="17bd8-139">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="17bd8-139">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="17bd8-140">Windows 10 Anniversary Update および Windows Server 2016 の場合:394802</span><span class="sxs-lookup"><span data-stu-id="17bd8-140">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="17bd8-141">他のすべての Windows オペレーティング システム (他の Windows 10 オペレーティング システムを含む):394806</span><span class="sxs-lookup"><span data-stu-id="17bd8-141">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="17bd8-142">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="17bd8-142">.NET Framework 4.7</span></span>     | <span data-ttu-id="17bd8-143">Windows 10 Creators Update:460798</span><span class="sxs-lookup"><span data-stu-id="17bd8-143">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="17bd8-144">他のすべての Windows オペレーティング システム (他の Windows 10 オペレーティング システムを含む):460805</span><span class="sxs-lookup"><span data-stu-id="17bd8-144">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="17bd8-145">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="17bd8-145">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="17bd8-146">Windows 10 Fall Creators Update および Windows Server バージョン 1709:461308</span><span class="sxs-lookup"><span data-stu-id="17bd8-146">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="17bd8-147">他のすべての Windows オペレーティング システム (他の Windows 10 オペレーティング システムを含む):461310</span><span class="sxs-lookup"><span data-stu-id="17bd8-147">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="17bd8-148">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="17bd8-148">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="17bd8-149">Windows 10 April 2018 Update および Windows Server バージョン 1803:461808</span><span class="sxs-lookup"><span data-stu-id="17bd8-149">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="17bd8-150">Windows 10 April 2018 Update および Windows Server バージョン 1803 以外のすべての Windows オペレーティング システム:461814</span><span class="sxs-lookup"><span data-stu-id="17bd8-150">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="17bd8-151">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="17bd8-151">.NET Framework 4.8</span></span>     | <span data-ttu-id="17bd8-152">Windows 10 May 2019 Update および Windows 10 November 2019 Update:528040</span><span class="sxs-lookup"><span data-stu-id="17bd8-152">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="17bd8-153">Windows 10 May 2020 Update:528209</span><span class="sxs-lookup"><span data-stu-id="17bd8-153">On Windows 10 May 2020 Update: 528209</span></span><br/><span data-ttu-id="17bd8-154">他のすべての Windows オペレーティング システム (他の Windows 10 オペレーティング システムを含む):528049</span><span class="sxs-lookup"><span data-stu-id="17bd8-154">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="17bd8-155">最小バージョン</span><span class="sxs-lookup"><span data-stu-id="17bd8-155">Minimum version</span></span>

<span data-ttu-id="17bd8-156">.NET Framework の "*最小*" バージョンが存在するかどうかを判断するには、前の表から、そのバージョンの最小の **Release** REG_DWORD の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-156">To determine whether a *minimum* version of the .NET Framework is present, use the smallest **Release** REG_DWORD value for that version from the previous table.</span></span>

<span data-ttu-id="17bd8-157">たとえば、アプリケーションが .NET Framework 4.8 以降のバージョンで実行されている場合、**Release** REG_DWORD の値が 528040 "*以上*" であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-157">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that is *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="17bd8-158">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="17bd8-158">.NET Framework version</span></span> | <span data-ttu-id="17bd8-159">最小値</span><span class="sxs-lookup"><span data-stu-id="17bd8-159">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="17bd8-160">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="17bd8-160">.NET Framework 4.5</span></span>     | <span data-ttu-id="17bd8-161">378389</span><span class="sxs-lookup"><span data-stu-id="17bd8-161">378389</span></span> |
| <span data-ttu-id="17bd8-162">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="17bd8-162">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="17bd8-163">378675</span><span class="sxs-lookup"><span data-stu-id="17bd8-163">378675</span></span> |
| <span data-ttu-id="17bd8-164">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="17bd8-164">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="17bd8-165">379893</span><span class="sxs-lookup"><span data-stu-id="17bd8-165">379893</span></span> |
| <span data-ttu-id="17bd8-166">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="17bd8-166">.NET Framework 4.6</span></span>     | <span data-ttu-id="17bd8-167">393295</span><span class="sxs-lookup"><span data-stu-id="17bd8-167">393295</span></span> |
| <span data-ttu-id="17bd8-168">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="17bd8-168">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="17bd8-169">394254</span><span class="sxs-lookup"><span data-stu-id="17bd8-169">394254</span></span> |
| <span data-ttu-id="17bd8-170">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="17bd8-170">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="17bd8-171">394802</span><span class="sxs-lookup"><span data-stu-id="17bd8-171">394802</span></span> |
| <span data-ttu-id="17bd8-172">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="17bd8-172">.NET Framework 4.7</span></span>     | <span data-ttu-id="17bd8-173">460798</span><span class="sxs-lookup"><span data-stu-id="17bd8-173">460798</span></span> |
| <span data-ttu-id="17bd8-174">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="17bd8-174">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="17bd8-175">461308</span><span class="sxs-lookup"><span data-stu-id="17bd8-175">461308</span></span> |
| <span data-ttu-id="17bd8-176">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="17bd8-176">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="17bd8-177">461808</span><span class="sxs-lookup"><span data-stu-id="17bd8-177">461808</span></span> |
| <span data-ttu-id="17bd8-178">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="17bd8-178">.NET Framework 4.8</span></span>     | <span data-ttu-id="17bd8-179">528040</span><span class="sxs-lookup"><span data-stu-id="17bd8-179">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="17bd8-180">レジストリ エディターを使用する</span><span class="sxs-lookup"><span data-stu-id="17bd8-180">Use Registry Editor</span></span>

01. <span data-ttu-id="17bd8-181">**スタート** メニューの **[ファイル名を指定して実行]** を選択し、「*regedit*」と入力し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-181">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="17bd8-182">regedit を実行するには、管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="17bd8-182">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="17bd8-183">レジストリ エディターで、次のサブキーを開きます。**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**。</span><span class="sxs-lookup"><span data-stu-id="17bd8-183">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="17bd8-184">**Full** サブキーが存在しない場合は、.NET Framework 4.5 以降はインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="17bd8-184">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

01. <span data-ttu-id="17bd8-185">**Release** という REG_DWORD のエントリを確認します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-185">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="17bd8-186">それがある場合、.NET Framework 4.5 以降がインストールされています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-186">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="17bd8-187">その値は、.NET Framework の特定のバージョンに対応しています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-187">Its value corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="17bd8-188">たとえば、次の図では、**Release** エントリの値は 528040 で、これは .NET Framework 4.8 のリリース キーです。</span><span class="sxs-lookup"><span data-stu-id="17bd8-188">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

    <span data-ttu-id="17bd8-189">![.NET Framework 4.5 のレジストリ エントリ](./media/clr-installdir.png ".NET Framework 4.5 のレジストリ エントリ。")</span><span class="sxs-lookup"><span data-stu-id="17bd8-189">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="17bd8-190">PowerShell を使用して最小バージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="17bd8-190">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="17bd8-191">PowerShell コマンドを使用し、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** サブキーの **Release** エントリの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-191">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="17bd8-192">次の例では、**Release** エントリの値を確認して、.NET Framework 4.6.2 以降がインストールされているかどうかを判断しています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-192">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="17bd8-193">このコードでは、インストールされていない場合は、`True` が返され、されている場合は `False` が返されます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-193">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="17bd8-194">コードを使用してレジストリのクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="17bd8-194">Query the registry using code</span></span>

01. <span data-ttu-id="17bd8-195"><xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> メソッドと <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> メソッドを使用し、Windows レジストリの **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** サブキーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="17bd8-195">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="17bd8-196">実行しているアプリが 32 ビットで、64 ビットの Windows で実行されている場合、レジストリ パスは前に示したものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="17bd8-196">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="17bd8-197">64 ビットのレジストリは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** サブキーで入手できます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-197">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="17bd8-198">たとえば、.NET Framework 4.5 のレジストリ サブキーは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** になります。</span><span class="sxs-lookup"><span data-stu-id="17bd8-198">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="17bd8-199">**Release** REG_DWORD の値を確認して、インストールされているバージョンを判断します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-199">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="17bd8-200">上位互換性があるかを確認するには、[.NET Framework のバージョンの表](#version_table)で示されている値以上の値があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-200">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="17bd8-201">次の例では、レジストリから **Release** の値を確認し、インストールされている .NET Framework 4.5 以降のバージョンを探しています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-201">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="17bd8-202">この例では、バージョンのチェックで推奨されている方法に従います。</span><span class="sxs-lookup"><span data-stu-id="17bd8-202">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="17bd8-203">**Release** エントリの値が、既知のリリース キー値*以上*かどうかを確認しています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-203">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="17bd8-204">最新バージョンから最も古いバージョンの順にチェックします。</span><span class="sxs-lookup"><span data-stu-id="17bd8-204">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="17bd8-205">.NET Framework 1.0 から 4.0 を検出する</span><span class="sxs-lookup"><span data-stu-id="17bd8-205">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="17bd8-206">.NET Framework 1.1 から 4.0 の各バージョンは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** のサブキーとして一覧されています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-206">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="17bd8-207">次の表には、各 .NET Framework バージョンへのパスが一覧されています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-207">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="17bd8-208">ほとんどのバージョンでは、`1` の **Install** REG_DWORD の値があり、このバージョンがインストールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-208">For most versions, there's a **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="17bd8-209">これらのサブキーには、バージョン文字列を含む **Version** REG_SZ の値もあります。</span><span class="sxs-lookup"><span data-stu-id="17bd8-209">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="17bd8-210">レジストリ パスの **NET Framework Setup** サブキーの先頭は、ピリオドでは "*ありません*"。</span><span class="sxs-lookup"><span data-stu-id="17bd8-210">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="17bd8-211">Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="17bd8-211">Framework Version</span></span>  | <span data-ttu-id="17bd8-212">レジストリ サブキー</span><span class="sxs-lookup"><span data-stu-id="17bd8-212">Registry Subkey</span></span> | <span data-ttu-id="17bd8-213">[値]</span><span class="sxs-lookup"><span data-stu-id="17bd8-213">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="17bd8-214">1</span><span class="sxs-lookup"><span data-stu-id="17bd8-214">1.0</span></span>                | <span data-ttu-id="17bd8-215">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span><span class="sxs-lookup"><span data-stu-id="17bd8-215">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="17bd8-216">**Install** REG_SZ は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="17bd8-216">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="17bd8-217">1.1</span><span class="sxs-lookup"><span data-stu-id="17bd8-217">1.1</span></span>                | <span data-ttu-id="17bd8-218">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="17bd8-218">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="17bd8-219">**Install** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="17bd8-219">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="17bd8-220">2.0</span><span class="sxs-lookup"><span data-stu-id="17bd8-220">2.0</span></span>                | <span data-ttu-id="17bd8-221">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="17bd8-221">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="17bd8-222">**Install** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="17bd8-222">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="17bd8-223">3.0</span><span class="sxs-lookup"><span data-stu-id="17bd8-223">3.0</span></span>                | <span data-ttu-id="17bd8-224">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span><span class="sxs-lookup"><span data-stu-id="17bd8-224">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="17bd8-225">**InstallSuccess** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="17bd8-225">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="17bd8-226">3.5</span><span class="sxs-lookup"><span data-stu-id="17bd8-226">3.5</span></span>                | <span data-ttu-id="17bd8-227">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span><span class="sxs-lookup"><span data-stu-id="17bd8-227">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="17bd8-228">**Install** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="17bd8-228">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="17bd8-229">4.0 Client Profile</span><span class="sxs-lookup"><span data-stu-id="17bd8-229">4.0 Client Profile</span></span> | <span data-ttu-id="17bd8-230">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span><span class="sxs-lookup"><span data-stu-id="17bd8-230">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="17bd8-231">**Install** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="17bd8-231">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="17bd8-232">4.0 Full Profile</span><span class="sxs-lookup"><span data-stu-id="17bd8-232">4.0 Full Profile</span></span>   | <span data-ttu-id="17bd8-233">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span><span class="sxs-lookup"><span data-stu-id="17bd8-233">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="17bd8-234">**Install** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="17bd8-234">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="17bd8-235">実行しているアプリが 32 ビットで、64 ビットの Windows で実行されている場合、レジストリ パスは前に示したものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="17bd8-235">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="17bd8-236">64 ビットのレジストリは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** サブキーで入手できます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-236">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="17bd8-237">たとえば、.NET Framework 3.5 のレジストリ サブキーは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5** になります。</span><span class="sxs-lookup"><span data-stu-id="17bd8-237">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="17bd8-238">.NET Framework 1.0 サブキーへのレジストリ パスは、他のものとは異なるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="17bd8-238">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="17bd8-239">レジストリ エディターを使用する (古いバージョンのフレームワーク)</span><span class="sxs-lookup"><span data-stu-id="17bd8-239">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="17bd8-240">**スタート** メニューの **[ファイル名を指定して実行]** を選択し、「*regedit*」と入力し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-240">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="17bd8-241">regedit を実行するには、管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="17bd8-241">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="17bd8-242">確認するバージョンと一致するサブキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-242">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="17bd8-243">「[.NET Framework 1.0 から 4.0 を検出する](#detect-net-framework-10-through-40)」セクションの表を使用します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-243">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="17bd8-244">次の図では、.NET Framework 3.5 のサブキーとその **Version** の値を示しています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-244">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="17bd8-245">![.NET Framework 3.5 のレジストリ エントリ。](./media/net-4-and-earlier.png ".NET Framework 3.5 以前のバージョン")</span><span class="sxs-lookup"><span data-stu-id="17bd8-245">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="17bd8-246">コードを使用してレジストリのクエリを実行する (以前のバージョンのフレームワーク)</span><span class="sxs-lookup"><span data-stu-id="17bd8-246">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="17bd8-247"><xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> クラスを使用して、Windows レジストリの **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** サブキーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="17bd8-247">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17bd8-248">実行しているアプリが 32 ビットで、64 ビットの Windows で実行されている場合、レジストリ パスは前に示したものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="17bd8-248">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="17bd8-249">64 ビットのレジストリは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** サブキーで入手できます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-249">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="17bd8-250">たとえば、.NET Framework 3.5 のレジストリ サブキーは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5** になります。</span><span class="sxs-lookup"><span data-stu-id="17bd8-250">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="17bd8-251">次の例では、インストールされている .NET Framework のバージョン 1 から 4 が検索されています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-251">The following example finds the .NET Framework 1 through 4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="17bd8-252">CLR のバージョンを探す</span><span class="sxs-lookup"><span data-stu-id="17bd8-252">Find CLR versions</span></span>

<span data-ttu-id="17bd8-253">.NET Framework と共にインストールされる .NET Framework CLR は、個別にバージョン管理されます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-253">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="17bd8-254">.NET Framework CLR のバージョンを検出するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="17bd8-254">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="17bd8-255">**Clrver.exe ツール**</span><span class="sxs-lookup"><span data-stu-id="17bd8-255">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="17bd8-256">[CLR バージョン ツール (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) を使用して、コンピューターにインストールされている CLR のバージョンを判断します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-256">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="17bd8-257">[Visual Studio の開発者コマンド プロンプト](../tools/developer-command-prompt-for-vs.md)を開いて、「`clrver`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-257">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="17bd8-258">出力例</span><span class="sxs-lookup"><span data-stu-id="17bd8-258">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="17bd8-259">**`Environment` クラス**</span><span class="sxs-lookup"><span data-stu-id="17bd8-259">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="17bd8-260">.NET Framework 4.5 以降のバージョンでは、CLR のバージョンの検出に <xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="17bd8-260">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="17bd8-261">代わりに、「[.NET Framework 4.5 以降のバージョンを検出する](#detect-net-framework-45-and-later-versions)」で説明するように、レジストリのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-261">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>
  
  01. <span data-ttu-id="17bd8-262"><xref:System.Environment.Version?displayProperty=nameWithType> プロパティを照会し、<xref:System.Version> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-262">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>
  
      <span data-ttu-id="17bd8-263">返された `System.Version` オブジェクトは、現在コードを実行しているランタイムのバージョンを示しています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-263">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="17bd8-264">コンピューターにインストールされている可能性のある、アセンブリのバージョンやランタイムのその他のバージョンは返されません。</span><span class="sxs-lookup"><span data-stu-id="17bd8-264">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>
  
      <span data-ttu-id="17bd8-265">.NET Framework バージョン 4、4.5、4.5.1、4.5.2 の場合は、返される <xref:System.Version> オブジェクトの文字列表現は 4.0.30319.*xxxxx* という形式です。この *xxxxx* は 42000 未満になります。</span><span class="sxs-lookup"><span data-stu-id="17bd8-265">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="17bd8-266">.NET Framework 4.6 以降のバージョンの場合は、4.0.30319.42000 という形式です。</span><span class="sxs-lookup"><span data-stu-id="17bd8-266">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>
  
  01. <span data-ttu-id="17bd8-267">**Version** オブジェクトを取得したら、次のようにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-267">After you have the **Version** object, query it as follows:</span></span>
  
      - <span data-ttu-id="17bd8-268">メジャー リリース識別子 (たとえば、バージョン 4.0 の場合の *4*) には、<xref:System.Version.Major%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-268">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>
  
      - <span data-ttu-id="17bd8-269">マイナー リリース識別子 (たとえば、バージョン 4.0 の場合の *0*) には、<xref:System.Version.Minor%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-269">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>
  
      - <span data-ttu-id="17bd8-270">バージョンの完全な文字列 (たとえば、*4.0.30319.18010*) には、<xref:System.Version.ToString%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="17bd8-270">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="17bd8-271">このメソッドでは、コードを実行しているランタイムのバージョンを示す値が 1 つ返されます。</span><span class="sxs-lookup"><span data-stu-id="17bd8-271">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="17bd8-272">コンピューターにインストールされている可能性のあるアセンブリ バージョンやその他のランタイム バージョンは返されません。</span><span class="sxs-lookup"><span data-stu-id="17bd8-272">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="17bd8-273">次の例では、<xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティを使用して CLR バージョンの情報を取得しています。</span><span class="sxs-lookup"><span data-stu-id="17bd8-273">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="17bd8-274">関連項目</span><span class="sxs-lookup"><span data-stu-id="17bd8-274">See also</span></span>

- [<span data-ttu-id="17bd8-275">方法: インストールされている .NET Framework の更新プログラムを確認する</span><span class="sxs-lookup"><span data-stu-id="17bd8-275">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="17bd8-276">開発者向けの .NET Framework のインストール</span><span class="sxs-lookup"><span data-stu-id="17bd8-276">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="17bd8-277">.NET Framework のバージョンおよび依存関係</span><span class="sxs-lookup"><span data-stu-id="17bd8-277">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
