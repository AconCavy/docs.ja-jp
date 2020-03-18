---
title: -target (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: af7bd917f57c8752a2026fbb98aa8b22adc98db7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204513"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="12d12-102">-target (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="12d12-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="12d12-103">**-target** コンパイラ オプションは、次の 6 つの形式のいずれかで指定できます。</span><span class="sxs-lookup"><span data-stu-id="12d12-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="12d12-104">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="12d12-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="12d12-105">Windows 8.x Store アプリの .exe ファイルを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="12d12-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="12d12-106">/target:exe</span><span class="sxs-lookup"><span data-stu-id="12d12-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="12d12-107">.exe ファイルを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="12d12-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="12d12-108">/target:library</span><span class="sxs-lookup"><span data-stu-id="12d12-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="12d12-109">コード ライブラリを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="12d12-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="12d12-110">/target:module</span><span class="sxs-lookup"><span data-stu-id="12d12-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="12d12-111">モジュールを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="12d12-111">To create a module.</span></span>  
  
 [<span data-ttu-id="12d12-112">/target:winexe</span><span class="sxs-lookup"><span data-stu-id="12d12-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="12d12-113">Windows プログラムを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="12d12-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="12d12-114">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="12d12-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="12d12-115">.winmdobj 中間ファイルを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="12d12-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="12d12-116">**-target:module** を指定しない限り、 **-target** を使用すると、.NET Framework のアセンブリ マニフェストが出力ファイルに配置されます。</span><span class="sxs-lookup"><span data-stu-id="12d12-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="12d12-117">詳細については、「[.NET のアセンブリ](../../../standard/assembly/index.md)」と「[共通の属性](../../programming-guide/concepts/attributes/common-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12d12-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="12d12-118">アセンブリ マニフェストは、コンパイル中の最初の .exe 出力ファイルに配置されます。 .exe 出力ファイルがない場合には、最初の DLL ファイルに配置されます。</span><span class="sxs-lookup"><span data-stu-id="12d12-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="12d12-119">たとえば、次のコマンド ラインでは、マニフェストは `1.exe` に配置されます。</span><span class="sxs-lookup"><span data-stu-id="12d12-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="12d12-120">コンパイラの 1 回のコンパイルで作成されるアセンブリ マニフェストは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="12d12-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="12d12-121">コンパイルにおけるすべてのファイルの情報は、アセンブリ マニフェストに含まれます。</span><span class="sxs-lookup"><span data-stu-id="12d12-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="12d12-122">**-target:module** で作成されたもの以外のすべての出力ファイルには、アセンブリ マニフェストを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="12d12-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="12d12-123">コマンド ラインで複数の出力ファイルを生成する場合は、アセンブリ マニフェストを 1 つだけ作成できます。このアセンブリ マニフェストは、コマンド ラインで指定した最初の出力ファイルに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="12d12-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="12d12-124">最初の出力ファイル ( **-target:exe**、 **-target:winexe**、 **-target:library**、 **-target:module**) にかかわらず、同じコンパイルで生成された他の出力ファイルはすべてモジュール ( **-target:module**) でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="12d12-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="12d12-125">アセンブリを作成する場合は、<xref:System.CLSCompliantAttribute> 属性を使用して、コードのすべてまたは一部が CLS 準拠であることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="12d12-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="12d12-126">このコンパイラ オプションのプログラムによる設定の詳細については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12d12-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d12-127">参照</span><span class="sxs-lookup"><span data-stu-id="12d12-127">See also</span></span>

- [<span data-ttu-id="12d12-128">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="12d12-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="12d12-129">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="12d12-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="12d12-130">-subsystemversion (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="12d12-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
