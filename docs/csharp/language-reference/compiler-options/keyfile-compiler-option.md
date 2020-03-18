---
title: -keyfile (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bf271cc6b6887e930911071d4603b51daed55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970262"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="fecfc-102">-keyfile (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="fecfc-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="fecfc-103">暗号化キーを格納するファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="fecfc-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fecfc-104">構文</span><span class="sxs-lookup"><span data-stu-id="fecfc-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="fecfc-105">引数</span><span class="sxs-lookup"><span data-stu-id="fecfc-105">Arguments</span></span>  
  
|<span data-ttu-id="fecfc-106">用語</span><span class="sxs-lookup"><span data-stu-id="fecfc-106">Term</span></span>|<span data-ttu-id="fecfc-107">定義</span><span class="sxs-lookup"><span data-stu-id="fecfc-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="fecfc-108">厳密な名前のキーを格納するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="fecfc-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fecfc-109">解説</span><span class="sxs-lookup"><span data-stu-id="fecfc-109">Remarks</span></span>  
 <span data-ttu-id="fecfc-110">このオプションを指定すると、コンパイラは、指定したファイルからアセンブリ マニフェストに公開キーを挿入し、最終的なアセンブリに秘密キーで署名します。</span><span class="sxs-lookup"><span data-stu-id="fecfc-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="fecfc-111">キー ファイルを生成するには、コマンド ラインで「sn -k `file`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="fecfc-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="fecfc-112">**-target:module** を指定してコンパイルした場合は、キー ファイルの名前がモジュールに保持され、[-addmodule](./addmodule-compiler-option.md) でアセンブリをコンパイルすると作成されるアセンブリに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="fecfc-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="fecfc-113">また、暗号化情報を [-keycontainer](./keycontainer-compiler-option.md) でコンパイラに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="fecfc-113">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="fecfc-114">部分的に署名されたアセンブリを作成する場合は、[-delaysign](./delaysign-compiler-option.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="fecfc-114">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="fecfc-115">同じコンパイルで (コマンド ライン オプションまたはカスタム属性によって) -keyfile と -keycontainer を両方とも指定すると、コンパイラは最初にキー コンテナーを試します。</span><span class="sxs-lookup"><span data-stu-id="fecfc-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="fecfc-116">それが成功すると、アセンブリはキー コンテナーの情報で署名されます。</span><span class="sxs-lookup"><span data-stu-id="fecfc-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="fecfc-117">キー コンテナーが見つからない場合、コンパイラは -keyfile で指定されたファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="fecfc-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="fecfc-118">ファイルが検出された場合、アセンブリはキー ファイルの情報で署名され、キー情報はキー コンテナーにインストールされるため (sn -i と同様)、次のコンパイル時にはキー コンテナーが有効になります。</span><span class="sxs-lookup"><span data-stu-id="fecfc-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="fecfc-119">キー ファイルには公開キーだけが含まれる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fecfc-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="fecfc-120">詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../standard/assembly/create-use-strong-named.md)」および「[アセンブリへの遅延署名](../../../standard/assembly/delay-sign.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fecfc-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fecfc-121">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="fecfc-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="fecfc-122">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="fecfc-122">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="fecfc-123">**[署名]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fecfc-123">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="fecfc-124">**[厳密な名前のキー ファイルを選択してください]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="fecfc-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="fecfc-125">このコンパイラ オプションには、プログラムで <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A> を使ってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="fecfc-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fecfc-126">参照</span><span class="sxs-lookup"><span data-stu-id="fecfc-126">See also</span></span>

- [<span data-ttu-id="fecfc-127">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="fecfc-127">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="fecfc-128">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="fecfc-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
