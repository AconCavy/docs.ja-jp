---
title: -target:winmdobj (C# コンパイラ オプション)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204492"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="ced0f-102">-target:winmdobj (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="ced0f-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="ced0f-103">**-target:winmdobj** コンパイラ オプションを使用すると、コンパイラは、Windows ランタイム バイナリ (.winmd) ファイルに変換できる .winmdobj 中間ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="ced0f-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="ced0f-104">.winmd ファイルは、マネージド言語プログラムだけでなく JavaScript および C++ プログラムでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="ced0f-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ced0f-105">構文</span><span class="sxs-lookup"><span data-stu-id="ced0f-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="ced0f-106">解説</span><span class="sxs-lookup"><span data-stu-id="ced0f-106">Remarks</span></span>  
 <span data-ttu-id="ced0f-107">**winmdobj** 設定は、中間モジュールが必要であることをコンパイラに通知します。</span><span class="sxs-lookup"><span data-stu-id="ced0f-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="ced0f-108">これに対し、Visual Studio が C# クラス ライブラリを .winmdobj ファイルとしてコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ced0f-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="ced0f-109">.winmdobj ファイルは <xref:Microsoft.Build.Tasks.WinMDExp> エクスポート ツールで送信され、Windows メタデータ ファイル (.winmd) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ced0f-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="ced0f-110">.winmd ファイルには、元のライブラリのコードと WinMD メタデータの両方が含まれています。メタデータは、JavaScript または C++、および Windows ランタイムで使用されます。</span><span class="sxs-lookup"><span data-stu-id="ced0f-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="ced0f-111">**-target:winmdobj** コンパイラ オプションを使用してコンパイルされたファイルの出力は、WimMDExp エクスポート ツール用の入力としてのみ使用するように設計されています。 .winmdobj ファイル自体は直接参照されません。</span><span class="sxs-lookup"><span data-stu-id="ced0f-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="ced0f-112">[-out](./out-compiler-option.md) オプションを使用しない限り、出力ファイル名は最初の入力ファイルと同じになります。</span><span class="sxs-lookup"><span data-stu-id="ced0f-112">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="ced0f-113">[Main](../../programming-guide/main-and-command-args/index.md) メソッドは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ced0f-113">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="ced0f-114">コマンド プロンプトで -target:winmdobj オプションを指定すると、次の **-out** または [-target:module](./target-module-compiler-option.md) オプションまでのすべてのファイルが、Windows プログラムを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ced0f-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="ced0f-115">Windows ストア アプリ用に Visual Studio IDE でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="ced0f-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="ced0f-116">**ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ced0f-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="ced0f-117">**[アプリケーション]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="ced0f-117">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="ced0f-118">**[出力の種類]** リストで、 **[WinMD ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ced0f-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="ced0f-119">**[WinMD ファイル]** オプションは、Windows 8.x Store アプリ テンプレートでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ced0f-119">The **WinMD File** option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="ced0f-120">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ced0f-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ced0f-121">例</span><span class="sxs-lookup"><span data-stu-id="ced0f-121">Example</span></span>  
 <span data-ttu-id="ced0f-122">次のコマンドは .winmdobj 中間ファイルに `filename.cs` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ced0f-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ced0f-123">参照</span><span class="sxs-lookup"><span data-stu-id="ced0f-123">See also</span></span>

- [<span data-ttu-id="ced0f-124">-target (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="ced0f-124">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="ced0f-125">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="ced0f-125">C# Compiler Options</span></span>](./index.md)
