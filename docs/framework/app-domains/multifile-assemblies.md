---
title: マルチファイル アセンブリ
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
ms.openlocfilehash: 2a70e45d50763cf99c55cf08600c3c816b4043b7
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644216"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="94600-102">マルチファイル アセンブリ</span><span class="sxs-lookup"><span data-stu-id="94600-102">Multifile assemblies</span></span>

<span data-ttu-id="94600-103">コマンド ライン コンパイラまたは Visual C++ で Visual Studio を使って、.NET Framework をターゲットとするマルチファイル アセンブリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="94600-103">You can create multifile assemblies that target the .NET Framework using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="94600-104">アセンブリ内の 1 つのファイルには、アセンブリ マニフェストが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="94600-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="94600-105">アプリケーションを起動するアセンブリには、`Main` メソッドや `WinMain` メソッドなどのエントリ ポイントも含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="94600-105">An assembly that starts an application must also contain an entry point, such as a `Main` or `WinMain` method.</span></span>

<span data-ttu-id="94600-106">たとえば、2 つのコード モジュール *Client.cs* と *Stringer.cs* を含むアプリケーションがあるものとします。</span><span class="sxs-lookup"><span data-stu-id="94600-106">For example, suppose you have an application that contains two code modules, *Client.cs* and *Stringer.cs*.</span></span> <span data-ttu-id="94600-107">*Stringer.cs* は、*Client.cs* 内のコードによって参照される `myStringer` 名前空間を作成します。</span><span class="sxs-lookup"><span data-stu-id="94600-107">*Stringer.cs* creates the `myStringer` namespace that is referenced by the code in *Client.cs*.</span></span> <span data-ttu-id="94600-108">*Client.cs* には、アプリケーションのエントリ ポイントである `Main` メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="94600-108">*Client.cs* contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="94600-109">この例では、2 つのコード モジュールをコンパイルし、さらにアプリケーションを起動するアセンブリ マニフェストを含む 3 番目のファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="94600-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="94600-110">アセンブリ マニフェストは、*Client* モジュールと *Stringer* モジュールの両方を参照します。</span><span class="sxs-lookup"><span data-stu-id="94600-110">The assembly manifest references both the *Client* and *Stringer* modules.</span></span>

> [!NOTE]
> <span data-ttu-id="94600-111">アセンブリに複数のコード モジュールがある場合でも、マルチファイル アセンブリが持つことのできるエントリ ポイントは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="94600-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="94600-112">マルチファイル アセンブリを作成するのにはいくつかの理由があります。</span><span class="sxs-lookup"><span data-stu-id="94600-112">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="94600-113">異なる言語で記述されたモジュールを結合するため。</span><span class="sxs-lookup"><span data-stu-id="94600-113">To combine modules written in different languages.</span></span> <span data-ttu-id="94600-114">これは、マルチファイル アセンブリを作成する最も一般的な理由です。</span><span class="sxs-lookup"><span data-stu-id="94600-114">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="94600-115">使用頻度の低い型を、必要なときにだけダウンロードされるモジュールに入れることにより、アプリケーションのダウンロードを最適化するため。</span><span class="sxs-lookup"><span data-stu-id="94600-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="94600-116">Microsoft Internet Explorer で `<object>` タグを使ってダウンロードされるアプリケーションを作成する場合は、マルチファイル アセンブリを作成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="94600-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="94600-117">このシナリオでは、コード モジュールとは別に、アセンブリ マニフェストだけを含むファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="94600-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="94600-118">Internet Explorer は、最初にアセンブリ マニフェストをダウンロードした後、ワーカー スレッドを作成して、追加のモジュールまたは必要なアセンブリをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="94600-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="94600-119">アセンブリ マニフェストが含まれるファイルがダウンロードしている間、Internet Explorer はユーザー入力に応答できません。</span><span class="sxs-lookup"><span data-stu-id="94600-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="94600-120">アセンブリ マニフェストを含むファイルが小さいほど、Internet Explorer が応答しない時間が短くなります。</span><span class="sxs-lookup"><span data-stu-id="94600-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="94600-121">複数の開発者が記述したコード モジュールを結合するため。</span><span class="sxs-lookup"><span data-stu-id="94600-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="94600-122">開発者ごとに各コード モジュールをアセンブリにコンパイルすることもできますが、そうすると、すべてのモジュールがマルチファイル アセンブリに収められている場合であれば公開されない一部の型が強制的に公開されることがあります。</span><span class="sxs-lookup"><span data-stu-id="94600-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="94600-123">アセンブリを作成した後は、アセンブリ マニフェスト (以降アセンブリ) を含むファイルに署名したり、ファイルとアセンブリに厳密な名前を付けて、グローバル アセンブリ キャッシュに配置したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="94600-123">Once you create the assembly, you can sign the file that contains the assembly manifest, and hence the assembly, or you can give the file and the assembly a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="94600-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="94600-124">See also</span></span>

- [<span data-ttu-id="94600-125">方法: マルチファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="94600-125">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="94600-126">アセンブリを使用したプログラム</span><span class="sxs-lookup"><span data-stu-id="94600-126">Program with assemblies</span></span>](../../standard/assembly/index.md)
