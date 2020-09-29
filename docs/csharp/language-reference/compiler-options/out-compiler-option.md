---
description: -out (C# コンパイラ オプション)
title: -out (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 409760ee0b147065a2128c62c304fb5d70cfcf42
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193882"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="09fbe-103">-out (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="09fbe-103">-out (C# Compiler Options)</span></span>

<span data-ttu-id="09fbe-104">**-out** オプションは、出力ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="09fbe-104">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09fbe-105">構文</span><span class="sxs-lookup"><span data-stu-id="09fbe-105">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="09fbe-106">引数</span><span class="sxs-lookup"><span data-stu-id="09fbe-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="09fbe-107">コンパイラによって作成された出力ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="09fbe-107">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09fbe-108">注釈</span><span class="sxs-lookup"><span data-stu-id="09fbe-108">Remarks</span></span>  

 <span data-ttu-id="09fbe-109">コマンド ラインでは、コンパイル用に複数の出力ファイルを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="09fbe-109">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="09fbe-110">コンパイラは、**-out** オプションの後に 1 つまたは複数のソース コード ファイルがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="09fbe-110">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="09fbe-111">そしてすべてのソース コード ファイルがその **-out** オプションで指定された出力ファイルにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="09fbe-111">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="09fbe-112">作成するファイルの完全な名前と拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="09fbe-112">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="09fbe-113">出力ファイルの名前を指定しない場合:</span><span class="sxs-lookup"><span data-stu-id="09fbe-113">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="09fbe-114">.exe は **Main** メソッドを含むソース コード ファイルからその名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="09fbe-114">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="09fbe-115">.dll または .netmodule は最初のソース コード ファイルからその名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="09fbe-115">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="09fbe-116">1 つの出力ファイルをコンパイルするために使用されるソース コード ファイルは、別の出力ファイルのコンパイルの同じコンパイルでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="09fbe-116">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="09fbe-117">コマンド ラインのコンパイルで複数の出力ファイルを生成する場合は、出力ファイルのいずれか 1 つだけがアセンブリになれること、および (**-out** で暗黙的または明示的に) 指定された最初の出力ファイルだけがアセンブリになれることに留意してください。</span><span class="sxs-lookup"><span data-stu-id="09fbe-117">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="09fbe-118">コンパイルの一部として生成されるすべてのモジュールが、同じくコンパイルで作成されるアセンブリに関連付けらるファイルになります。</span><span class="sxs-lookup"><span data-stu-id="09fbe-118">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="09fbe-119">[ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) を使用して、アセンブリ マニフェストを表示し、関連付けられているファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="09fbe-119">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="09fbe-120">exe をフレンド アセンブリのターゲットにするには、-out コンパイラ オプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="09fbe-120">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="09fbe-121">詳細については、「[フレンド アセンブリ](../../../standard/assembly/friend.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09fbe-121">For more information see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="09fbe-122">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="09fbe-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="09fbe-123">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="09fbe-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="09fbe-124">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="09fbe-124">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="09fbe-125">**[アセンブリ名]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="09fbe-125">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="09fbe-126">このコンパイラ オプションをプログラムで設定するには: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> は読み取り専用のプロパティで、プロジェクトの種類 (exe、ライブラリなど) と、アセンブリ名の組み合わせによって決まります。</span><span class="sxs-lookup"><span data-stu-id="09fbe-126">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="09fbe-127">これらのプロパティの一方または両方を変更するには、出力ファイル名を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09fbe-127">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09fbe-128">例</span><span class="sxs-lookup"><span data-stu-id="09fbe-128">Example</span></span>  

 <span data-ttu-id="09fbe-129">`t.cs` をコンパイルして出力ファイル `t.exe` とビルド `t2.cs` を作成し、モジュール出力ファイル `mymodule.netmodule` を作成します。</span><span class="sxs-lookup"><span data-stu-id="09fbe-129">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="09fbe-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="09fbe-130">See also</span></span>

- [<span data-ttu-id="09fbe-131">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="09fbe-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="09fbe-132">フレンド アセンブリ</span><span class="sxs-lookup"><span data-stu-id="09fbe-132">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
- [<span data-ttu-id="09fbe-133">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="09fbe-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
