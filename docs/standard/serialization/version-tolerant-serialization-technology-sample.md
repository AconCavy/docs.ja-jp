---
title: バージョン間の耐性があるシリアル化に対応する技術サンプル
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 317a47d46b839417e01eed9deca2459a96aaa201
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960780"
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="baf43-102">バージョン間の耐性があるシリアル化に対応する技術サンプル</span><span class="sxs-lookup"><span data-stu-id="baf43-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="baf43-103">サンプルのダウンロード</span><span class="sxs-lookup"><span data-stu-id="baf43-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="baf43-104">このサンプルでは、.NET でのバージョン間の耐性があるシリアル化に対応する機能を示します。</span><span class="sxs-lookup"><span data-stu-id="baf43-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="baf43-105">このサンプルでは、バージョンの異なる複数の <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> を使用するアプリケーションをビルドし、データをシリアル化および逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="baf43-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="baf43-106">さまざまなバージョンがありますが、このアプリケーションではシームレスに処理できます。</span><span class="sxs-lookup"><span data-stu-id="baf43-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="baf43-107">詳細については、「[Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md)」(バージョン トレラントなシリアル化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="baf43-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="baf43-108">コマンド プロンプトを使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="baf43-108">To build the sample using the command prompt</span></span>  
  
1. <span data-ttu-id="baf43-109">コマンド プロンプト ウィンドウを表示し、サンプルの使用言語に対応するサブディレクトリ (V1 Application または V2 Application の下) に移動します。</span><span class="sxs-lookup"><span data-stu-id="baf43-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2. <span data-ttu-id="baf43-110">コマンド ラインに「**msbuild.exe \<ver> application.sln**」と入力します (この \<ver> は v1 または v2 です)。</span><span class="sxs-lookup"><span data-stu-id="baf43-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="baf43-111">Visual Studio を使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="baf43-111">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="baf43-112">エクスプローラーを開き、サンプルが格納されている、言語固有のサブディレクトリのいずれかに移動します。</span><span class="sxs-lookup"><span data-stu-id="baf43-112">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="baf43-113">前の手順で選択したディレクトリの V1 Application サブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="baf43-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3. <span data-ttu-id="baf43-114">V1 Application.sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="baf43-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4. <span data-ttu-id="baf43-115">**[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="baf43-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5. <span data-ttu-id="baf43-116">V2 Application サブディレクトリに移動し、前の 2 つの手順を実行して、V2 Application をビルドします。</span><span class="sxs-lookup"><span data-stu-id="baf43-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="baf43-117">各アプリケーションは、既定で、それぞれのプロジェクト ディレクトリの \bin または \bin\Debug サブディレクトリにビルドされます。</span><span class="sxs-lookup"><span data-stu-id="baf43-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="baf43-118">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="baf43-118">To run the sample</span></span>  
  
1. <span data-ttu-id="baf43-119">コマンド プロンプト ウィンドウで、サンプル アプリケーションをビルドしたときに選択した言語に対応する、言語固有のサブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="baf43-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2. <span data-ttu-id="baf43-120">コマンド ラインに「**runme.cmd**」と入力し、両方のアプリケーションを一度に実行します。</span><span class="sxs-lookup"><span data-stu-id="baf43-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="baf43-121">または、新しい実行可能ファイルが格納されているディレクトリに移動し、これらを順に実行します。</span><span class="sxs-lookup"><span data-stu-id="baf43-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="baf43-122">このサンプルでは、コンソール アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="baf43-122">The sample builds console applications.</span></span> <span data-ttu-id="baf43-123">出力を表示するには、コマンド プロンプト ウィンドウでこれらを起動し、実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="baf43-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf43-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="baf43-124">See also</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.IO.FileStream>
