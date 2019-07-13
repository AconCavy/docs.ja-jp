---
title: SQL Server でのスナップショット分離
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 0ff89f2d5ffa177b9413f6a2925bb05729e053a3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592893"
---
# <a name="snapshot-isolation-in-sql-server"></a>SQL Server でのスナップショット分離
スナップショット分離により、OLTP アプリケーションのコンカレンシーが向上しています。  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>スナップショット分離と行バージョン管理について  
 トランザクションごとに更新された行バージョンが保持されるスナップショット分離を有効にすると**tempdb**します。 一意のトランザクション シーケンス番号が各トランザクションを識別し、これらの一意の番号がそれぞれの行バージョン用に記録されます。 トランザクションは、シーケンス番号がトランザクションのシーケンス番号よりも前にある、最新の行バージョンを処理します。 トランザクションが開始された後で作成された最新の行バーションは、トランザクションにより無視されます。  
  
 "スナップショット" という用語は、トランザクション内のすべてのクエリが、トランザクションの開始時点のデータベースの状態に基づいて、データベースの同じバージョン、つまりスナップショットを参照するという事実を表しています。 ロックは、スナップショット トランザクション内の基になるデータ行やデータ ページでは取得されません。スナップショット トランザクションでは、先に開始されてまだ完了していないトランザクションによりブロックされることなく、他のトランザクションを実行できます。 データを変更するトランザクションは、データを読み取るトランザクションをブロックしません。また、データを読み取るトランザクションは、データを書き込むトランザクションをブロックしません。この理由は、通常、これらのトランザクションは SQL Server の既定の READ COMMITTED 分離レベルにあるためです。 また、ブロック不可の動作は、複雑なトランザクションのデッドロックの可能性を大幅に軽減します。  
  
 スナップショット分離では、オプティミスティック コンカレンシー モデルを使用します。 スナップショット トランザクションは、トランザクションの開始後に変更されたデータに対して変更をコミットしようとすると、このトランザクションがロールバックし、エラーになります。 このエラーは、変更されるデータにアクセスする、SELECT ステートメントの UPDLOCK ヒントを使用することにより回避できます。 詳細については、SQL Server オンライン ブックの「ロックのヒント」を参照してください。  
  
 スナップショット分離は、トランザクション内で使用する前に、ALLOW_SNAPSHOT_ISOLATION ON データベース オプションを設定して有効にする必要があります。 一時データベースに行バージョンを格納するためのメカニズムがアクティブになります (**tempdb**)。 Transact-SQL ALTER DATABASE ステートメントで使用する、各データベース内のスナップショット分離を有効にする必要があります。 この点では、スナップショット分離は、構成を必要としない READ COMMITTED、REPEATABLE READ、SERIALIZABLE、および READ UNCOMMITTED の従来の分離レベルとは異なります。 次のステートメントは、スナップショット分離をアクティブにして、既定の READ COMMITTED 動作を SNAPSHOT で置き換えます。  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 READ_COMMITTED_SNAPSHOT ON オプションを設定すると、既定の READ COMMITTED 分離レベルの下にあるバージョン管理された行にアクセスできます。 READ_COMMITTED_SNAPSHOT オプションが OFF に設定されている場合、バージョン管理された行にアクセスするためには、各セッションのスナップショット分離レベルを明示的に設定する必要があります。  
  
## <a name="managing-concurrency-with-isolation-levels"></a>分離レベルによるコンカレンシーの管理  
 Transact-SQL ステートメントを実行する分離レベルは、ロック動作と行バージョン管理動作を決定します。 分離レベルには接続全体のスコープがあり、SET TRANSACTION ISOLATION LEVEL ステートメントで接続に設定されると、その接続が閉じられるか、別の分離レベルが設定されるまでは有効になります。 接続が閉じられてプールに返されると、最後の SET TRANSACTION ISOLATION LEVEL ステートメントからの分離レベルが保持されます。 それ以降、プールされた接続を再利用する接続では、その接続がプールされた時点で有効にされた分離レベルが使用されます。  
  
 接続内で発行される個別のクエリには、接続の分離レベルに影響を与えることなく、1 つのステートメントまたはトランザクションの分離を変更するロック ヒントを含めることができます。 ストアド プロシージャまたは関数内で設定される分離レベルまたはロック ヒントは、これらを呼び出す接続の分離レベルを変更しません。また、分離レベルまたはロック ヒントは、ストアド プロシージャまたは関数呼び出しの間だけ有効になります。  
  
 SQL-92 標準で定義された 4 つの分離レベルが、初期のバージョンの SQL Server ではサポートされていました。  
  
