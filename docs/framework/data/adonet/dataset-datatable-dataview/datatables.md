---
title: DataTables
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: 12255f738dea0a4713389e599468d1a7fab67d23
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784693"
---
# <a name="datatables"></a><span data-ttu-id="286cc-102">DataTables</span><span class="sxs-lookup"><span data-stu-id="286cc-102">DataTables</span></span>
<span data-ttu-id="286cc-103"><xref:System.Data.DataSet> は、テーブル、リレーションシップ、および制約のコレクションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="286cc-103">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="286cc-104">ADO.NET では、<xref:System.Data.DataTable> は **DataSet** 内のテーブルを表すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="286cc-104">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="286cc-105">**DataTable** は、1 つのメモリ内のリレーショナル データ テーブルを表します。このテーブルのデータは、そのデータが存在する .NET ベース アプリケーションのローカル データですが、**DataAdapter** を使用して Microsoft SQL Server などのデータ ソースから読み込むこともできます。詳細については、「[DataAdapter からの DataSet の読み込み](../populating-a-dataset-from-a-dataadapter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="286cc-105">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="286cc-106">**DataTable** クラスは、.NET Framework クラス ライブラリ内の **System.Data** 名前空間のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="286cc-106">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="286cc-107">**DataTable** は、単独でも **DataSet** のメンバーとしても作成および使用できます。また、**DataTable** オブジェクトは、<xref:System.Data.DataView> などの他の .NET Framework オブジェクトからも使用できます。</span><span class="sxs-lookup"><span data-stu-id="286cc-107">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="286cc-108">**DataSet** 内のテーブルのコレクションには、**DataSet** オブジェクトの **Tables** プロパティを使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="286cc-108">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="286cc-109">テーブルのスキーマ (構造) は、列と制約で表されます。</span><span class="sxs-lookup"><span data-stu-id="286cc-109">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="286cc-110">**DataTable** のスキーマは、<xref:System.Data.DataColumn> オブジェクト共に <xref:System.Data.ForeignKeyConstraint> および <xref:System.Data.UniqueConstraint> オブジェクトを使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="286cc-110">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="286cc-111">テーブルの列は、データ ソースの列に割り当てたり、式で算出された値を格納したり、格納されている値を自動的にインクリメントしたり、主キー値を格納したりできます。</span><span class="sxs-lookup"><span data-stu-id="286cc-111">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="286cc-112">**DataTable** には、スキーマだけでなく、データを格納して順序付けるための行も必要です。</span><span class="sxs-lookup"><span data-stu-id="286cc-112">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="286cc-113"><xref:System.Data.DataRow> クラスは、テーブルに格納される実際のデータを表します。</span><span class="sxs-lookup"><span data-stu-id="286cc-113">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="286cc-114">**DataRow** およびそのプロパティとメソッドを使用して、テーブル内のデータを取得、評価、および操作できます。</span><span class="sxs-lookup"><span data-stu-id="286cc-114">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="286cc-115">行内のデータがアクセスされて変更されると、**DataRow** オブジェクトには、現在の状態と元の状態が維持されます。</span><span class="sxs-lookup"><span data-stu-id="286cc-115">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="286cc-116">テーブル間で 1 つ以上の列を関連付け、テーブル間の親子のリレーションシップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="286cc-116">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="286cc-117">**DataTable** オブジェクト間のリレーションシップを作成するには、<xref:System.Data.DataRelation> を使用します。</span><span class="sxs-lookup"><span data-stu-id="286cc-117">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="286cc-118">**DataRelation** オブジェクトを使用すると、特定の行に関連付けられた子の行または親の行を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="286cc-118">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="286cc-119">詳しくは、「[DataRelation の追加](adding-datarelations.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="286cc-119">For more information, see [Adding DataRelations](adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="286cc-120">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="286cc-120">In This Section</span></span>  
 [<span data-ttu-id="286cc-121">DataTable の作成</span><span class="sxs-lookup"><span data-stu-id="286cc-121">Creating a DataTable</span></span>](creating-a-datatable.md)  
 <span data-ttu-id="286cc-122">**DataTable** を作成し、それを **DataSet** に追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="286cc-122">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="286cc-123">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="286cc-123">DataTable Schema Definition</span></span>](datatable-schema-definition.md)  
 <span data-ttu-id="286cc-124">**DataColumn** オブジェクトと制約の作成および使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="286cc-124">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="286cc-125">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="286cc-125">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="286cc-126">テーブル内のデータを追加、変更、および削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="286cc-126">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="286cc-127">**DataTable** イベントを使用してテーブル内のデータが変更されたかどうかを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="286cc-127">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="286cc-128">DataTable イベントの処理</span><span class="sxs-lookup"><span data-stu-id="286cc-128">Handling DataTable Events</span></span>](handling-datatable-events.md)  
 <span data-ttu-id="286cc-129">列値が変更された場合や行が追加または削除された場合のイベントなど、**DataTable** で使用できるイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="286cc-129">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="286cc-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="286cc-130">Related Sections</span></span>  
 [<span data-ttu-id="286cc-131">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="286cc-131">ADO.NET</span></span>](../index.md)  
 <span data-ttu-id="286cc-132">ADO.NET のアーキテクチャとコンポーネントについて説明し、ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="286cc-132">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="286cc-133">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="286cc-133">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="286cc-134">テーブル間のリレーションシップを作成する方法も含め、ADO.NET の **DataSet** について説明します。</span><span class="sxs-lookup"><span data-stu-id="286cc-134">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="286cc-135">**Constraint** オブジェクトの参照情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="286cc-135">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="286cc-136">**DataColumn** オブジェクトの参照情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="286cc-136">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="286cc-137">**DataSet** オブジェクトの参照情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="286cc-137">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="286cc-138">**DataTable** オブジェクトの参照情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="286cc-138">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="286cc-139">クラス ライブラリの概要</span><span class="sxs-lookup"><span data-stu-id="286cc-139">Class Library Overview</span></span>](../../../../standard/class-library-overview.md)  
 <span data-ttu-id="286cc-140">**System** 名前空間やその下位レベルの名前空間 **System.Data** が含まれる .NET Framework クラス ライブラリの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="286cc-140">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286cc-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="286cc-141">See also</span></span>

- [<span data-ttu-id="286cc-142">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="286cc-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
