---
title: DataAdapter からの DataSet の読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: d2d7719c7f6c2cacd6d68ecae226673248bbd680
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149233"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>DataAdapter からの DataSet の読み込み
ADO.NET<xref:System.Data.DataSet>は、データ ソースとは無関係に一貫したリレーショナル プログラミング モデルを提供する、メモリ常駐型のデータ表現です。 `DataSet` はテーブル、制約、およびテーブル間のリレーションシップを含む完全なデータのセットを表します。 `DataSet` はデータ ソースとは独立しているため、 `DataSet` にはそのアプリケーションに固有のデータと複数のデータ ソースからのデータを含めることができます。 既存のデータ ソースとの対話は `DataAdapter`によって制御されます。  
  
 `SelectCommand` の `DataAdapter` プロパティは、データ ソースからデータを取得する `Command` オブジェクトです。 `InsertCommand`の `UpdateCommand`、 `DeleteCommand` 、 `DataAdapter` の各プロパティは、 `Command` のデータに対して行われた変更に基づいてデータ ソースのデータ更新を管理する `DataSet`オブジェクトです。 これらのプロパティの詳細については、「 [DataAdapter を使用したデータ ソースの更新](updating-data-sources-with-dataadapters.md)」を参照してください。  
  
 `Fill` の `DataAdapter` メソッドは、 `DataSet` の `SelectCommand` の結果を `DataAdapter`に設定するために使用します。 `Fill` は、その引数として、設定対象である `DataSet` と、 `DataTable` オブジェクト (つまり、 `DataTable` から返された行を格納する `SelectCommand`の名前) を受け取ります。  
  
> [!NOTE]
> `DataAdapter` を使用してテーブル全体を取得すると、特にテーブルの行数が多い場合は処理に時間がかかります。 データベースにアクセスし、データを検索して処理した後、そのデータをクライアントに転送するという時間のかかる処理が伴うためです。 また、テーブル全体をクライアントに取得しようとすると、サーバー上ですべての行がロックされます。 `WHERE` 句を使用して、クライアントから返される行数をできるだけ減らすことでパフォーマンスを向上させることができます。 また、 `SELECT` ステートメントで必要な列を明示的に指定するだけでもクライアントに返されるデータ量を減らすことができます。 それ以外の対策としては、一度に数百行など、行をバッチで取得し、クライアントが現在のバッチの処理を完了した時点で次のバッチを取得する方法も効果的です。  
  
 `Fill` メソッドは、 `DataReader` オブジェクトを暗黙的に使用して `DataSet`内でテーブルを作成するための列の名前と型、および `DataSet`内のテーブルの行を設定するためのデータを返します。 テーブルおよび列は、存在しない場合にのみ作成されます。それ以外の場合、 `Fill` には、既存の `DataSet` スキーマが使用されます。 列の種類は、ADO.NET の[「データ型マッピング](data-type-mappings-in-ado-net.md)」の表に従って .NET Framework 型として作成されます。 主キーは、データ ソースおよび`DataAdapter`に存在しない限り作成されません **。**`MissingSchemaAction` は`MissingSchemaAction`**に設定されています。**`AddWithKey`. `Fill` はテーブルに主キーがあることがわかると、主キー列の値がデータ ソースから返された主キー列の値と一致する行について、データ ソースから返されたデータで `DataSet` 内のデータを上書きします。 主キーが見つからない場合は、 `DataSet`のテーブルの末尾にデータを追加します。 `Fill`は、データを設定するときに存在する可能性のあるマッピング`DataSet`を使用します (「[データアダプタ データ テーブル」および「データ列マッピング](dataadapter-datatable-and-datacolumn-mappings.md)」を参照)。  
  
> [!NOTE]
> `SelectCommand` が OUTER JOIN の結果を返す場合、 `DataAdapter` は、生成される `PrimaryKey` に `DataTable`値を設定しません。 自分で `PrimaryKey` を定義して、重複行が正しく解決されるようにする必要があります。 詳細については、「[主キーの定義](./dataset-datatable-dataview/defining-primary-keys.md)」を参照してください。  
  
 次のコード サンプルでは、Microsoft SQL Server の <xref:System.Data.SqlClient.SqlDataAdapter> データベースへの <xref:System.Data.SqlClient.SqlConnection> を使用する `Northwind` のインスタンスを作成し、 <xref:System.Data.DataTable> 内の `DataSet` に顧客リストを読み込みます。 <xref:System.Data.SqlClient.SqlConnection> コンストラクターに渡される SQL ステートメントおよび <xref:System.Data.SqlClient.SqlDataAdapter> 引数は、 <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> の <xref:System.Data.SqlClient.SqlDataAdapter>プロパティを作成するために使用されます。  
  
## <a name="example"></a>例  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim queryString As String = _  
  "SELECT CustomerID, CompanyName FROM dbo.Customers"  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  queryString, connection)  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
