---
title: 標準クエリ演算子の変換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: 1bba36579fce4fe78289ccb986073280b531420a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661876"
---
# <a name="standard-query-operator-translation"></a>標準クエリ演算子の変換

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、標準クエリ演算子から SQL コマンドへの変換が行われます。 データベースのクエリ プロセッサは、SQL 変換の実行のセマンティクスを決定します。

標準クエリ演算子が定義されている*シーケンス*します。 シーケンスは*注文*シーケンスの各要素の参照 id に依存しています。 詳細については、次を参照してください。[標準クエリ演算子の概要 (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)または[標準クエリ演算子の概要 (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)します。

主に SQL が扱う*値のセットを順不同*します。 通常、順序付けは、明示的な後処理の操作として、クエリの中間結果ではなく最終結果に対して適用されます。 ID は値で定義されます。 このため、SQL クエリを理解して、マルチセットを処理する (*バッグ*) の代わりに*設定*します。

以下、標準クエリ演算子とその SQL 変換との違いを、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 用 SQL Server プロバイダーの場合について説明します。

## <a name="operator-support"></a>演算子のサポート

### <a name="concat"></a>Concat

<xref:System.Linq.Enumerable.Concat%2A> メソッドは、受信側と引数の順序が同じである、順序付けされたマルチセットに対して定義されます。 <xref:System.Linq.Enumerable.Concat%2A> は、共通の順序に従ったマルチセットに対する `UNION ALL` として機能します。

最後の手順は、結果を生成する前の SQL での順序付けです。 <xref:System.Linq.Enumerable.Concat%2A> は、引数の順序を維持しません。 適切な順序にするには、<xref:System.Linq.Enumerable.Concat%2A> の結果を明示的に順序付けする必要があります。

### <a name="intersect-except-union"></a>Intersect、Except、Union

<xref:System.Linq.Enumerable.Intersect%2A> メソッドと <xref:System.Linq.Enumerable.Except%2A> メソッドは、セットに対してのみ正しく定義されます。 マルチセットのセマンティクスは未定義です。

<xref:System.Linq.Enumerable.Union%2A> メソッドは、マルチセットの順序なし連結メソッドとして、マルチセットに対して定義されます (事実上、SQL の UNION ALL 句の結果)。

### <a name="take-skip"></a>Take、Skip

<xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A>メソッドは、に対してのみ正しく定義*の順序付けセット*します。 順序付けされていないセットまたはマルチセットのセマンティクスは未定義です。

> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A> と <xref:System.Linq.Enumerable.Skip%2A> を SQL Server 2000 に対するクエリで使用する場合は、いくつかの制限があります。 詳細については、「Skip 例外と Take 例外を SQL Server 2000」エントリを参照してください。[トラブルシューティング](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)します。

SQL では、順序付けの制限のため[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]メソッドの結果にこれらのメソッドの引数の順序を移動しようとしています。 たとえば、次のような [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリがあるとします。

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

このコードに対して生成される SQL では、順序が次のように末尾に移動されます。

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<xref:System.Linq.Enumerable.Take%2A> と <xref:System.Linq.Enumerable.Skip%2A> を連結する場合は、指定されているすべての順序が一致することが当然必要です。 それ以外の場合、結果は未定義です。

<xref:System.Linq.Enumerable.Take%2A> と <xref:System.Linq.Enumerable.Skip%2A> はいずれも、標準クエリ演算子の仕様に基づく、負でない定数の整数引数に対して正しく定義されます。

### <a name="operators-with-no-translation"></a>変換されない演算子

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって変換されないメソッドを次に示します。 最も一般的な理由は、順序なしのマルチセットとシーケンスの違いにあります。

|演算子|理由|
|---------------|---------------|
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|SQL クエリの操作の対象は、シーケンスではなく、マルチセットです。 結果に対して適用する最後の句が `ORDER BY` であることが必要です。 このため、これら 2 つのメソッドには、汎用的な変換がありません。|
|<xref:System.Linq.Enumerable.Reverse%2A>|順序付けされたセットに対しては、このメソッドの変換が可能ですが、現在の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では変換されません。|
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|順序付けされたセットに対しては、これらのメソッドの変換が可能ですが、現在の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では変換されません。|
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|SQL クエリの操作の対象は、インデックス可能なシーケンスではなくマルチセットです。|
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (既定の引数のオーバーロード)|一般に、任意のタプルに対して既定値を指定することはできません。 場合によっては、外部結合を通じて、タプルに対する null 値の使用が可能です。|

## <a name="expression-translation"></a>式の変換

### <a name="null-semantics"></a>null セマンティクス

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、null 比較セマンティクスを SQL に強制しません。 比較演算子は、対応する SQL の演算子に構文上は変換されます。 このため、セマンティクスには、サーバーまたは接続の設定で定義された SQL セマンティクスが反映されます。 たとえば、2 つの null 値が既定の SQL Server の設定で等しくないと見なされますが、セマンティクスを変更する設定を変更することができます。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、クエリを変換するときにサーバーの設定を考慮しません。

リテラルの null による比較は適切な SQL 形式 (`is null` または `is not null`) に変換されます。

`null` の値の照合順序は SQL Server で定義されます [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では変更されません。

### <a name="aggregates"></a>集計

標準クエリ演算子の集計メソッド <xref:System.Linq.Enumerable.Sum%2A> では、空のシーケンスや null のみを含むシーケンスはゼロに評価されます。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、SQL のセマンティクスのまま変更せずと<xref:System.Linq.Enumerable.Sum%2A>に評価される`null`ゼロまたは null のみを含むシーケンスの空のシーケンスではなく。

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] での集計には、中間結果に対する SQL の制限が適用されます。 32 ビットの整数の <xref:System.Linq.Enumerable.Sum%2A> の計算では、64 ビットの結果は使用されません。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] による <xref:System.Linq.Enumerable.Sum%2A> の変換では、オーバーフローが発生することがあります。これには、標準クエリ演算子の実装で、対応するメモリ内シーケンスでオーバーフローが発生しないケースも含まれます。

同様に、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が整数値の <xref:System.Linq.Enumerable.Average%2A> を変換するときには、`integer` ではなく `double` として計算されます。

### <a name="entity-arguments"></a>エンティティ引数

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] により、エンティティ型で使用される、<xref:System.Linq.Enumerable.GroupBy%2A>と<xref:System.Linq.Enumerable.OrderBy%2A>メソッド。 これらの演算子の変換では、型の引数を使用している場合、その型のすべてのメンバーを指定しているのと同等と見なされます。 たとえば、次のコードは同じ意味です。

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a>引数の等値性/比較

以下のメソッドの実装では、引数が等値であることが必要です。

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 等値との比較をサポートしている*フラット*引数、またはシーケンスが含まれる引数ではなく。 フラットな引数とは、SQL の行に対応付けられる型のものです。 シーケンスを含まないと静的に決定できる 1 つまたは複数のエンティティ型の射影は、フラットな引数と見なされます。

フラットな引数の例を次に示します。

[!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

フラットでない (階層構造の) 引数の例を次に示します。

[!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a>Visual Basic の関数の変換

Visual Basic のコンパイラが使用する以下のヘルパー関数は、対応する SQL 演算子および関数に変換されます。

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

変換メソッド :

|||||
|-|-|-|-|
|ToBoolean|ToSByte|ToByte|ToChar|
|ToCharArrayRankOne|ToDate|ToDecimal|ToDouble|
|ToInteger|ToUInteger|ToLong|ToULong|
|ToShort|ToUShort|ToSingle|ToString|

## <a name="inheritance-support"></a>継承のサポート

### <a name="inheritance-mapping-restrictions"></a>継承の対応付けの制限

詳細については、「[方法 :継承階層を割り当てる](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)します。

### <a name="inheritance-in-queries"></a>クエリでの継承

C# のキャストは射影でのみサポートされます。 他の場所で使用したキャストは変換されず、無視されます。 SQL 関数名を除き、SQL が実行するのは、共通言語ランタイム (CLR: Common Language Runtime) の <xref:System.Convert> に相当する処理のみです。 つまり、SQL は、ある型の値を別の型に変更することはできます。 CLR のキャストに相当するものはありません。同じビット列を別の型として再解釈するという概念がないためです。 したがって、C# のキャストはローカルでのみ機能します。 リモート処理はされません。

演算子 `is` と `as`、および `GetType` メソッドは、`Select` 演算子に限定されません。 他のクエリ演算子でも使用できます。

## <a name="sql-server-2008-support"></a>SQL Server 2008 のサポート

.NET Framework 3.5 SP1 以降、LINQ to SQL は SQL Server 2008 で導入された新しい日付/時刻型へのマッピングをサポートします。 ただし、これらの新しい型にマッピングされた値を操作するときに使用できる LINQ to SQL のクエリ演算子にはいくつか制限があります。

### <a name="unsupported-query-operators"></a>サポートされていないクエリ演算子

`DATETIME2`、`DATE`、`TIME`、および `DATETIMEOFFSET` は、SQL Server の新しい日付/時刻型にマッピングされた値ではサポートされていません。

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

これらの SQL Server の日付と時刻型へのマッピングの詳細については、次を参照してください。 [SQL-CLR 型マッピング](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)します。

## <a name="sql-server-2005-support"></a>SQL Server 2005 のサポート

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、SQL Server 2005 の以下の機能をサポートしていません。

- SQL CLR 用に作成されたストアド プロシージャ。

- ユーザー定義型。

- XML クエリ機能。

## <a name="sql-server-2000-support"></a>SQL Server 2000 のサポート

次の SQL Server 2000 の制限事項 (Microsoft SQL Server 2005 との比較) に影響を与える[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]をサポートします。

### <a name="cross-apply-and-outer-apply-operators"></a>Cross Apply 演算子および Outer Apply 演算子

これらの演算子では、SQL Server 2000 で使用できません。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、一連の書き換えを行って、これらの演算子を適切な結合に置換します。

`Cross Apply` および `Outer Apply` は、リレーションシップ ナビゲーションに対してのみ生成されます。 どのようなクエリのセットに対してこのような書き換えが可能かは、正しく定義されていません。 このため、SQL Server 2000 のサポートされているクエリの最小限のセットはリレーションシップのナビゲーションを含まないセット。

### <a name="text--ntext"></a>text / ntext

データ型`text`  /  `ntext`に対して特定のクエリ操作では使用できません`varchar(max)`  /  `nvarchar(max)`、Microsoft SQL Server 2005 でサポートされています。

この制限事項には、対処方法はありません。 具体的には、`Distinct()` 列または `text` 列に割り当てられているメンバーを含む結果に対して、`ntext` を使用することはできません。

### <a name="behavior-triggered-by-nested-queries"></a>入れ子になったクエリによってトリガーされる動作

(SP4 まで)、SQL Server 2000 のバインダーでは、入れ子になったクエリによってトリガーされる特異な動作があります。 この特異動作をトリガーする SQL クエリのセットは、正しく定義されていません。 このためのセットを定義することはできません[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL Server の例外を引き起こす可能性のあるクエリ。

### <a name="skip-and-take-operators"></a>Skip 演算子および Take 演算子

<xref:System.Linq.Enumerable.Take%2A> と <xref:System.Linq.Enumerable.Skip%2A> を SQL Server 2000 に対するクエリで使用する場合は、いくつかの制限があります。 詳細については、「Skip 例外と Take 例外を SQL Server 2000」エントリを参照してください。[トラブルシューティング](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)します。

## <a name="object-materialization"></a>オブジェクトの具体化

実体化とは、1 つまたは複数の SQL クエリで返された行から CLR オブジェクトを作成することです。

- 次の呼び出しは*がローカルで実行*実体化の一部として。

  - コンストラクター

  - 射影での `ToString` メソッド

  - 射影での型キャスト

- 次のメソッド、<xref:System.Linq.Enumerable.AsEnumerable%2A>メソッドは*がローカルで実行*します。 このメソッドでは即時実行は行われません。

- `struct` は、クエリ結果の戻り値の型として、または結果の型のメンバーとして使用できます。 エンティティはクラスである必要があります。 匿名型はクラス インスタンスとして実体化されますが、射影では名前付き構造体 (エンティティ以外) を使用できます。

- クエリ結果の戻り値の型のメンバーには、<xref:System.Linq.IQueryable%601> 型を使用できます。 これはローカル コレクションとして実体化されます。

- 次のメソッドにより、*即時実体化*メソッドに適用されるシーケンスの。

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a>関連項目

- [参照](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [シーケンスの要素の取得またはスキップ](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)
- [2 つのシーケンスの連結](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)
- [2 つのシーケンスの差集合の取得](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)
- [2 つのシーケンスの積集合の取得](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)
- [2 つのシーケンスの和集合の取得](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
