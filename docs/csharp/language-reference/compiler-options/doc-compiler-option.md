---
title: -doc (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: 01ea71f3de9e30abe25184e38a59f3707b54bd5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "73422973"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="75299-102">-doc (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="75299-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="75299-103">**-doc** オプションを使用すると、XML ファイル内にドキュメント コメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="75299-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75299-104">構文</span><span class="sxs-lookup"><span data-stu-id="75299-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="75299-105">引数</span><span class="sxs-lookup"><span data-stu-id="75299-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="75299-106">XML の出力ファイル。コンパイルのソース コード ファイルのコメントが入力されます。</span><span class="sxs-lookup"><span data-stu-id="75299-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75299-107">解説</span><span class="sxs-lookup"><span data-stu-id="75299-107">Remarks</span></span>  
 <span data-ttu-id="75299-108">ソース コード ファイルで、次の項目の前にあるドキュメント コメントを処理し、XML ファイルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="75299-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="75299-109">[クラス](../keywords/class.md)、[デリゲート](../builtin-types/reference-types.md#the-delegate-type)、[インターフェイス](../keywords/interface.md)などのユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="75299-109">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="75299-110">フィールド、[イベント](../keywords/event.md)、[プロパティ](../../programming-guide/classes-and-structs/using-properties.md)、メソッドなどのメンバー</span><span class="sxs-lookup"><span data-stu-id="75299-110">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="75299-111">Main を含むソース コード ファイルが最初に XML に出力されます。</span><span class="sxs-lookup"><span data-stu-id="75299-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="75299-112">生成された .xml ファイルで [IntelliSense](/visualstudio/ide/using-intellisense) 機能を使用するには、サポートするアセンブリの名前と .xml ファイル名を同じにして、その .xml ファイルをアセンブリと同じディレクトリに置きます。</span><span class="sxs-lookup"><span data-stu-id="75299-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="75299-113">これで、アセンブリが Visual Studio プロジェクトで参照されると、.xml ファイルも同様に検出されます。</span><span class="sxs-lookup"><span data-stu-id="75299-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="75299-114">詳細については、[コード コメントの追加](/visualstudio/ide/reference/generate-xml-documentation-comments)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75299-114">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="75299-115">[-target:module](./target-module-compiler-option.md) でコンパイルしない限り、`file` には \<assembly>\</assembly> タグが追加されます。コンパイルの出力ファイルのアセンブリ マニフェストを含むファイルの名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="75299-115">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75299-116">-doc オプションは、すべての入力ファイル (プロジェクトの設定で設定された場合、そのプロジェクト内のすべてのファイル) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="75299-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="75299-117">特定のファイルまたはコードの特定のセクションについて、ドキュメントのコメントに関する警告を無効にするには、[#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="75299-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="75299-118">コードのコメントからドキュメントを生成する方法については、「[ドキュメント コメント用の推奨タグ](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75299-118">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="75299-119">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="75299-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="75299-120">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="75299-120">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="75299-121">**[ビルド]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="75299-121">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="75299-122">**[XML ドキュメント ファイル]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="75299-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="75299-123">このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="75299-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75299-124">参照</span><span class="sxs-lookup"><span data-stu-id="75299-124">See also</span></span>

- [<span data-ttu-id="75299-125">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="75299-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="75299-126">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="75299-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
