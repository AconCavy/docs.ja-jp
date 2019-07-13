---
title: SQL Server のインスタンスの列挙 (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: d6d76d677bcf7dfa7df632bde8de76401a46db05
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661886"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>SQL Server のインスタンスの列挙 (ADO.NET)
SQL Server には、現在のネットワーク内の SQL Server インスタンスを検索するアプリケーションが許可されます。 <xref:System.Data.Sql.SqlDataSourceEnumerator> クラスは、表示可能なすべてのサーバーに関する情報が含まれた <xref:System.Data.DataTable> を提供することで、アプリケーション開発者にこの情報を公開します。 これは、テーブルには、ユーザーが新しい接続を作成しようとしたときに指定された一覧と一致してで使用可能なすべてのサーバーを含むドロップダウン リストを展開するネットワークで使用できるサーバー インスタンスの一覧が含まれています返される、**接続。プロパティ** ダイアログ ボックス。 結果には一部のインスタンスが表示されないことがあります。  
  
> [!NOTE]
>  大半の Windows サービスと同様に、できるだけ少ない特権で SQL Browser サービスを実行することをお勧めします。 SQL Browser サービスの詳細および SQL Browser サービスの動作を管理する方法については、SQL Server オンライン ブックを参照してください。  
  
## <a name="retrieving-an-enumerator-instance"></a>列挙子インスタンスの取得  
 使用可能な SQL Server インスタンスに関する情報が含まれたテーブルを取得するには、まず、共有プロパティまたは静的プロパティである <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> プロパティを使用して列挙子を取得する必要があります。  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 静的なインスタンスを取得したら、使用可能なサーバーに関する情報が含まれた <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> を返す <xref:System.Data.DataTable> メソッドを呼び出すことができます。  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 このメソッド呼び出しから返されるテーブルには、次の列が含まれています。これらすべての列に `string` 値が含まれています。  
  
|Column|説明|  
|------------|-----------------|  
|**ServerName**|サーバーの名前。|  
|**InstanceName**|サーバー インスタンスの名前。 サーバーが既定のインスタンスとして実行されている場合は空白になります。|  
|**IsClustered**|サーバーがクラスターの一部になっているかどうかを示します。|  
|**Version**|サーバーのバージョン。 例えば:<br /><br /> -9.00.x (SQL Server 2005)<br />-   10.0.xx (SQL Server 2008)<br />-10.50.x (SQL Server 2008 R2)<br />-   11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>列挙の制約  
 使用可能なサーバーの一部が表示されないことがあります。 サーバーの一覧は、タイムアウトやネットワーク トラフィックなどの要因によって異なることがあります。 そのため、2 回続けて呼び出しても、呼び出しごとにリストが異なる可能性があります。 同じネットワーク上のサーバーのみがリストに表示されます。 通常、ブロードキャスト パケットはルーターを経由しません。そのため、特定のサーバーがリストに表示されないことがありますが、その状態はいつ呼び出しを行っても変わりません。  
  
 一覧に含まれているサーバーは、`IsClustered` やバージョンなどの追加情報を持っている場合も、持っていない場合もあります。 サーバーが持っている情報は、一覧が取得された方法によって異なります。 SQL Server ブラウザー サービスを介して一覧表示されるサーバーには、名前しか一覧表示しない Windows インフラストラクチャを介して検索されたサーバーより多くの詳細情報が含まれています。  
  
> [!NOTE]
>  サーバー列挙は、完全に信頼された環境で実行している場合にのみ利用できます。 部分的に信頼された環境で実行されているアセンブリは、<xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) アクセス許可を持っている場合でも、サーバー列挙を使用できません。  
  
 SQL Server の情報を提供する、 <xref:System.Data.Sql.SqlDataSourceEnumerator> SQL Browser という名前の外部 Windows サービスを利用しています。 このサービスは既定で有効になりますが、管理者がこのサービスをオフにしたり無効にしたりすると、サーバー インスタンスがこのクラスから見えなくなります。  
  
## <a name="example"></a>例  
 次のコンソール アプリケーションは、表示可能なすべての SQL Server インスタンスに関する情報を取得し、コンソール ウィンドウにその情報を表示します。  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [SQL Server と ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
