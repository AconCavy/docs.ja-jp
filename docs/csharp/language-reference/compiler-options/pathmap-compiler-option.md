---
title: -pathmap (C# コンパイラ オプション)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606630"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="2309a-102">-pathmap (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="2309a-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="2309a-103">**-pathmap** コンパイラ オプションは、コンパイラによるソース パス名出力への物理パスのマップ方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="2309a-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="2309a-104">構文</span><span class="sxs-lookup"><span data-stu-id="2309a-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="2309a-105">引数</span><span class="sxs-lookup"><span data-stu-id="2309a-105">Arguments</span></span>

 <span data-ttu-id="2309a-106">`path1` 現在の環境でのソース ファイルへの完全なパス</span><span class="sxs-lookup"><span data-stu-id="2309a-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="2309a-107">`sourcePath1` 出力ファイルにおいて `path1` の代わりに使用されるソース パス。</span><span class="sxs-lookup"><span data-stu-id="2309a-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="2309a-108">複数のマップされるソース パスを指定するには、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="2309a-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="2309a-109">解説</span><span class="sxs-lookup"><span data-stu-id="2309a-109">Remarks</span></span>

<span data-ttu-id="2309a-110">コンパイラは、次の理由でその出力にソース パスを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="2309a-110">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="2309a-111"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute> が省略可能なパラメーターに適用される場合、引数はソース パスに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="2309a-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="2309a-112">ソース パスは、PDB ファイルに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="2309a-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="2309a-113">PDB ファイルのパスは、PE (ポータブル実行可能) ファイルに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="2309a-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="2309a-114">このオプションは、コンパイラが実行されるコンピューター上の各物理パスを、出力ファイルに書き込まれる必要がある対応するパスにマップします。</span><span class="sxs-lookup"><span data-stu-id="2309a-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="2309a-115">例</span><span class="sxs-lookup"><span data-stu-id="2309a-115">Example</span></span>

<span data-ttu-id="2309a-116">ディレクトリ `t.cs`C:**work\\tests\\ 内の**  をコンパイルし、出力ではそのディレクトリを **\publish** にマップします。</span><span class="sxs-lookup"><span data-stu-id="2309a-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="2309a-117">参照</span><span class="sxs-lookup"><span data-stu-id="2309a-117">See also</span></span>

- [<span data-ttu-id="2309a-118">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="2309a-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2309a-119">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="2309a-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
