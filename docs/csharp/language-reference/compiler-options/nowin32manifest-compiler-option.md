---
title: -nowin32manifest (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602719"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="e24f1-102">-nowin32manifest (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="e24f1-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="e24f1-103">**-nowin32manifest** オプションを利用し、アプリケーション マニフェストを実行可能ファイルに埋め込まないようコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="e24f1-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e24f1-104">構文</span><span class="sxs-lookup"><span data-stu-id="e24f1-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="e24f1-105">解説</span><span class="sxs-lookup"><span data-stu-id="e24f1-105">Remarks</span></span>  
 <span data-ttu-id="e24f1-106">このオプションを使用すると、Win32 リソース ファイルに、あるいは後のビルド ステップでアプリケーション マニフェストを指定しない限り、 Windows Vista で仮想化に従います。</span><span class="sxs-lookup"><span data-stu-id="e24f1-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="e24f1-107">Visual Studio では、このオプションを **[アプリケーション プロパティ]** ページで設定します。 **[マニフェスト]** ドロップダウン リストの **[マニフェストなしでアプリケーションを作成します]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e24f1-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="e24f1-108">詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e24f1-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="e24f1-109">マニフェスト作成の詳細については、「[-win32manifest (C# コンパイラ オプション)](./win32manifest-compiler-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e24f1-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e24f1-110">参照</span><span class="sxs-lookup"><span data-stu-id="e24f1-110">See also</span></span>

- [<span data-ttu-id="e24f1-111">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="e24f1-111">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e24f1-112">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="e24f1-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
