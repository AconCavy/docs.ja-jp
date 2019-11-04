---
title: '方法 : アプリケーションをローカライズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: 26c09e547205e7819ebb43d6e34b6e18d6d9ff98
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460837"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="d29b9-102">方法 : アプリケーションをローカライズする</span><span class="sxs-lookup"><span data-stu-id="d29b9-102">How to: Localize an Application</span></span>
<span data-ttu-id="d29b9-103">このチュートリアルでは、LocBaml ツールを使用して、ローカライズされたアプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d29b9-104">LocBaml ツールは、実稼働可能なアプリケーションではありません。</span><span class="sxs-lookup"><span data-stu-id="d29b9-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="d29b9-105">それはローカリゼーション API の一部を使用するサンプルとして提供されており、ローカリゼーション ツールを記述する方法を例示します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>   
## <a name="overview"></a><span data-ttu-id="d29b9-106">概要</span><span class="sxs-lookup"><span data-stu-id="d29b9-106">Overview</span></span>  
 <span data-ttu-id="d29b9-107">この説明では、アプリケーションのローカリゼーションの手順を段階を追って示します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="d29b9-108">最初に、翻訳されるテキストを抽出できるようにアプリケーションを準備します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="d29b9-109">テキストの翻訳後、翻訳されたテキストを元のアプリケーションの新しいコピーにマージします。</span><span class="sxs-lookup"><span data-stu-id="d29b9-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="d29b9-110">［要件］</span><span class="sxs-lookup"><span data-stu-id="d29b9-110">Requirements</span></span>  
 <span data-ttu-id="d29b9-111">この説明では、コマンドラインから実行するコンパイラである Microsoft build engine (MSBuild) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-111">Over the course of this discussion, you will use Microsoft build engine (MSBuild), which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="d29b9-112">また、プロジェクト ファイルを使用するよう指示されます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="d29b9-113">MSBuild とプロジェクトファイルの使用方法については、「[ビルドと配置](../app-development/building-and-deploying-wpf-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d29b9-113">For instructions on how to use MSBuild and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="d29b9-114">この説明のすべての例では、カルチャとして en-US (英語-米国) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="d29b9-115">別の言語をインストールしなくても、この例の手順全体の作業を行えます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a><span data-ttu-id="d29b9-116">サンプルのアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="d29b9-116">Create a Sample Application</span></span>  
 <span data-ttu-id="d29b9-117">このステップでは、ローカリゼーション用のアプリケーションを準備します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="d29b9-118">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のサンプルでは、この説明のコード サンプルで使用される HelloApp のサンプルが提供されています。</span><span class="sxs-lookup"><span data-stu-id="d29b9-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="d29b9-119">このサンプルを使用する場合は、 [LocBaml ツールサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)から [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="d29b9-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="d29b9-120">ローカリゼーションを開始するポイントまで、アプリケーションを開発します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="d29b9-121">プロジェクトファイルで開発言語を指定して、MSBuild がニュートラル言語リソースを格納するメインアセンブリとサテライトアセンブリ (.resources 拡張子を持つファイル) を生成するようにします。</span><span class="sxs-lookup"><span data-stu-id="d29b9-121">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="d29b9-122">HelloApp サンプルのプロジェクト ファイルは HelloApp.csproj です。</span><span class="sxs-lookup"><span data-stu-id="d29b9-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="d29b9-123">このファイルに、以下のように特定される開発言語があります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="d29b9-124">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルに UID を追加します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="d29b9-125">UID は、ファイルへの変更を追跡して、翻訳する必要がある項目を識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="d29b9-126">ファイルに Uid を追加するには、プロジェクトファイルで**updateuid**を実行します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="d29b9-127">**msbuild-t:updateuid helloapp.resources.dll**</span><span class="sxs-lookup"><span data-stu-id="d29b9-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="d29b9-128">不足している Uid または重複する Uid がないことを確認するには、 **checkuid**を実行します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="d29b9-129">**msbuild-helloapp.resources.dll checkuid**</span><span class="sxs-lookup"><span data-stu-id="d29b9-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="d29b9-130">**Updateuid**を実行した後、ファイルには uid が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="d29b9-131">たとえば、HelloApp の Pane1.xaml ファイルに、以下の内容があるはずです。</span><span class="sxs-lookup"><span data-stu-id="d29b9-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="d29b9-132">ニュートラル言語リソースのサテライト アセンブリを作成する</span><span class="sxs-lookup"><span data-stu-id="d29b9-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="d29b9-133">ニュートラル言語リソースのサテライト アセンブリを生成するようにアプリケーションを構成した後、アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="d29b9-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="d29b9-134">これにより、メイン アプリケーション アセンブリだけでなく、ローカリゼーションで LocBaml が必要とするニュートラル言語リソースのサテライト アセンブリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="d29b9-135">アプリケーションをビルドするには</span><span class="sxs-lookup"><span data-stu-id="d29b9-135">To build the application:</span></span>  
  
