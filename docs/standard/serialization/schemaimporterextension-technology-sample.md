---
title: SchemaImporterExtension の技術サンプル
ms.date: 03/30/2017
ms.assetid: 3f5eb78f-0ef6-433a-b095-3a63b1ce0bc9
ms.openlocfilehash: d63461425fd0b3366d39892512577b0dd706de13
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490869"
---
# <a name="schemaimporterextension-technology-sample"></a><span data-ttu-id="3ea50-102">SchemaImporterExtension の技術サンプル</span><span class="sxs-lookup"><span data-stu-id="3ea50-102">SchemaImporterExtension Technology Sample</span></span>
[<span data-ttu-id="3ea50-103">サンプルのダウンロード</span><span class="sxs-lookup"><span data-stu-id="3ea50-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/SchemaImporterExtension.zip.exe)  
  
 <span data-ttu-id="3ea50-104">このサンプルでは、XML スキーマをインポートするときのコード生成を微調整する、<xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> のカスタム化を示します。</span><span class="sxs-lookup"><span data-stu-id="3ea50-104">This sample demonstrates a custom <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> that allows fine control over code generation when an XML schema is imported.</span></span> <span data-ttu-id="3ea50-105">このアプリケーションは、この拡張機能のビルド、登録および起動の方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3ea50-105">The application shows how to build, register and invoke this extension.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="3ea50-106">コマンド プロンプトを使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="3ea50-106">To build the sample using the command prompt</span></span>  
  
1. <span data-ttu-id="3ea50-107">コマンド プロンプト ウィンドウを開き、サンプルが格納されている、言語固有のサブディレクトリのいずれかに移動します。</span><span class="sxs-lookup"><span data-stu-id="3ea50-107">Open a Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="3ea50-108">コマンド ラインで「**msbuild.exe OrderSchemaImporterExtension.sln**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3ea50-108">Type **msbuild.exe OrderSchemaImporterExtension.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="3ea50-109">Visual Studio を使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="3ea50-109">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="3ea50-110">エクスプローラーを開き、サンプルが格納されている、言語固有のサブディレクトリのいずれかに移動します。</span><span class="sxs-lookup"><span data-stu-id="3ea50-110">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="3ea50-111">OrderSchemaImporterExtension.sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="3ea50-111">Double-click the icon for OrderSchemaImporterExtension.sln to open the file in Visual Studio.</span></span>  
  
3. <span data-ttu-id="3ea50-112">**[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ea50-112">On the **Build** menu, click **Build Solution**.</span></span>  
  
 <span data-ttu-id="3ea50-113">アプリケーションは、既定の \bin ディレクトリまたは \bin\Debug ディレクトリにビルドされます。</span><span class="sxs-lookup"><span data-stu-id="3ea50-113">The application will be built in the default \bin or \bin\Debug directory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="3ea50-114">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="3ea50-114">To run the sample</span></span>  
  
1. <span data-ttu-id="3ea50-115">コマンド プロンプトを使用して、新しい実行可能ファイルが格納されているディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="3ea50-115">Navigate to the directory containing the new executable, using the command prompt.</span></span>  
  
2. <span data-ttu-id="3ea50-116">コマンド ラインで**実行ファイル名**を入力します。</span><span class="sxs-lookup"><span data-stu-id="3ea50-116">Type **[exe name]** at the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ea50-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="3ea50-117">Remarks</span></span>  
 <span data-ttu-id="3ea50-118">サンプルのバイナリ ファイルを作成する方法およびサンプルを登録する手順の詳細については、ソース コード ファイルおよび build.proj ファイル内のコメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ea50-118">For more information about sample binary creation and registration steps, see the comments in the source code and build.proj files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea50-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ea50-119">See also</span></span>

- <xref:System.CodeDom.CodeCompileUnit>
- <xref:System.CodeDom.CodeNamespace>
- <xref:System.CodeDom.CodeNamespaceImport>
- <xref:Microsoft.CSharp.CSharpCodeProvider>
- <xref:System.Xml.Serialization.IXmlSerializable>
- <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>
- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- <xref:System.Web.Services.Description>
- <xref:System.Web.Services.Discovery>
- <xref:System.Xml.Serialization>
- <xref:System.Uri>
- <xref:Microsoft.VisualBasic.VBCodeProvider>
- <xref:System.Web.Services.Description.WebReference>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