- READ UNCOMMITTED は、他のトランザクションにより配置されたロックを無視するため、最も限定度が低い分離レベルです。 READ UNCOMMITTED の下で実行するトランザクションは、他のトランザクションによりまだコミットされていない、変更されたデータ値を読み取ることができます。これは "ダーティ" リードと呼ばれます。  
  
- READ COMMITTED は、SQL Server の既定の分離レベルです。 この分離レベルは、別のトランザクションによりまだコミットされていない、変更されたデータ値を読み取れないようにステートメントを指定することにより、ダーティ リードを防ぎます。 その他のトランザクションは、現在のトランザクション内で各ステートメントが実行される合間にデータを変更、挿入、削除できますが、反復不可能読み取りや "ファントム" データになります。  
  
- REPEATABLE READ は、READ COMMITTED よりも限定度が高い分離レベルです。 この分離レベルは、READ COMMITTED を含みます。さらに、現在のトランザクションをコミットするまでは、現在のトランザクションにより読み取られているデータを、他のトランザクションによって変更したり削除されたりしないようにします。 コンカレンシーは、READ COMMITTED の場合よりも低くなります。この理由は、読み取りデータ上で共有されるロックが、各ステートメントが終了するごとに解放されず、トランザクションが完了するまで保持されるためです。  
  
- SERIALIZABLE は、最も限定度の高い分離レベルで、トランザクションが完了するまで全範囲のキーをロックし、そのロックを保持します。 この分離レベルは、REPEATABLE READ を含みます。また、トランザクションが完了するまでは、トランザクションにより読み取られる範囲内に、他のトランザクションによって新しい行が挿入されないようにする制限を追加します。  
  
 詳細についてを参照してください、[トランザクション ロックおよび行のバージョン管理ガイド](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)します。  
  
### <a name="snapshot-isolation-level-extensions"></a>スナップショット分離レベルの拡張機能  
 SQL Server では、SNAPSHOT 分離レベルの導入および READ COMMITTED の追加実装と共に、SQL-92 分離レベルの拡張機能が導入されました。 READ_COMMITTED_SNAPSHOT 分離レベルは、すべてのトランザクションの READ COMMITTED を自動的に置き換えることができます。  
  
- SNAPSHOT 分離は、トランザクション内で読み取るデータに、他の同時トランザクションによって加えられた変更が反映されないようにします。 トランザクションでは、トランザクションの開始時に存在するデータの行バージョンを使用します。 データの読み取り時にロックがデータに配置されないため、データを書き込まれないようにスナップショット トランザクションによって他のトランザクションがブロックされるというようなことはありません。 データを書き込むトランザクションは、スナップショット トランザクションによるデータの読み取りをブロックしません。 スナップショット分離を使用するには、ALLOW_SNAPSHOT_ISOLATION データベース オプションを設定してスナップショット分離を有効にする必要があります。  
  