> このサンプル コードでは、 `Connection`の開始と終了を明示的に行っていません。 `Fill` メソッドは、接続がまだ開いていないことを認識すると `Connection` が使用している `DataAdapter` を暗黙的に開きます。 `Fill` が接続を開いた場合は、 `Fill` の終了時に Fill が接続を終了します。 これにより、 `Fill` や `Update`などの単一の操作を扱う場合にコードを簡略化できます。 これに対し、開いている接続を必要とする複数の操作を実行する場合は、 `Open` の `Connection`メソッドを明示的に呼び出し、データ ソースに対する操作の実行後に `Close` の `Connection`メソッドを呼び出すことでアプリケーションのパフォーマンスを改善できます。 リソースを解放して他のクライアント アプリケーションが使用できるようにするために、データ ソースへの接続を開いたままにする時間は最小限にすることをお勧めします。  
  
## <a name="multiple-result-sets"></a>複数結果セット  
 `DataAdapter` は複数の結果セットを検出すると、 `DataSet`に複数のテーブルを作成します。 これらのテーブルには、Table0 のように、"Table" で始まるインクリメンタル既定名 Table*N*が割り当てられます。 テーブル名を引数として `Fill` メソッドに渡すと、TableName0 を表す "TableName" で始まるインクリメンタル既定名 TableName*N*が割り当てられます。  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>複数の DataAdapter からの DataSet の読み込み  
 オブジェクトの任意`DataAdapter`の数を`DataSet`使用できます。 それぞれの `DataAdapter` で 1 つ以上の `DataTable` オブジェクトにデータを格納し、関連するデータ ソースに更新を反映させることができます。 `DataRelation` に対して `Constraint` オブジェクトおよび `DataSet` オブジェクトを部分的に追加できるため、複数の異なるデータ ソースから取得したデータを関連付けることができます。 たとえば、Microsoft SQL Server データベース、OLE DB を通じて公開される IBM DB2 データベース、および XML をストリーム転送するデータ ソースからのデータを `DataSet` に含めることができます。 1 つ以上の `DataAdapter` オブジェクトを使用して、各データ ソースとの通信を行うことができます。  
  
### <a name="example"></a>例  
 次のコード サンプルでは、Microsoft SQL Server 2000 の `Northwind` データベースおよび Microsoft Access の `Northwind` データベースから、それぞれ顧客リストと注文リストを取得します。 取得したテーブルを `DataRelation`で関連付けて、顧客および対応する注文の一覧を表示します。 オブジェクトの詳細`DataRelation`については、「[データリレーションシップの追加](./dataset-datatable-dataview/adding-datarelations.md)」および「[データリレーションシップのナビゲート](./dataset-datatable-dataview/navigating-datarelations.md)」を参照してください。  
  
```vb  
' Assumes that customerConnection is a valid SqlConnection object.  
' Assumes that orderConnection is a valid OleDbConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", customerConnection)  
  
Dim ordAdapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SELECT * FROM Orders", orderConnection)  
  
Dim customerOrders As DataSet = New DataSet()  
custAdapter.Fill(customerOrders, "Customers")  
ordAdapter.Fill(customerOrders, "Orders")  
  
Dim relation As DataRelation = _  
  customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustomerID"), _
  customerOrders.Tables("Orders").Columns("CustomerID"))  
  
Dim pRow, cRow As DataRow  
For Each pRow In customerOrders.Tables("Customers").Rows  
  Console.WriteLine(pRow("CustomerID").ToString())  
  
  For Each cRow In pRow.GetChildRows(relation)  
    Console.WriteLine(vbTab & cRow("OrderID").ToString())  
  Next  
Next  
```  
  
```csharp  
// Assumes that customerConnection is a valid SqlConnection object.  
// Assumes that orderConnection is a valid OleDbConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", customerConnection);  
OleDbDataAdapter ordAdapter = new OleDbDataAdapter(  
  "SELECT * FROM Orders", orderConnection);  
  
DataSet customerOrders = new DataSet();  
  
custAdapter.Fill(customerOrders, "Customers");  
ordAdapter.Fill(customerOrders, "Orders");  
  
DataRelation relation = customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustomerID"],  
  customerOrders.Tables["Orders"].Columns["CustomerID"]);  
  
foreach (DataRow pRow in customerOrders.Tables["Customers"].Rows)  
{  
  Console.WriteLine(pRow["CustomerID"]);  
   foreach (DataRow cRow in pRow.GetChildRows(relation))  
    Console.WriteLine("\t" + cRow["OrderID"]);  
}  
```  
  