1. <span data-ttu-id="d29b9-136">Helloapp.resources.dll をコンパイルして、ダイナミックリンクライブラリ (DLL) を作成します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-136">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
     <span data-ttu-id="d29b9-137">**msbuild helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="d29b9-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="d29b9-138">新規作成されたメインのアプリケーション アセンブリ HelloApp.exe は、次のフォルダーに作成されます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="d29b9-139">新規作成されたニュートラル言語リソースのサテライト アセンブリ HelloApp.resources.dll は次のフォルダーに作成されます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="d29b9-140">LocBaml ツールをビルドする</span><span class="sxs-lookup"><span data-stu-id="d29b9-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="d29b9-141">LocBaml のビルドに必要なすべてのファイルは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] サンプルに配置されています。</span><span class="sxs-lookup"><span data-stu-id="d29b9-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="d29b9-142">C# [LocBaml ツールサンプル](https://go.microsoft.com/fwlink/?LinkID=160016)からファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d29b9-142">Download the C# files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
2. <span data-ttu-id="d29b9-143">ツールをビルドするには、コマンド ラインでプロジェクト ファイル (locbaml.csproj) を実行します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="d29b9-144">**msbuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="d29b9-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="d29b9-145">新しく作成された実行可能ファイル (locbaml.exe) を検索するには、bin \release ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="d29b9-146">例: C:\LocBaml\Bin\Release\locbaml.exe</span><span class="sxs-lookup"><span data-stu-id="d29b9-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="d29b9-147">LocBaml を実行するときに指定できるオプションは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d29b9-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="d29b9-148">**parse**または **-p:** Baml、リソース、または DLL ファイルを解析して、.csv または .txt ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-148">**parse** or **-p:** Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="d29b9-149">**generate**または **-g:** 翻訳されたファイルを使用して、ローカライズされたバイナリファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="d29b9-150">**out**または **-o** {*filedirectory*] **:** 出力ファイル名。</span><span class="sxs-lookup"><span data-stu-id="d29b9-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="d29b9-151">**culture**または **-cul** {*culture*] **:** 出力アセンブリのロケール。</span><span class="sxs-lookup"><span data-stu-id="d29b9-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="d29b9-152">**translation**または **-trans** {*translation. .csv*] **:** 翻訳またはローカライズされたファイル。</span><span class="sxs-lookup"><span data-stu-id="d29b9-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="d29b9-153">**asmpath**または **-asmpath:** {*filedirectory*] **:** [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] コードにカスタムコントロールが含まれている場合は、カスタムコントロールアセンブリに**asmpath**を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="d29b9-154">**nologo:** ロゴまたは著作権情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="d29b9-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="d29b9-155">**verbose:** 詳細モードの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d29b9-156">ツールの実行時にオプションの一覧が必要な場合は、「 **LocBaml** 」と入力し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="d29b9-157">LocBaml を使用してファイルを解析する</span><span class="sxs-lookup"><span data-stu-id="d29b9-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="d29b9-158">LocBaml ツールが作成されたので、これを使用して HelloApp.resources.dll を解析し、ローカライズするテキスト コンテンツを抽出できる状態になりました。</span><span class="sxs-lookup"><span data-stu-id="d29b9-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="d29b9-159">LocBaml.exe を、メインのアプリケーション アセンブリが作成された、アプリケーションの bin \debug フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d29b9-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="d29b9-160">サテライト アセンブリ ファイルを解析して、.csv ファイルとして出力を格納するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="d29b9-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="d29b9-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d29b9-162">入力ファイル HelloApp.resources.dll が LocBaml.exe と同じディレクトリに存在しない場合は、いずれかのファイルを移動して両方のファイルが同じディレクトリにあるようにします。</span><span class="sxs-lookup"><span data-stu-id="d29b9-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="d29b9-163">LocBaml を実行してファイルを解析する際、出力はコンマ区切り (.csv ファイル) またはタブ区切り (.txt ファイル) された 7 つのフィールドで構成されます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="d29b9-164">HelloApp.resources.dll の解析済みの .csv ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="d29b9-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="d29b9-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="d29b9-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="d29b9-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="d29b9-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="d29b9-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="d29b9-168">7 つのフィールドは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d29b9-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="d29b9-169">**BAML 名**。</span><span class="sxs-lookup"><span data-stu-id="d29b9-169">**BAML Name**.</span></span> <span data-ttu-id="d29b9-170">ソース言語のサテライト アセンブリに関する BAML リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="d29b9-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="d29b9-171">**リソース キー**。</span><span class="sxs-lookup"><span data-stu-id="d29b9-171">**Resource Key**.</span></span> <span data-ttu-id="d29b9-172">ローカライズされたリソースの識別子。</span><span class="sxs-lookup"><span data-stu-id="d29b9-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="d29b9-173">**カテゴリ**。</span><span class="sxs-lookup"><span data-stu-id="d29b9-173">**Category**.</span></span> <span data-ttu-id="d29b9-174">値の型です。</span><span class="sxs-lookup"><span data-stu-id="d29b9-174">The value type.</span></span> <span data-ttu-id="d29b9-175">「[ローカリゼーション属性とコメント」を](localization-attributes-and-comments.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="d29b9-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="d29b9-176">**読みやすさ**。</span><span class="sxs-lookup"><span data-stu-id="d29b9-176">**Readability**.</span></span> <span data-ttu-id="d29b9-177">ローカライザーによって値が読み取れるかどうか。</span><span class="sxs-lookup"><span data-stu-id="d29b9-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="d29b9-178">「[ローカリゼーション属性とコメント」を](localization-attributes-and-comments.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="d29b9-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="d29b9-179">**変更可能性**。</span><span class="sxs-lookup"><span data-stu-id="d29b9-179">**Modifiability**.</span></span> <span data-ttu-id="d29b9-180">ローカライザーによって値が変更できるかどうか。</span><span class="sxs-lookup"><span data-stu-id="d29b9-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="d29b9-181">「[ローカリゼーション属性とコメント」を](localization-attributes-and-comments.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="d29b9-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="d29b9-182">**コメント**。</span><span class="sxs-lookup"><span data-stu-id="d29b9-182">**Comments**.</span></span> <span data-ttu-id="d29b9-183">値をローカライズする方法を決定するための値の追加の説明。</span><span class="sxs-lookup"><span data-stu-id="d29b9-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="d29b9-184">「[ローカリゼーション属性とコメント」を](localization-attributes-and-comments.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="d29b9-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="d29b9-185">**値**。</span><span class="sxs-lookup"><span data-stu-id="d29b9-185">**Value**.</span></span> <span data-ttu-id="d29b9-186">目的のカルチャに翻訳するテキストの値。</span><span class="sxs-lookup"><span data-stu-id="d29b9-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="d29b9-187">次の表は、.csv ファイルの区切り記号付きの値にこれらのフィールドをマップする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d29b9-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="d29b9-188">BAML 名</span><span class="sxs-lookup"><span data-stu-id="d29b9-188">BAML name</span></span>|<span data-ttu-id="d29b9-189">リソース キー</span><span class="sxs-lookup"><span data-stu-id="d29b9-189">Resource key</span></span>|<span data-ttu-id="d29b9-190">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="d29b9-190">Category</span></span>|<span data-ttu-id="d29b9-191">読みやすさ</span><span class="sxs-lookup"><span data-stu-id="d29b9-191">Readability</span></span>|<span data-ttu-id="d29b9-192">変更可能性</span><span class="sxs-lookup"><span data-stu-id="d29b9-192">Modifiability</span></span>|<span data-ttu-id="d29b9-193">コメント</span><span class="sxs-lookup"><span data-stu-id="d29b9-193">Comments</span></span>|<span data-ttu-id="d29b9-194">[値]</span><span class="sxs-lookup"><span data-stu-id="d29b9-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="d29b9-195">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="d29b9-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="d29b9-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="d29b9-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="d29b9-197">Ignore</span><span class="sxs-lookup"><span data-stu-id="d29b9-197">Ignore</span></span>|<span data-ttu-id="d29b9-198">false</span><span class="sxs-lookup"><span data-stu-id="d29b9-198">FALSE</span></span>|<span data-ttu-id="d29b9-199">false</span><span class="sxs-lookup"><span data-stu-id="d29b9-199">FALSE</span></span>||<span data-ttu-id="d29b9-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="d29b9-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="d29b9-201">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="d29b9-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="d29b9-202">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="d29b9-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="d29b9-203">None</span><span class="sxs-lookup"><span data-stu-id="d29b9-203">None</span></span>|<span data-ttu-id="d29b9-204">true</span><span class="sxs-lookup"><span data-stu-id="d29b9-204">TRUE</span></span>|<span data-ttu-id="d29b9-205">true</span><span class="sxs-lookup"><span data-stu-id="d29b9-205">TRUE</span></span>||<span data-ttu-id="d29b9-206">Hello World</span><span class="sxs-lookup"><span data-stu-id="d29b9-206">Hello World</span></span>|
   |<span data-ttu-id="d29b9-207">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="d29b9-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="d29b9-208">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="d29b9-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="d29b9-209">None</span><span class="sxs-lookup"><span data-stu-id="d29b9-209">None</span></span>|<span data-ttu-id="d29b9-210">true</span><span class="sxs-lookup"><span data-stu-id="d29b9-210">TRUE</span></span>|<span data-ttu-id="d29b9-211">true</span><span class="sxs-lookup"><span data-stu-id="d29b9-211">TRUE</span></span>||<span data-ttu-id="d29b9-212">Goodbye World</span><span class="sxs-lookup"><span data-stu-id="d29b9-212">Goodbye World</span></span>|
  
   <span data-ttu-id="d29b9-213">**[コメント]** フィールドのすべての値に値が含まれていないことに注意してください。フィールドに値がない場合は、空になります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="d29b9-214">また、最初の行の項目は読み取りも変更もできず、**カテゴリ**値として "Ignore" が含まれていることにも注意してください。これらはすべて、値がローカライズ可能ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="d29b9-215">解析されたファイル内のローカライズ可能な項目の検出を容易にするため (特に大規模なファイルの場合)、**カテゴリ**、**読みやすさ**、**変更可能性**で項目を並べ替えたりフィルター処理したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="d29b9-216">たとえば、読み取りも変更もできない値をフィルター処理することができます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a><span data-ttu-id="d29b9-217">ローカライズ可能なコンテンツを翻訳する</span><span class="sxs-lookup"><span data-stu-id="d29b9-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="d29b9-218">抽出されたコンテンツを翻訳するために使用可能な任意のツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="d29b9-219">これを行うには、リソースを .csv ファイルに書き込み、Microsoft Excel で表示して、最後の列 (値) に変更を加える方法が適しています。</span><span class="sxs-lookup"><span data-stu-id="d29b9-219">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="d29b9-220">LocBaml を使用して新しい .resources.dll ファイルを生成する</span><span class="sxs-lookup"><span data-stu-id="d29b9-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="d29b9-221">LocBaml で HelloApp.resources.dll を解析して識別されたコンテンツは翻訳済みであり、元のアプリケーションにマージする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="d29b9-222">**Generate**または **-g**オプションを使用して、新しい .resources .dll ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="d29b9-223">新しい HelloApp.resources.dll ファイルを生成するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="d29b9-224">カルチャを en-US (/cul:en-US) としてマークします。</span><span class="sxs-lookup"><span data-stu-id="d29b9-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="d29b9-225">**LocBaml/generate Helloapp.resources.dll/trans: Hello. .csv/out: c:\/cul: en-US.**</span><span class="sxs-lookup"><span data-stu-id="d29b9-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d29b9-226">入力ファイル Hello.csv が実行可能ファイル LocBaml.exe と同じディレクトリに存在しない場合は、いずれかのファイルを移動して、両方のファイルが同じディレクトリにあるようにします。</span><span class="sxs-lookup"><span data-stu-id="d29b9-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="d29b9-227">C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll ディレクトリにある古い HelloApp.resources.dll ファイルを新規作成した HelloApp.resources.dll ファイルに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="d29b9-228">ここで "Hello World" と "Goodbye World" をアプリケーション内で翻訳する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="d29b9-229">別のカルチャに翻訳するには、翻訳先の言語のカルチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="d29b9-230">フランス語 (カナダ) に翻訳する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="d29b9-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="d29b9-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="d29b9-232">メイン アプリケーション アセンブリと同じアセンブリで、新しいサテライト アセンブリを格納するために、新しいカルチャ固有のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="d29b9-233">フランス語 (カナダ) のフォルダーは "fr-CA" となります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="d29b9-234">新しいフォルダーに生成されたサテライト アセンブリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="d29b9-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="d29b9-235">新しいサテライト アセンブリをテストするには、アプリケーションが実行するカルチャを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="d29b9-236">2 つの方法のいずれかでこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="d29b9-237">オペレーティングシステムの地域設定を変更します ([**スタート** &#124; **] コントロールパネル** &#124;の **[地域と言語] オプション**)。</span><span class="sxs-lookup"><span data-stu-id="d29b9-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="d29b9-238">アプリケーションで、次のコードを App.xaml.cs に追加します。</span><span class="sxs-lookup"><span data-stu-id="d29b9-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="d29b9-239">LocBaml を使用するためのヒント</span><span class="sxs-lookup"><span data-stu-id="d29b9-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="d29b9-240">カスタム コントロールを定義するすべての依存アセンブリを LocBaml のローカル ディレクトリにコピーするか、GAC にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="d29b9-241">これは、ローカライズ API がバイナリ XAML (BAML) を読み取るときに、依存アセンブリにアクセスできる必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="d29b9-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="d29b9-242">メインのアセンブリが署名済みの場合は、生成されたリソース DLL も読み込むために署名されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="d29b9-243">ローカライズされたリソースの DLL は、メインのアセンブリと同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d29b9-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a><span data-ttu-id="d29b9-244">次の内容</span><span class="sxs-lookup"><span data-stu-id="d29b9-244">What's Next</span></span>  
 <span data-ttu-id="d29b9-245">これで、LocBaml ツールの使用方法に関する基本的な知識が得られました。</span><span class="sxs-lookup"><span data-stu-id="d29b9-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="d29b9-246">UID を含むファイルを作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d29b9-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="d29b9-247">LocBaml ツールを使用することで、ローカライズ可能なコンテンツを抽出するファイルを解析できます。コンテンツを翻訳すると、翻訳済みのコンテンツをマージする .resources.dll ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="d29b9-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="d29b9-248">このトピックには、可能性のあるすべての詳細情報は含まれていませんが、LocBaml を使用してアプリケーションをローカライズするために必要な知識は得られました。</span><span class="sxs-lookup"><span data-stu-id="d29b9-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d29b9-249">関連項目</span><span class="sxs-lookup"><span data-stu-id="d29b9-249">See also</span></span>

- [<span data-ttu-id="d29b9-250">WPF のグローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="d29b9-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="d29b9-251">自動レイアウトの使用の概要</span><span class="sxs-lookup"><span data-stu-id="d29b9-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
