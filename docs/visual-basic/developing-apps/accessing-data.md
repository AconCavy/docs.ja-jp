---
title: Visual Basic アプリケーションにおけるデータ アクセス
ms.date: 07/20/2015
helpviewer_keywords:
- data [Visual Basic]
- Visual Basic, data access
ms.assetid: 3086ab38-3be5-4b22-9385-7d0e16b04f6a
ms.openlocfilehash: c9094e1550ad837444b7670cf54226322583be79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387609"
---
# <a name="accessing-data-in-visual-basic-applications"></a><span data-ttu-id="86beb-102">Visual Basic アプリケーションにおけるデータ アクセス</span><span class="sxs-lookup"><span data-stu-id="86beb-102">Accessing data in Visual Basic applications</span></span>

<span data-ttu-id="86beb-103">Visual Basic には、データにアクセスするアプリケーションを開発する際に役立ついくつかの新機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="86beb-103">Visual Basic includes several new features to assist in developing applications that access data.</span></span> <span data-ttu-id="86beb-104">Windows アプリケーションのデータ バインド フォームは、[[データ ソース]](/visualstudio/data-tools/add-new-data-sources) ウィンドウからフォームに項目をドラッグすることにより作成できます。</span><span class="sxs-lookup"><span data-stu-id="86beb-104">Data-bound forms for Windows applications are created by dragging items from the [Data Sources Window](/visualstudio/data-tools/add-new-data-sources) onto the form.</span></span> <span data-ttu-id="86beb-105">データをコントロールにバインドするには、 **[データ ソース]** ウィンドウから既存のコントロールに項目をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="86beb-105">You bind controls to data by dragging items from the **Data Sources Window** onto existing controls.</span></span>

## <a name="related-sections"></a><span data-ttu-id="86beb-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="86beb-106">Related sections</span></span>

[<span data-ttu-id="86beb-107">Visual Studio でのデータへのアクセス</span><span class="sxs-lookup"><span data-stu-id="86beb-107">Accessing Data in Visual Studio</span></span>](/visualstudio/data-tools/)  
<span data-ttu-id="86beb-108">アプリケーションにデータ アクセス機能を取り込む方法について説明したページへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-108">Provides links to pages that discuss incorporating data access functionality into your applications.</span></span>

[<span data-ttu-id="86beb-109">.NET 用の Visual Studio データ ツール</span><span class="sxs-lookup"><span data-stu-id="86beb-109">Visual Studio data tools for .NET</span></span>](/visualstudio/data-tools/visual-studio-data-tools-for-dotnet)  
<span data-ttu-id="86beb-110">Visual Studio を使用して、データを操作するアプリケーションを作成する方法に関するページへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-110">Provides links to pages on creating applications that work with data, using Visual Studio.</span></span>

[<span data-ttu-id="86beb-111">LINQ</span><span class="sxs-lookup"><span data-stu-id="86beb-111">LINQ</span></span>](../programming-guide/language-features/linq/index.md)  
<span data-ttu-id="86beb-112">Visual Basic での LINQ の使用方法について説明するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-112">Provides links to topics that describe how to use LINQ with Visual Basic.</span></span>