- READ_COMMITTED_SNAPSHOT データベース オプションは、スナップショット分離がデータベース内で有効になっている場合に、既定の READ COMMITTED 分離レベルの動作を決定します。 READ_COMMITTED_SNAPSHOT ON を明示的に指定していない場合、READ COMMITTED はすべての暗黙のトランザクションに適用されます。 これにより、READ_COMMITTED_SNAPSHOT OFF (既定) を設定した場合と同じ動作が生成されます。 READ_COMMITTED_SNAPSHOT OFF が有効になっている場合、データベース エンジンは共有ロックを使用して、既定の分離レベルを強制適用します。 READ_COMMITTED_SNAPSHOT データベース オプションが ON に設定されている場合、データベース エンジンは、ロックを使用してデータを保護せずに、既定として行バージョン管理とスナップショット分離を使用します。  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>スナップショット分離と行バージョン管理の機能について  
 SQL Server データベース エンジンが、元の行でのコピーを格納するスナップショット分離レベルが有効にすると、行が更新されるたびに**tempdb**行にトランザクション シーケンス番号を追加します。 発生するイベントのシーケンスは次のとおりです。  
  
- 新しいトランザクションが開始され、トランザクション シーケンス番号が割り当てられます。  
  
- データベース エンジンが、トランザクション内の行を読み取りから行バージョンを取得**tempdb**シーケンス番号は、最も近いと、トランザクション シーケンス番号よりも低い。  
  
- データベース エンジンは、スナップショット トランザクションの開始時点でアクティブだったコミットされていないトランザクションのトランザクション シーケンス番号の一覧内に、トランザクション シーケンス番号があるかどうかを確認します。  
  
- トランザクションから行のバージョンの読み込み**tempdb**トランザクションの開始時点で最新だった。 トランザクションが開始された後で挿入された新しい行は、シーケンス番号の値がトランザクション シーケンス番号の値よりも大きくなるため確認されません。  
  
- 現在のトランザクションで行バージョンがあるため、トランザクションの開始後に削除された行が表示されます**tempdb**下限のシーケンス番号の値にします。  
  
 スナップショット分離の適用により、トランザクションは、基になるテーブル上でロックを受け付けたり配置したりすることなく、トランザクションの開始時に存在したすべてのデータを確認します。 その結果、競合がある状況でパフォーマンスが向上することになります。  
  
 スナップショット トランザクションでは、他のトランザクションによって行が更新されないようにするロックは使用せずに、常にオプティミスティック コンカレンシーを使用します。 スナップショット トランザクションは、トランザクションの開始後に変更された行への更新をコミットしようとすると、このトランザクションがロールバックし、エラーになります。  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>ADO.NET でのスナップショット分離の使用  
 スナップショット分離は、<xref:System.Data.SqlClient.SqlTransaction> クラスによって ADO.NET 内でサポートされます。 開始する必要があります、データベースがスナップショット分離が有効になって READ_COMMITTED_SNAPSHOT ON が構成されていない場合、<xref:System.Data.SqlClient.SqlTransaction>を使用して、 **IsolationLevel.Snapshot**列挙値を呼び出すときに、 <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A>メソッド。 このコード フラグメントでは、接続は開かれている <xref:System.Data.SqlClient.SqlConnection> オブジェクトであることを前提としています。  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>例  
 ロックされたデータにアクセスしようとすることにより、分離レベルがそれぞれどのように動作するのかを、次の例に示します。このサンプルは、実行用のコードで使用されることは想定していません。  
  
 接続するコード、 **AdventureWorks**サンプルでは、SQL Server データベースとという名前のテーブルを作成します。 **TestSnapshot**を 1 行のデータを挿入します。 コードには ALTER DATABASE Transact-SQL ステートメントを使用し、データベースのスナップショット分離を有効にします。このとき、既定の READ COMMITTED 分離レベルの動作を有効なままにし、READ_COMMITTED_SNAPSHOT オプションは設定しません。 続いてコードは、次のアクションを実行します。  
  
- 更新トランザクションを開始するために、SERIALIZABLE 分離レベルを使用する sqlTransaction1 を開始し、完了しないようにします。 これには、テーブルがロックするという効果があります。  
  
- 2 番目の接続を開き、SNAPSHOT 分離レベルを使用してデータを読み取るする 2 番目のトランザクションを開始、 **TestSnapshot**テーブル。 スナップショット分離が有効になっているため、このトランザクションは、sqlTransaction1 が開始する前に存在していたデータを読み取ることができます。  
  
