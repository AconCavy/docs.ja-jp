---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: dd98b45d75ff421dc81666ed47695132a49bfa3a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524482"
---
# <a name="-addmodule"></a><span data-ttu-id="08475-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="08475-102">-addmodule</span></span>
<span data-ttu-id="08475-103">指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="08475-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08475-104">構文</span><span class="sxs-lookup"><span data-stu-id="08475-104">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="08475-105">引数</span><span class="sxs-lookup"><span data-stu-id="08475-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="08475-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="08475-106">Required.</span></span> <span data-ttu-id="08475-107">メタデータは含まれるが、アセンブリ マニフェストは含まれないファイルのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="08475-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="08475-108">ファイル名に空白が含まれる場合は、名前を二重引用符 ("") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="08475-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08475-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="08475-109">Remarks</span></span>  
 <span data-ttu-id="08475-110">`fileList` パラメーターで指定するファイルは、`-target:module` オプションを使用して作成するか、`-target:module` と同等の別のコンパイラを使用して作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08475-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="08475-111">`-addmodule` で追加したモジュールはすべて、実行時に出力ファイルと同じディレクトリに置かれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="08475-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="08475-112">つまり、コンパイル時には任意のディレクトリからモジュールを指定できますが、実行時にはアプリケーション ディレクトリにこのモジュールが置かれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="08475-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="08475-113">そうでない場合、<xref:System.TypeLoadException> エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="08475-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="08475-114">`-addmodule` で `-target:module` 以外の [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) オプションを (暗黙的または明示的に) 指定すると、`-addmodule` に渡すファイルはプロジェクトのアセンブリの一部になります。</span><span class="sxs-lookup"><span data-stu-id="08475-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="08475-115">`-addmodule` で追加された 1 つ以上のファイルを含む出力ファイルを実行するには、アセンブリが必要です。</span><span class="sxs-lookup"><span data-stu-id="08475-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="08475-116">アセンブリが含まれるファイルからメタデータをインポートするには、[-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="08475-116">Use [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08475-117">`-addmodule` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="08475-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08475-118">例</span><span class="sxs-lookup"><span data-stu-id="08475-118">Example</span></span>  
 <span data-ttu-id="08475-119">モジュールは、次のコード例で作成されます。</span><span class="sxs-lookup"><span data-stu-id="08475-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="08475-120">次のコードにより、モジュールの型がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="08475-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="08475-121">`t1` を実行すると、`802` が出力されます。</span><span class="sxs-lookup"><span data-stu-id="08475-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08475-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="08475-122">See also</span></span>

- [<span data-ttu-id="08475-123">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="08475-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="08475-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08475-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="08475-125">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08475-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="08475-126">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="08475-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
