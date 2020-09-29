---
title: 'チュートリアル: データの操作 (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: dbf18273e69ff0977f5d16ff179b8659865ef696
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164052"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="b60c4-102">チュートリアル: データの操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b60c4-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>

<span data-ttu-id="b60c4-103">このチュートリアルでは、データベースに対してデータの追加、変更、および削除を行う、基本の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] シナリオ全体を示します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="b60c4-104">顧客の追加、顧客名の変更、および注文の削除を行うため、サンプルの Northwind データベースのコピーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="b60c4-105">このチュートリアルは、Visual Basic 開発設定を使用して記述されています。</span><span class="sxs-lookup"><span data-stu-id="b60c4-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b60c4-106">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b60c4-106">Prerequisites</span></span>  

 <span data-ttu-id="b60c4-107">このチュートリアルの前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b60c4-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="b60c4-108">このチュートリアルでは、専用フォルダー ("c:\linqtest2") を使用してファイルを保持します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="b60c4-109">チュートリアルを開始する前に、このフォルダーを作成してください。</span><span class="sxs-lookup"><span data-stu-id="b60c4-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="b60c4-110">Northwind サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="b60c4-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="b60c4-111">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="b60c4-112">手順については、「[サンプル データベースのダウンロード](downloading-sample-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b60c4-112">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="b60c4-113">データベースをダウンロードしたら、northwnd.mdf ファイルを c:\linqtest2 フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
- <span data-ttu-id="b60c4-114">Northwind データベースから生成された Visual Basic コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="b60c4-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="b60c4-115">このファイルを生成するには、オブジェクト リレーショナル デザイナーまたは SQLMetal ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="b60c4-116">このチュートリアルは、SQLMetal ツールを使用して次のコマンド ラインで作成されています。</span><span class="sxs-lookup"><span data-stu-id="b60c4-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="b60c4-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="b60c4-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="b60c4-118">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b60c4-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b60c4-119">概要</span><span class="sxs-lookup"><span data-stu-id="b60c4-119">Overview</span></span>  

 <span data-ttu-id="b60c4-120">このチュートリアルは、主に次の 6 つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="b60c4-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="b60c4-121">Visual Studio で [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="b60c4-122">プロジェクトにデータベース コード ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="b60c4-123">新しい顧客オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="b60c4-124">顧客の連絡先名を変更します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="b60c4-125">注文を削除します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="b60c4-126">これらの変更を Northwind データベースに送信します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="b60c4-127">LINQ to SQL ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="b60c4-127">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="b60c4-128">最初のタスクに、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロジェクトをビルドおよび実行するために必要な参照を含む Visual Studio ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="b60c4-129">LINQ to SQL ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="b60c4-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="b60c4-130">Visual Studio で **[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-130">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="b60c4-131">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Visual Basic]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="b60c4-132">**[テンプレート]** ペインの **[コンソール アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="b60c4-133">**[プロジェクト名]** ボックスに「**LinqDataManipulationApp**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="b60c4-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="b60c4-135">LINQ の参照とディレクティブを追加する</span><span class="sxs-lookup"><span data-stu-id="b60c4-135">Adding LINQ References and Directives</span></span>  

 <span data-ttu-id="b60c4-136">このチュートリアルで使用するアセンブリは、既定ではプロジェクトにインストールされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b60c4-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="b60c4-137">`System.Data.Linq` がプロジェクトの参照 (**ソリューション エクスプローラー**で **[すべてのファイルを表示]** をクリックし、 **[参照設定]** ノードを展開) に表示されていない場合は、以下の手順に従って追加します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="b60c4-138">System.Data.Linq を追加するには</span><span class="sxs-lookup"><span data-stu-id="b60c4-138">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="b60c4-139">**ソリューション エクスプローラー**で、 **[参照設定]** を右クリックし、 **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="b60c4-140">**[参照の追加]** ダイアログ ボックスで、 **[.NET]** をクリックし、System.Data.Linq アセンブリをクリックします。次に、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b60c4-141">アセンブリがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b60c4-141">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="b60c4-142">コード エディターで、**Module1** の上に次のディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b60c4-143">プロジェクトに Northwind コード ファイルを追加する</span><span class="sxs-lookup"><span data-stu-id="b60c4-143">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="b60c4-144">これらの手順では、SQLMetal ツールを使用して Northwind サンプル データベースからコード ファイルを生成していることが前提です。</span><span class="sxs-lookup"><span data-stu-id="b60c4-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="b60c4-145">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b60c4-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b60c4-146">プロジェクトに Northwind コード ファイルを追加するには</span><span class="sxs-lookup"><span data-stu-id="b60c4-146">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="b60c4-147">**[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="b60c4-148">**[既存項目の追加]** ダイアログ ボックスで c:\linqtest2\northwind.vb に移動し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="b60c4-149">プロジェクトに northwind.vb ファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="b60c4-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="b60c4-150">データベース接続の設定</span><span class="sxs-lookup"><span data-stu-id="b60c4-150">Setting Up the Database Connection</span></span>  

 <span data-ttu-id="b60c4-151">最初に、データベースへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-151">First, test your connection to the database.</span></span> <span data-ttu-id="b60c4-152">データベースの名前 Northwnd に i の文字が欠けていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b60c4-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="b60c4-153">次の手順でエラーが生成された後で、northwind.vb ファイルを調べて、Northwind 部分クラスのスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="b60c4-154">データベース接続を設定してテストするには</span><span class="sxs-lookup"><span data-stu-id="b60c4-154">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="b60c4-155">`Sub Main` に次のコードを入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b60c4-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. <span data-ttu-id="b60c4-156">この時点でアプリケーションをテストするには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="b60c4-157">**コンソール** ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="b60c4-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="b60c4-158">**コンソール** ウィンドウで Enter キーを押すか、Visual Studio の **[デバッグ]** メニューの **[デバッグの停止]** をクリックして、アプリケーションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b60c4-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="b60c4-159">新しいエンティティの作成</span><span class="sxs-lookup"><span data-stu-id="b60c4-159">Creating a New Entity</span></span>  

 <span data-ttu-id="b60c4-160">新しいエンティティを作成する手順は簡単です。</span><span class="sxs-lookup"><span data-stu-id="b60c4-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="b60c4-161">`Customer` キーワードを使用してオブジェクト (`New` など) を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b60c4-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="b60c4-162">以降のセクションでは、ローカル キャッシュのみに変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="b60c4-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="b60c4-163">このチュートリアルの終盤で <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すまで、変更内容はデータベースに送信されません。</span><span class="sxs-lookup"><span data-stu-id="b60c4-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="b60c4-164">新しい Customer エンティティ オブジェクトを追加するには</span><span class="sxs-lookup"><span data-stu-id="b60c4-164">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="b60c4-165">次のコードを `Customer` 内の `Console.ReadLine` の前に追加することで、新しい `Sub Main` を作成します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="b60c4-166">F5 キーを押してソリューションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="b60c4-167">結果は、以下のようにコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b60c4-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="b60c4-168">新しい行は結果に表示されません。</span><span class="sxs-lookup"><span data-stu-id="b60c4-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="b60c4-169">新しいデータは、まだデータベースに送信されていません。</span><span class="sxs-lookup"><span data-stu-id="b60c4-169">The new data has not yet been submitted to the database.</span></span>  
  
3. <span data-ttu-id="b60c4-170">**コンソール** ウィンドウで Enter キーを押して、デバッグを停止します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="b60c4-171">エンティティの更新</span><span class="sxs-lookup"><span data-stu-id="b60c4-171">Updating an Entity</span></span>  

 <span data-ttu-id="b60c4-172">以降の手順では、`Customer` オブジェクトを取得し、そのプロパティの 1 つを変更します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="b60c4-173">顧客の名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="b60c4-173">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="b60c4-174">`Console.ReadLine()` の前に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="b60c4-175">エンティティの削除</span><span class="sxs-lookup"><span data-stu-id="b60c4-175">Deleting an Entity</span></span>  

 <span data-ttu-id="b60c4-176">同じ顧客オブジェクトを使用して、最初の注文を削除できます。</span><span class="sxs-lookup"><span data-stu-id="b60c4-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="b60c4-177">行間のリレーションシップを切断し、データベースから行を削除する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="b60c4-178">行を削除するには</span><span class="sxs-lookup"><span data-stu-id="b60c4-178">To delete a row</span></span>  
  
- <span data-ttu-id="b60c4-179">`Console.ReadLine()` の直前に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="b60c4-180">変更内容のデータベースへの送信</span><span class="sxs-lookup"><span data-stu-id="b60c4-180">Submitting Changes to the Database</span></span>  

 <span data-ttu-id="b60c4-181">最後の手順は、オブジェクトの作成、更新、および削除を実際にデータベースに送信するために必要です。</span><span class="sxs-lookup"><span data-stu-id="b60c4-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="b60c4-182">この手順を行わないと、変更はローカルのみに留まり、クエリの結果には反映されません。</span><span class="sxs-lookup"><span data-stu-id="b60c4-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="b60c4-183">データベースに変更内容を送信するには</span><span class="sxs-lookup"><span data-stu-id="b60c4-183">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="b60c4-184">`Console.ReadLine` の直前に次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="b60c4-185">変更内容の送信前と送信後の変化を示すために、次のコードを (`SubmitChanges` の後に) 挿入します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. <span data-ttu-id="b60c4-186">F5 キーを押してソリューションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="b60c4-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="b60c4-187">次のようにコンソール ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b60c4-187">The console window appears as follows:</span></span>  
  
    ```console
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. <span data-ttu-id="b60c4-188">**コンソール** ウィンドウで Enter キーを押して、デバッグを停止します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b60c4-189">変更内容を送信して新しい顧客を追加した後で、このソリューションを再度実行することはできません。同じ顧客を再度追加できないためです。</span><span class="sxs-lookup"><span data-stu-id="b60c4-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="b60c4-190">ソリューションを再度実行するには、追加する顧客 ID の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="b60c4-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b60c4-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="b60c4-191">See also</span></span>

- [<span data-ttu-id="b60c4-192">チュートリアルによる学習</span><span class="sxs-lookup"><span data-stu-id="b60c4-192">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