- 3 つ目の接続を開いて、READ COMMITTED 分離レベルを使ってトランザクションを開始し、テーブル内のデータの読み取りを試みます。 この場合、コードはデータを読み取れません。コードは最初のトランザクション内のテーブルに置かれたロックを超えて読み取りを行うことができず、タイムアウトになるためです。REPEATABLE READ 分離レベルと SERIALIZABLE 分離レベルが使用されている場合は、これらの分離レベルも、最初のトランザクション内に置かれたロックを超えて読み取りを行うことができないため、同じ結果になります。  
  
- 4 つ目の接続を開き、sqlTransaction1 内でコミットされていない値のダーティ リードを実行する READ UNCOMMITTED 分離レベルを使用し、トランザクションを開始します。 最初のトランザクションがコミットされていない場合、この値は実際にデータベース内には存在しません。  
  
- 最初のトランザクションをロールバックし、削除することによってクリーンアップ、 **TestSnapshot**スナップショット分離のテーブルおよびオフにすると、 **AdventureWorks**データベース。  
  
> [!NOTE]
>  次の例では、接続プールを無効にした状態で同じ接続文字列を使用します。 接続をプールした場合、その分離レベルをリセットしても、サーバー側の分離レベルはリセットされません。 その結果、同じプールされた内部接続を使用する後続の接続は、プールされた接続と同じ分離レベルで開始されることになります。 接続プールを無効にする代わりに、各接続について分離レベルを明示的に設定することもできます。  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>例  
 データ変更が行われている間のスナップショット分離の動作の例を次に示します。 コードは、次のアクションを実行します。  
  
- 接続する、 **AdventureWorks**サンプル データベースと有効のスナップショット分離します。  
  
- という名前のテーブルを作成します。 **TestSnapshotUpdate**サンプル データの 3 つの行を挿入します。  
  
- SNAPSHOT 分離を使って sqlTransaction1 を開始し、完了しないようにします。 3 行のデータがトランザクション内で選択されます。  
  
- 1 秒あたりの作成**SqlConnection**に**AdventureWorks**し、sqltransaction1 内で選択した行のいずれかの値を更新する READ COMMITTED 分離レベルを使用して 2 番目のトランザクションを作成します。  
  
- sqlTransaction2 をコミットします。  
  
- sqlTransaction1 に戻り、sqlTransaction1 がコミットした行と同じ行の更新を試みます。 エラー 3960 が発生し、sqlTransaction1 は自動的にロールバックされます。 **SqlException.Number**と**SqlException.Message**コンソール ウィンドウに表示されます。  
  
- スナップショット分離をオフにクリーンアップ コードを実行します**AdventureWorks**を削除し、 **TestSnapshotUpdate**テーブル。  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>スナップショット分離でのロック ヒントの使用  
 前の例では、最初のトランザクションがデータを選択し、このトランザクションが完了する前に 2 つ目のトランザクションがデータを更新しています。その結果、最初のトランザクションが同じ行を更新しようとすると、競合が発生します。 トランザクションの先頭にロック ヒントを指定することにより、長時間にわたるスナップショット トランザクションにおいて更新競合が発生する可能性を軽減できます。 次の SELECT ステートメントでは、選択した行をロックするために、UPDLOCK ヒントが使用されています。  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 UPDLOCK ロック ヒントを使用すると、最初のトランザクションが完了する前に行が更新されるのをブロックします。 これにより、選択した行が後にトランザクション内で更新されるときに、競合が発生しないことが保証されます。 SQL Server オンライン ブックの「ロックのヒント」を参照してください。  
  
 アプリケーションで競合が多数発生する場合、スナップショット分離は適切な選択肢ではない可能性があります。 ヒントの使用は、本当に必要な場合のみに制限する必要があります。 アプリケーションは、ロック ヒントに常に依存する操作にならないように設計されている必要があります。  
  
## <a name="see-also"></a>関連項目

- [SQL Server と ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
- [トランザクションのロックおよび行のバージョン管理ガイド](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)