[<span data-ttu-id="86beb-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="86beb-113">LINQ to SQL</span></span>](../../framework/data/adonet/sql/linq/index.md)  
<span data-ttu-id="86beb-114">[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="86beb-114">Provides information about [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="86beb-115">プログラミング例もあります。</span><span class="sxs-lookup"><span data-stu-id="86beb-115">Includes programming examples.</span></span>  

[<span data-ttu-id="86beb-116">Visual Studio の LINQ to SQL ツール</span><span class="sxs-lookup"><span data-stu-id="86beb-116">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
<span data-ttu-id="86beb-117">アプリケーションで [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) オブジェクト モデルを作成する方法に関するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-117">Provides links to topics about how to create a [LINQ to SQL](../../framework/data/adonet/sql/linq/index.md) object model in applications.</span></span>

[<span data-ttu-id="86beb-118">n 層アプリケーションでのデータセットの操作</span><span class="sxs-lookup"><span data-stu-id="86beb-118">Work with datasets in n-tier applications</span></span>](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)  
<span data-ttu-id="86beb-119">複数層データ アプリケーションを作成する方法に関するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-119">Provides links to topics about how to create multitiered data applications.</span></span>

[<span data-ttu-id="86beb-120">新しい接続の追加</span><span class="sxs-lookup"><span data-stu-id="86beb-120">Add new connections</span></span>](/visualstudio/data-tools/add-new-connections)  
<span data-ttu-id="86beb-121">Visual Studio で、デザイン時ツールを使用してアプリケーションをデータに接続する方法と、ADO.NET 接続オブジェクトを使用してアプリケーションをデータに接続する方法に関するページへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-121">Provides links to pages on connecting your application to data with design-time tools and ADO.NET connection objects, using Visual Studio.</span></span>

[<span data-ttu-id="86beb-122">Visual Studio のデータセット ツール</span><span class="sxs-lookup"><span data-stu-id="86beb-122">Dataset Tools in Visual Studio</span></span>](/visualstudio/data-tools/dataset-tools-in-visual-studio)  
<span data-ttu-id="86beb-123">データセットにデータを読み込む方法と、SQL ステートメントおよびストアド プロシージャを実行する方法を説明しているページへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-123">Provides links to pages describing how to load data into datasets and how to execute SQL statements and stored procedures.</span></span>  

[<span data-ttu-id="86beb-124">Visual Studio でのデータへのコントロールのバインド</span><span class="sxs-lookup"><span data-stu-id="86beb-124">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)  
<span data-ttu-id="86beb-125">データ バインド コントロールを使用して Windows フォームにデータを表示する方法について説明しているページへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-125">Provides links to pages that explain how to display data on Windows Forms through data-bound controls.</span></span>

[<span data-ttu-id="86beb-126">データセットのデータの編集</span><span class="sxs-lookup"><span data-stu-id="86beb-126">Edit Data in Datasets</span></span>](/visualstudio/data-tools/edit-data-in-datasets)  
<span data-ttu-id="86beb-127">データセットのデータ テーブルにあるデータを操作する方法について説明しているページへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-127">Provides links to pages describing how to manipulate the data in the data tables of a dataset.</span></span>  

[<span data-ttu-id="86beb-128">データセットのデータの検証</span><span class="sxs-lookup"><span data-stu-id="86beb-128">Validate data in datasets</span></span>](/visualstudio/data-tools/validate-data-in-datasets)  
<span data-ttu-id="86beb-129">列と行の変更時にデータセットに対する検証を追加する方法について説明しているページへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-129">Provides links to pages describing how to add validation to a dataset during column and row changes.</span></span>

[<span data-ttu-id="86beb-130">データをデータベースに保存する</span><span class="sxs-lookup"><span data-stu-id="86beb-130">Save data back to the database</span></span>](/visualstudio/data-tools/save-data-back-to-the-database)  
<span data-ttu-id="86beb-131">更新済みのデータをアプリケーションからデータベースに送信する方法について説明しているページへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="86beb-131">Provides links to pages explaining how to send updated data from an application to the database.</span></span>

[<span data-ttu-id="86beb-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="86beb-132">ADO.NET</span></span>](../../framework/data/adonet/index.md)  
<span data-ttu-id="86beb-133">.NET Framework プログラマにデータ アクセス サービスを公開する ADO.NET クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="86beb-133">Describes the ADO.NET classes, which expose data-access services to the .NET Framework programmer.</span></span>

[<span data-ttu-id="86beb-134">Office ソリューションにおけるデータ</span><span class="sxs-lookup"><span data-stu-id="86beb-134">Data in Office Solutions</span></span>](/visualstudio/vsto/data-in-office-solutions)  
<span data-ttu-id="86beb-135">Office ソリューションでデータを操作する方法を説明するページへのリンクを示します。スキーマ指向プログラミング、データ キャッシュ、およびサーバー側データ アクセスに関する説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="86beb-135">Contains links to pages that explain how data works in Office solutions, including information about schema-oriented programming, data caching, and server-side data access.</span></span>
