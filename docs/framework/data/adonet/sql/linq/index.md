---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 4553be9eeab8792197503d0b1de872f4494277b6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634626"
---
# <a name="linq-to-sql"></a><span data-ttu-id="9c9d7-102">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9c9d7-102">LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="9c9d7-103">は .NET Framework バージョン3.5 のコンポーネントであり、リレーショナルデータをオブジェクトとして管理するためのランタイムインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-103">is a component of .NET Framework version 3.5 that provides a run-time infrastructure for managing relational data as objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c9d7-104">リレーショナル データは 2 次元テーブル (*リレーション*または*フラット ファイル*) のコレクションで表され、共通の列がテーブルを相互に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-104">Relational data appears as a collection of two-dimensional tables (*relations* or *flat files*), where common columns relate tables to each other.</span></span> <span data-ttu-id="9c9d7-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を効果的に使用するには、リレーショナル データベースの基本原則を理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-105">To use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectively, you must have some familiarity with the underlying principles of relational databases.</span></span>  
  
 <span data-ttu-id="9c9d7-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="9c9d7-107">アプリケーションが実行されると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-107">When the application runs, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates into SQL the language-integrated queries in the object model and sends them to the database for execution.</span></span> <span data-ttu-id="9c9d7-108">データベースから結果が返されると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はそれをプログラミング言語で操作できるオブジェクトに変換し直します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-108">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates them back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="9c9d7-109">通常、Visual Studio を使用する開発者は、オブジェクトリレーショナルデザイナーを使用します。これは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]の多くの機能を実装するためのユーザーインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-109">Developers using Visual Studio typically use the Object Relational Designer, which provides a user interface for implementing many of the features of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="9c9d7-110">このリリースの [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に含まれているドキュメントでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを構築するのに必要な基本的なビルド ブロック、プロセス、および手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-110">The documentation that is included with this release of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] describes the basic building blocks, processes, and techniques you need for building [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="9c9d7-111">また、特定の問題について Microsoft Docs を検索したり、 [LINQ フォーラム](https://go.microsoft.com/fwlink/?LinkId=76488)に参加したりすることもできます。このトピックでは、より複雑なトピックについて、専門家に詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-111">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="9c9d7-112">最後に、 [LINQ to SQL: リレーショナルデータのための .Net 統合言語クエリに](https://go.microsoft.com/fwlink/?LinkId=93205)関するホワイトペーパーでは、Visual Basic とC#コード例を使用して、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] テクノロジについて詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-112">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c9d7-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9c9d7-113">In This Section</span></span>  
 [<span data-ttu-id="9c9d7-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="9c9d7-114">Getting Started</span></span>](getting-started.md)  
 <span data-ttu-id="9c9d7-115">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の簡単な概要と、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して作業を始める方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-115">Provides a condensed overview of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] along with information about how to get started using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="9c9d7-116">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9c9d7-116">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="9c9d7-117">マップ、クエリ、更新、デバッグ、および同様のタスクを行う手順を示します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-117">Provides steps for mapping, querying, updating, debugging, and similar tasks.</span></span>  
  
 [<span data-ttu-id="9c9d7-118">参照</span><span class="sxs-lookup"><span data-stu-id="9c9d7-118">Reference</span></span>](reference.md)  
 <span data-ttu-id="9c9d7-119">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のさまざまな側面に関するリファレンス情報を示します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-119">Provides reference information about several aspects of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="9c9d7-120">SQL-CLR 型マッピング、標準クエリ演算子変換などのトピックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-120">Topics include SQL-CLR Type Mapping, Standard Query Operator Translation, and more.</span></span>  
  
 [<span data-ttu-id="9c9d7-121">サンプル</span><span class="sxs-lookup"><span data-stu-id="9c9d7-121">Samples</span></span>](samples.md)  
 <span data-ttu-id="9c9d7-122">Visual Basic とC#サンプルへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-122">Provides links to Visual Basic and C# samples.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9c9d7-123">関連セクション</span><span class="sxs-lookup"><span data-stu-id="9c9d7-123">Related Sections</span></span>  
 <span data-ttu-id="9c9d7-124">[統合言語クエリ (LINQ)- C# ](../../../../../csharp/programming-guide/concepts/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="9c9d7-124">[Language-Integrated Query (LINQ) - C#](../../../../../csharp/programming-guide/concepts/linq/index.md)</span></span>\
 <span data-ttu-id="9c9d7-125">の LINQ テクノロジの概要にC#ついて説明します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-125">Provides overviews of LINQ technologies in C#.</span></span>
 
 [<span data-ttu-id="9c9d7-126">統合言語クエリ (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c9d7-126">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="9c9d7-127">Visual Basic の LINQ テクノロジの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-127">Provides overviews of LINQ technologies in Visual Basic.</span></span>
  
 [<span data-ttu-id="9c9d7-128">LINQ</span><span class="sxs-lookup"><span data-stu-id="9c9d7-128">LINQ</span></span>](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="9c9d7-129">Visual Basic ユーザー向けの LINQ テクノロジについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-129">Describes LINQ technologies for Visual Basic users.</span></span>  
  
 [<span data-ttu-id="9c9d7-130">LINQ と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9c9d7-130">LINQ and ADO.NET</span></span>](../../linq-and-ado-net.md)  
 <span data-ttu-id="9c9d7-131">ADO.NET ポータルにリンクします。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-131">Links to the ADO.NET portal.</span></span>  
  
 <span data-ttu-id="9c9d7-132">[LINQ to SQL チュートリアル](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9c9d7-132">[LINQ to SQL Walkthroughs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))</span></span>  
 <span data-ttu-id="9c9d7-133">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のチュートリアルを一覧します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-133">Lists walkthroughs available for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="9c9d7-134">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="9c9d7-134">Downloading Sample Databases</span></span>](downloading-sample-databases.md)  
 <span data-ttu-id="9c9d7-135">ドキュメントで使用されるサンプル データベースをダウンロードする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-135">Describes how to download sample databases used in the documentation.</span></span>  
  
 <span data-ttu-id="9c9d7-136">[LinqDataSource Web サーバーコントロールの概要](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9c9d7-136">[LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))</span></span>  
 <span data-ttu-id="9c9d7-137"><xref:System.Web.UI.WebControls.LinqDataSource> コントロールが、ASP.NET データソースコントロールアーキテクチャを使用して、統合言語クエリ (LINQ) を Web 開発者に公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c9d7-137">Describes how the <xref:System.Web.UI.WebControls.LinqDataSource> control exposes Language-Integrated Query (LINQ) to Web developers through the ASP.NET data-source control architecture.</span></span>
