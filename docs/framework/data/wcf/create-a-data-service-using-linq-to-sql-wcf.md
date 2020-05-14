---
title: '方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: cde5b9903a1fd164ce106a6a408ac4bb79976642
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802286"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="379d6-102">方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="379d6-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="379d6-103">WCF Data Services は、エンティティ データをデータ サービスとして公開します。</span><span class="sxs-lookup"><span data-stu-id="379d6-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="379d6-104">リフレクション プロバイダーでは、<xref:System.Linq.IQueryable%601> の実装を返すメンバーを公開するクラスに基づいたデータ モデルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="379d6-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="379d6-105">データ ソース内のデータに更新を加えるには、これらのクラスも <xref:System.Data.Services.IUpdatable> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="379d6-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="379d6-106">詳細については、「[Data Services プロバイダー](data-services-providers-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="379d6-106">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="379d6-107">このトピックでは、リフレクション プロバイダーを使用して Northwind サンプル データベースにアクセスする LINQ to SQL クラスを作成する方法と、これらのデータ クラスに基づくデータ サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="379d6-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="379d6-108">LINQ to SQL クラスをプロジェクトに追加するには</span><span class="sxs-lookup"><span data-stu-id="379d6-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="379d6-109">Visual Basic または C# アプリケーションから、 **[プロジェクト]** メニューの **[追加]**  >  **[新しい項目]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="379d6-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="379d6-110">**[LINQ to SQL クラス]** テンプレートをクリックします。</span><span class="sxs-lookup"><span data-stu-id="379d6-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="379d6-111">名前を「**Northwind.dbml**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="379d6-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="379d6-112">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="379d6-112">Click **Add**.</span></span>

     <span data-ttu-id="379d6-113">Northwind.dbml ファイルがプロジェクトに追加され、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開きます。</span><span class="sxs-lookup"><span data-stu-id="379d6-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="379d6-114">**サーバー エクスプローラー**または**データベース エクスプローラー**で、Northwind の下にある **[テーブル]** を展開して、`Customers` テーブルをオブジェクト リレーショナル デザイナー (O/R デザイナー) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="379d6-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="379d6-115">`Customer` エンティティ クラスが作成され、デザイン サーフェイスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="379d6-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="379d6-116">`Orders` テーブル、`Order_Details` テーブル、および `Products` テーブルに対して手順 6 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="379d6-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="379d6-117">LINQ to SQL クラスを表す新しい .dbml ファイルを右クリックして、 **[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="379d6-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="379d6-118"><xref:System.Data.Linq.DataContext> クラス (この場合は `NorthwindDataContext`) から継承するクラスの部分クラス定義を含む Northwind.cs という新しい分離コード ページが作成されます。</span><span class="sxs-lookup"><span data-stu-id="379d6-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="379d6-119">Northwind.cs コード ファイルの内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="379d6-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="379d6-120">このコードでは、<xref:System.Data.Linq.DataContext> と、および LINQ to SQL によって生成されたデータ クラスを拡張して、リフレクション プロバイダーを実装します。</span><span class="sxs-lookup"><span data-stu-id="379d6-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="379d6-121">LINQ to SQL ベースのデータ モデルを使用してデータ サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="379d6-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="379d6-122">**ソリューション エクスプローラー**で、ASP.NET プロジェクトの名前を右クリックし、 **[追加]**  >  **[新しい項目]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="379d6-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="379d6-123">**[新しい項目の追加]** ダイアログ ボックスで、 **[Web]** カテゴリの **[WCF Data Service]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="379d6-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Visual Studio 2015 の WCF Data Service 項目テンプレート](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="379d6-125">**WCF Data Service** テンプレートは Visual Studio 2015 で使用できますが、Visual Studio 2017 以降では使用できません。</span><span class="sxs-lookup"><span data-stu-id="379d6-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="379d6-126">サービスの名前を指定して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="379d6-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="379d6-127">Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="379d6-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="379d6-128">既定では、コード エディターのウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="379d6-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="379d6-129">データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindDataContext`) で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="379d6-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="379d6-130">データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="379d6-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="379d6-131">指定した 3 つのエンティティ セットのリソースへのクライアント アクセスが承認されます。</span><span class="sxs-lookup"><span data-stu-id="379d6-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="379d6-132">Web ブラウザーを使用して Northwind.svc データ サービスをテストするには、トピック「[Web ブラウザーからサービスへのアクセス](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="379d6-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="379d6-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="379d6-133">See also</span></span>

- [<span data-ttu-id="379d6-134">方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="379d6-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="379d6-135">方法: リフレクション プロバイダーを使用してデータ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="379d6-135">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="379d6-136">Data Services プロバイダー</span><span class="sxs-lookup"><span data-stu-id="379d6-136">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
