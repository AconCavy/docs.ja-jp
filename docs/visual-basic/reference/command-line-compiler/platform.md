---
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: a6226b73d5d5d4d48a71afe39e8a546019d4c0bc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352342"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="950a6-102">-platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="950a6-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="950a6-103">出力ファイルをどのプラットフォーム用の共通言語ランタイム (CLR) で実行するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="950a6-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="950a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="950a6-104">Syntax</span></span>  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="950a6-105">引数</span><span class="sxs-lookup"><span data-stu-id="950a6-105">Arguments</span></span>  
  
|<span data-ttu-id="950a6-106">用語</span><span class="sxs-lookup"><span data-stu-id="950a6-106">Term</span></span>|<span data-ttu-id="950a6-107">Definition</span><span class="sxs-lookup"><span data-stu-id="950a6-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="950a6-108">32 ビット x86 互換 CLR で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="950a6-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="950a6-109">AMD64 または EM64T 命令セットをサポートするコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="950a6-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="950a6-110">Itanium プロセッサ搭載のコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="950a6-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="950a6-111">ARM (アドバンスト RISC マシン) プロセッサ搭載のコンピューター上で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="950a6-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="950a6-112">任意のプラットフォーム上で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="950a6-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="950a6-113">アプリケーションは、Windows の 32 ビット バージョンでは 32 ビット アプリケーションとして、Windows の 64 ビット バージョンでは 64 ビット アプリケーションとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="950a6-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="950a6-114">このフラグが既定値です。</span><span class="sxs-lookup"><span data-stu-id="950a6-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="950a6-115">任意のプラットフォーム上で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="950a6-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="950a6-116">アプリケーションは、Windows の 32 ビット バージョンおよび 64 ビット バージョンの両方で、 32 ビット アプリケーションとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="950a6-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="950a6-117">このフラグは、実行可能ファイル () に対してのみ有効です。EXE) と .NET Framework 4.5 が必要です。</span><span class="sxs-lookup"><span data-stu-id="950a6-117">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="950a6-118">コメント</span><span class="sxs-lookup"><span data-stu-id="950a6-118">Remarks</span></span>  
 <span data-ttu-id="950a6-119">出力ファイルの対象となるプロセッサの種類を指定するには、`-platform` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="950a6-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="950a6-120">通常、Visual Basic で記述された .NET Framework アセンブリは、プラットフォームに関係なく、同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="950a6-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="950a6-121">ただし、プラットフォーム間で動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="950a6-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="950a6-122">その一般的な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="950a6-122">These common cases are:</span></span>  
  
- <span data-ttu-id="950a6-123">プラットフォームによってメンバーのサイズが変わる構造体 (ポインター型など)</span><span class="sxs-lookup"><span data-stu-id="950a6-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="950a6-124">定数のサイズを含むポインター演算</span><span class="sxs-lookup"><span data-stu-id="950a6-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="950a6-125">ハンドルに `Integer` ではなく <xref:System.IntPtr> を使用した不適切なプラットフォーム呼び出しまたは COM 宣言</span><span class="sxs-lookup"><span data-stu-id="950a6-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="950a6-126"><xref:System.IntPtr> の `Integer` へのキャスト</span><span class="sxs-lookup"><span data-stu-id="950a6-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="950a6-127">すべてのプラットフォームに存在するとは限らないコンポーネントを使用したプラットフォーム呼び出しまたは COM 相互運用機能の使用</span><span class="sxs-lookup"><span data-stu-id="950a6-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="950a6-128">**-Platform**オプションを使用すると、コードが実行されるアーキテクチャについて想定したことがわかった場合に、いくつかの問題を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="950a6-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="950a6-129">具体的な内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="950a6-129">Specifically:</span></span>  
  
- <span data-ttu-id="950a6-130">64 ビット プラットフォームを対象にし、アプリケーションを 32 ビット マシンで実行した場合、エラー メッセージは、このスイッチを使用しない場合よりも、エラー メッセージがかなり早期に出力され、より絞り込まれた内容になります。</span><span class="sxs-lookup"><span data-stu-id="950a6-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="950a6-131">オプションに `x86` フラグを設定し、その後、アプリケーションを 64 ビット マシンで実行した場合、アプリケーションはネイティブに実行されず、WOW サブシステムで実行されます。</span><span class="sxs-lookup"><span data-stu-id="950a6-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="950a6-132">64 ビット Windows オペレーティング システムの場合:</span><span class="sxs-lookup"><span data-stu-id="950a6-132">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="950a6-133">`-platform:x86` でコンパイルされたアセンブリは、WOW64 の下で動作する 32 ビット CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="950a6-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="950a6-134">`-platform:anycpu` でコンパイルされた実行可能ファイルは、64 ビット CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="950a6-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="950a6-135">`-platform:anycpu` でコンパイルでされた DLL は、ロード先のプロセスと同じ CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="950a6-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="950a6-136">`-platform:anycpu32bitpreferred` でコンパイルされた実行可能ファイルは、32 ビット CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="950a6-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="950a6-137">64ビットバージョンの Windows で実行するアプリケーションを開発する方法の詳細については、「 [64 ビットアプリケーション](../../../framework/64-bit-apps.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="950a6-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="950a6-138">Visual Studio IDE でプラットフォームを設定するには</span><span class="sxs-lookup"><span data-stu-id="950a6-138">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="950a6-139">**ソリューションエクスプローラー**で、プロジェクトを選択し、 **[プロジェクト]** メニューを開き、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="950a6-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="950a6-140">**[コンパイル]** タブで、 **[32 ビットを優先]** チェックボックスをオンまたはオフにします。または、 **[ターゲット CPU]** の一覧で値を選択します。</span><span class="sxs-lookup"><span data-stu-id="950a6-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="950a6-141">詳細については、「[[コンパイル] ページ (プロジェクトデザイナー)」 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="950a6-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="950a6-142">例</span><span class="sxs-lookup"><span data-stu-id="950a6-142">Example</span></span>  
 <span data-ttu-id="950a6-143">次の例は、`-platform` コンパイラ オプションを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="950a6-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="950a6-144">参照</span><span class="sxs-lookup"><span data-stu-id="950a6-144">See also</span></span>

- [<span data-ttu-id="950a6-145">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="950a6-145">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="950a6-146">Visual Basic コマンドラインコンパイラ</span><span class="sxs-lookup"><span data-stu-id="950a6-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="950a6-147">コンパイルコマンドラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="950a6-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
