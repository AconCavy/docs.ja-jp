---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: a612a68cffd927f3e360406cca6d9daae4f66c86
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775634"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="adfd2-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="adfd2-102">-moduleassemblyname</span></span>
<span data-ttu-id="adfd2-103">このモジュールが一部となるアセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="adfd2-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adfd2-104">構文</span><span class="sxs-lookup"><span data-stu-id="adfd2-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="adfd2-105">引数</span><span class="sxs-lookup"><span data-stu-id="adfd2-105">Arguments</span></span>  
  
|<span data-ttu-id="adfd2-106">用語</span><span class="sxs-lookup"><span data-stu-id="adfd2-106">Term</span></span>|<span data-ttu-id="adfd2-107">定義</span><span class="sxs-lookup"><span data-stu-id="adfd2-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="adfd2-108">このモジュールが一部となるアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="adfd2-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adfd2-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="adfd2-109">Remarks</span></span>  
 <span data-ttu-id="adfd2-110">`-target:module` オプションが指定されている場合にのみ、コンパイラで `-moduleassemblyname` オプションが処理されます。</span><span class="sxs-lookup"><span data-stu-id="adfd2-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="adfd2-111">これにより、コンパイラでモジュールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="adfd2-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="adfd2-112">コンパイラによって作成されたモジュールは、`-moduleassemblyname` オプションで指定されたアセンブリに対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="adfd2-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="adfd2-113">モジュールを別のアセンブリに配置すると、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="adfd2-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="adfd2-114">`-moduleassemblyname` オプションは、次の条件に該当する場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="adfd2-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="adfd2-115">モジュール内のデータ型が、参照アセンブリの `Friend` 型にアクセスする必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="adfd2-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="adfd2-116">参照アセンブリに、モジュールをビルドするアセンブリへのフレンド アセンブリのアクセス権が付与されている場合。</span><span class="sxs-lookup"><span data-stu-id="adfd2-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="adfd2-117">モジュールの作成の詳細については、「[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adfd2-117">For more information about creating a module, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="adfd2-118">フレンド アセンブリの詳細については、「[フレンド アセンブリ](../../../standard/assembly/friend.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adfd2-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adfd2-119">`-moduleassemblyname` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド プロンプトからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="adfd2-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adfd2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="adfd2-120">See also</span></span>

- [<span data-ttu-id="adfd2-121">方法: マルチファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="adfd2-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="adfd2-122">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="adfd2-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="adfd2-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adfd2-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="adfd2-124">-main</span><span class="sxs-lookup"><span data-stu-id="adfd2-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="adfd2-125">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adfd2-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="adfd2-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="adfd2-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="adfd2-127">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="adfd2-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="adfd2-128">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="adfd2-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="adfd2-129">フレンド アセンブリ</span><span class="sxs-lookup"><span data-stu-id="adfd2-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
