---
title: DataView オブジェクトの作成 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: bd39b40864703b6bb24c2cc6590787562f3f4f98
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504155"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>DataView オブジェクトの作成 (LINQ to DataSet)
作成する 2 つの方法がある、 <xref:System.Data.DataView> LINQ to DataSet のコンテキストでします。 作成することができます、<xref:System.Data.DataView>から LINQ to DataSet クエリ経由で、 <xref:System.Data.DataTable>、型指定されていないか、型指定された作成することもできます<xref:System.Data.DataTable>します。 どちらの場合も、作成、<xref:System.Data.DataView>のいずれかを使用して、<xref:System.Data.DataTableExtensions.AsDataView%2A>拡張メソッド。<xref:System.Data.DataView> LINQ to DataSet のコンテキストに直接構築可能ではありません。  
  
 <xref:System.Data.DataView> を作成した後に、Windows フォーム アプリケーションまたは ASP.NET アプリケーションの UI コントロールにバインドしたり、フィルターおよび並べ替えの設定を変更したりできます。  
  
 <xref:System.Data.DataView> は、インデックスを構築します。これにより、フィルター処理や並べ替えなど、インデックスを使用できる操作のパフォーマンスが大幅に向上します。 <xref:System.Data.DataView> のインデックスは、<xref:System.Data.DataView> の作成時に構築されるほか、並べ替えまたはフィルター処理の情報が変更されたときにも構築されます。 <xref:System.Data.DataView> を作成した後で、並べ替えまたはフィルター処理の情報を設定した場合、インデックスが最低でも 2 回 (<xref:System.Data.DataView> の作成時と、並べ替えまたはフィルターのプロパティの変更時) 構築されることになります。  
  
 フィルター処理と並べ替えの詳細については<xref:System.Data.DataView>を参照してください[DataView によるフィルター処理](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)と[DataView による並べ替え](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)します。  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>LINQ to DataSet クエリの結果からの DataView の作成  
 A<xref:System.Data.DataView>データセット クエリ結果の射影である場所に、LINQ の結果からオブジェクトを作成できる<xref:System.Data.DataRow>オブジェクト。 新しく作成される <xref:System.Data.DataView> は、その基となるクエリからのフィルター処理および並べ替え情報を継承します。  
  
> [!NOTE]
>  ほとんどの場合、フィルターに使用する式は、副作用のない確定的な式である必要があります。 また、並べ替えおよびフィルター処理は任意の回数実行されるため、特定の実行回数に依存するロジックが式に含まれないようにしてください。  
  
 匿名型を返すクエリまたは結合操作を実行するクエリからの <xref:System.Data.DataView> の作成はサポートされていません。  
  
 <xref:System.Data.DataView> の作成に使用されるクエリでは、次のクエリ演算子のみがサポートされます。  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 場合、<xref:System.Data.DataView>データセット クエリを LINQ から作成されたが、<xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>メソッドは、クエリで呼び出す最後のメソッドである必要があります。 次の例は、作成にこれを<xref:System.Data.DataView>合計支払額別に並べ替えられたオンライン注文の。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 文字列ベースを使用することも<xref:System.Data.DataView.RowFilter%2A>と<xref:System.Data.DataView.Sort%2A>フィルターおよび並べ替えのプロパティを<xref:System.Data.DataView>がクエリから作成された後です。 この操作を行うと、クエリから継承された並べ替えおよびフィルター情報がクリアされます。 次の例では、作成、<xref:System.Data.DataView>で始まる姓でフィルター処理するデータセット クエリを LINQ からの '。 文字列ベースの <xref:System.Data.DataView.Sort%2A> プロパティは、姓を昇順に並べ替え、名を降順に並べ替えるように設定されています。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>DataTable からの DataView の作成  
 データセット クエリを LINQ から作成されるだけでなく、<xref:System.Data.DataView>からオブジェクトを作成できる、<xref:System.Data.DataTable>を使用して、<xref:System.Data.DataTableExtensions.AsDataView%2A>メソッド。  
  
 次の例では、<xref:System.Data.DataView> を SalesOrderDetail テーブルから作成した後、<xref:System.Windows.Forms.BindingSource> オブジェクトのデータ ソースとして設定します。 このオブジェクトは、<xref:System.Windows.Forms.DataGridView> コントロールのプロキシとして動作します。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 <xref:System.Data.DataView> から <xref:System.Data.DataTable> を作成した後、フィルターおよび並べ替えを設定できます。 次の例では、<xref:System.Data.DataView> を Contact テーブルから作成した後、姓を昇順に並べ替え、名を降順に並べ替えるための <xref:System.Data.DataView.Sort%2A> プロパティを設定します。  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 ただし、<xref:System.Data.DataView.RowFilter%2A> をクエリから作成した後に <xref:System.Data.DataView.Sort%2A> プロパティまたは <xref:System.Data.DataView> プロパティを設定する操作を行うと、パフォーマンスが低下します。なぜなら、<xref:System.Data.DataView> により、フィルター処理および並べ替え処理をサポートするためのインデックスが構築されるからです。 <xref:System.Data.DataView.RowFilter%2A> プロパティまたは <xref:System.Data.DataView.Sort%2A> プロパティを設定すると、データのインデックスが再構築され、アプリケーションのオーバーヘッドが増加してパフォーマンスの低下を招きます。 可能な場合は、<xref:System.Data.DataView> を最初に作成するときにフィルター処理および並べ替え情報を指定して、後で情報を変更するのを避けてください。  
  
## <a name="see-also"></a>関連項目

- [データ バインディングと LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [DataView によるフィルター処理](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)
- [DataView による並べ替え](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
