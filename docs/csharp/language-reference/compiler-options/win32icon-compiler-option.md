---
description: -win32icon (C# コンパイラ オプション)
title: -win32icon (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 76a54f9011371492bdc15f15c3e40d51082deed3
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138411"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="7383f-103">-win32icon (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="7383f-103">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="7383f-104">**-win32icon** オプションは、エクスプローラーで出力ファイルを適切に表示する .ico ファイルを出力ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="7383f-104">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7383f-105">構文</span><span class="sxs-lookup"><span data-stu-id="7383f-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="7383f-106">引数</span><span class="sxs-lookup"><span data-stu-id="7383f-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="7383f-107">出力ファイルに追加する .ico ファイル。</span><span class="sxs-lookup"><span data-stu-id="7383f-107">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7383f-108">注釈</span><span class="sxs-lookup"><span data-stu-id="7383f-108">Remarks</span></span>  
 <span data-ttu-id="7383f-109">.ico ファイルは[リソース コンパイラ](/windows/desktop/menurc/resource-compiler)で作成できます。</span><span class="sxs-lookup"><span data-stu-id="7383f-109">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="7383f-110">リソース コンパイラは、Visual C++ プログラムをコンパイルするときに呼び出されます。.ico ファイルは .rc ファイルから作成されます。</span><span class="sxs-lookup"><span data-stu-id="7383f-110">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="7383f-111">.NET Framework リソース ファイルの [-linkresource](./linkresource-compiler-option.md) (参照) または [-resource](./resource-compiler-option.md) (アタッチ) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7383f-111">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="7383f-112">.res ファイルのインポートについては、[-win32res](./win32res-compiler-option.md) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7383f-112">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7383f-113">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="7383f-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="7383f-114">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="7383f-114">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="7383f-115">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7383f-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="7383f-116">**[アプリケーション アイコン]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="7383f-116">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="7383f-117">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7383f-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7383f-118">例</span><span class="sxs-lookup"><span data-stu-id="7383f-118">Example</span></span>  
 <span data-ttu-id="7383f-119">`in.cs` をコンパイルし、.ico ファイル `rf.ico` をアタッチし、`in.exe` を作成します。</span><span class="sxs-lookup"><span data-stu-id="7383f-119">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7383f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="7383f-120">See also</span></span>

- [<span data-ttu-id="7383f-121">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="7383f-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7383f-122">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="7383f-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