## <a name="sql-server-decimal-type"></a>SQL Server の 10 進数型  
 既定では、.NET Framework データ型を`DataSet`使用してデータを格納します。 ほとんどのアプリケーションで、これらのデータ型を使用してデータ ソース情報を簡単に表示できます。 しかし、データ ソースのデータ型が SQL Server の 10 進数データ型または数値データ型の場合は、この表現によって問題が生じる場合があります。 .NET Framework`decimal`データ型では最大 28 桁の有効桁数を使用`decimal`できますが、SQL Server データ型では 38 桁の有効桁数を使用できます。 `SqlDataAdapter` が動作している間に、 `Fill` が、SQL Server の `decimal` フィールドの有効桁数が 28 文字を超えていると判断した場合、現在の行は `DataTable`に追加されません。 その場合は `FillError` イベントが発生するため、開発者は有効桁数の消失が発生していないかどうかを確認し、適切に対応できます。 イベントの`FillError`詳細については、「 [DataAdapter イベントの処理](handling-dataadapter-events.md)」を参照してください。 SQL Server の `decimal` 値を取得するために、 <xref:System.Data.SqlClient.SqlDataReader> オブジェクトを使用し、 <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> メソッドを呼び出すこともできます。  
  
 ADO.NET 2.0 では、<xref:System.Data.SqlTypes>の`DataSet`サポートが強化されました。 詳細については、「 [SqlTypes and the DataSet](./sql/sqltypes-and-the-dataset.md)」を参照してください。  
  
## <a name="ole-db-chapters"></a>OLE DB のチャプター  
 階層構造の行セット、つまりチャプター (OLE DB では `DBTYPE_HCHAPTER`型、ADO では `adChapter`型) を使用して `DataSet`の内容を格納できます。 <xref:System.Data.OleDb.OleDbDataAdapter> が `Fill` が動作している間にチャプター列を検出すると、そのチャプター列のための `DataTable` を作成し、チャプターから取得した列と行をこのテーブルに格納します。 チャプター列用に作成されたテーブルには、親テーブルの名前とチャプター列の名前の両方を使用した "*ParentTableNameChapteredColumnName*" 形式の名前が割り当てられます。 `DataSet` にチャプター列の名前と一致するテーブルが既に存在する場合は、現在のテーブルにチャプター データが格納されます。 既存のテーブルにチャプター内の列と一致する列が存在しない場合は、新しい列が追加されます。  
  
 `DataSet` 内のテーブルにチャプター列のデータを格納する前に、親テーブルと子テーブルの両方に 1 つの整数列を追加し、親列を自動インクリメントに設定し、両方のテーブルに追加された列を使用して `DataRelation` を作成すると、階層構造の行セットを形成している親テーブルと子テーブルの間にリレーションが作成されます。 追加されたリレーションには親テーブルの名前とチャプター列の名前を使用した "*ParentTableNameChapterColumnName*" 形式の名前が割り当てられます。  
  
 関連付けられた列は、 `DataSet`だけに存在します。 そのデータ ソースからの次の Fill 操作を実行すると、変更を既存の行にマージするのではなく、テーブルに新しい行が追加されます。  
  
 `DataAdapter.Fill` を受け取る `DataTable`オーバーロードを使用した場合は、そのテーブルだけにデータが格納されます。 自動インクリメント整数列は、引き続きそのテーブルに追加されますが、子テーブルの作成、子テーブルへのデータの格納、およびリレーションの作成は行われません。  
  
 MSDataShape プロバイダーを使用して顧客リスト内の各顧客に対応するオーダー列を生成する例を次に示します。 チャプター列を生成した後で、1 つの `DataSet` 内にそのデータを格納します。  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=northwind")  
  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
  
Dim customers As DataSet = New DataSet()  
  
adapter.Fill(customers, "Customers")  
End Using  
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection("Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=(local);Integrated Security=SSPI;Initial Catalog=northwind"))  
{  
OleDbDataAdapter adapter = new OleDbDataAdapter("SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
}  
```  
  
 `Fill` 操作が完了すると、 `DataSet` に `Customers` と `CustomersOrders`の 2 つのテーブルが格納されます。 `CustomersOrders` はチャプター列を表します。 `Orders` という列が `Customers` テーブルに追加され、 `CustomersOrders` という列が `CustomersOrders` テーブルに追加されます。 `Orders` テーブルの `Customers` 列は、自動インクリメントに設定されます。 親テーブルである `DataRelation`テーブルに追加された列を使用して、 `CustomersOrders`という `Customers` が作成されます。 サンプル結果の一部を次の表に示します。  
  
### <a name="tablename-customers"></a>TableName: Customers  
  
|CustomerID|CompanyName|Orders|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Ana Trujillo Emparedados y helados|1|  
  
### <a name="tablename-customersorders"></a>TableName: CustomersOrders  
  
|CustomerID|OrderID|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](dataadapters-and-datareaders.md)
- [ADO.NET でのデータ型のマッピング](data-type-mappings-in-ado-net.md)
- [DbDataAdapter を使用したデータの変更](modifying-data-with-a-dbdataadapter.md)
- [複数のアクティブな結果セット (MARS)](./sql/multiple-active-result-sets-mars.md)
- [ADO.NET の概要](ado-net-overview.md)
