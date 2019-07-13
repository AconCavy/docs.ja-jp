---
title: Entity SQL と Transact-SQL の相違点
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 54d7a3fa8ce6e8a0aba6194bfc034eb4d47dbf60
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489932"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Entity SQL と Transact-SQL の相違点
このトピックでは、間の相違点を説明します。[!INCLUDE[esql](../../../../../../includes/esql-md.md)]と TRANSACT-SQL です。  
  
## <a name="inheritance-and-relationships-support"></a>継承とリレーションシップのサポート  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] エンティティの概念スキーマを直接操作し、継承やリレーションシップなどの概念モデルの機能をサポートします。  
  
 継承を操作するときは、スーパータイプ インスタンスのコレクションからサブタイプのインスタンスを選択すると便利である場合がよくあります。 [Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)演算子[!INCLUDE[esql](../../../../../../includes/esql-md.md)](のような`oftype`でC#シーケンス) この機能を提供します。  
  
## <a name="support-for-collections"></a>コレクションのサポート  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] コレクションをファーストクラスのエンティティとして扱われます。 例:  
  
- コレクションの式は、`from` 句内で有効です。  
  
- `in` サブクエリと `exists` サブクエリは任意のコレクションを使用できるように一般化されています。  
  
     サブクエリは一種のコレクションです。 `e1 in e2` および `exists(e)` は、これらの演算を実行する [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 構造です。  
  
- `union`、`intersect`、`except` などの集合演算は、現在ではコレクションに対して実行されます。  
  
- 結合はコレクションに対して実行されます。  
  
## <a name="support-for-expressions"></a>式のサポート  
 Transact SQL では、サブクエリ (テーブル) と式 (行および列) があります。  
  
 コレクションとを入れ子になったコレクションをサポートするために[!INCLUDE[esql](../../../../../../includes/esql-md.md)]はすべてを式。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] TRANSACT-SQL よりもコンポーザブルであり、すべての式をどこでも使用できます。 クエリ式は常に投射型のコレクションとなり、コレクション式が許可されている任意の場所で使用できます。 サポートされていない TRANSACT-SQL 式について[!INCLUDE[esql](../../../../../../includes/esql-md.md)]を参照してください[サポートされていない式](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)します。  
  
 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリはすべて有効です。  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>サブクエリの一貫した処理  
 テーブルに重点を指定するには、TRANSACT-SQL は、サブクエリのコンテキストを解釈を実行します。 内のサブクエリなど、`from`句は、マルチセット (テーブル) と見なされます。 ただし、`select` 句で使用される同じサブクエリは、スカラー サブクエリと見なされます。 同様に、サブクエリの左側にあるために使用する`in`演算子は、スカラー サブクエリの場合は、右側にあるは、サブクエリはマルチセット サブクエリをする必要があると見なされます。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ではこれらの違いが排除されます。 式は、使用するコンテキストに依存しない、一貫した方法で解釈されます。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] すべてのサブクエリはマルチセット サブクエリと見なします。 サブクエリ、スカラー値が必要な場合[!INCLUDE[esql](../../../../../../includes/esql-md.md)]提供、`anyelement`演算子です (この例では、サブクエリ) でのコレクションでは動作し、コレクションからシングルトン値を抽出します。  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>サブクエリの暗黙の強制型変換の回避  
 サブクエリの一貫した処理に伴う二次的作用として、スカラー値へのサブクエリの暗黙的な変換があります。 具体的には、transact-sql、(1 つのフィールド) を持つ行のマルチセットに暗黙的に変換データ型は、フィールドのスカラー値。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、この暗黙の強制型変換をサポートしていません。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、コレクションからシングルトン値を抽出するための ANYELEMENT 演算子と、クエリ式の実行中に row ラッパーの作成を回避するための `select value` 句が提供されています。  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>値を選択します。暗黙の Row ラッパーの回避  
 TRANSACT-SQL サブクエリの select 句は、句の項目に row ラッパーを暗黙的に作成します。 これは、スカラーやオブジェクトのコレクションを作成できないことを意味します。 Transact SQL では、1 つのフィールドの rowtype と、同じデータ型のシングルトン値の間の暗黙の強制変換を許可します。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] には、暗黙の行の構築をスキップする `select value` 句が用意されています。 `select value` 句には 1 つの項目のみを指定できます。 このような句を使用した場合、`select` 句内の項目には row ラッパーは構築されず、目的の構造を持つコレクションを作成できます。たとえば、`select value a` のように指定します。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] には、任意の行を構築するための行コンストラクターも用意されています。 `select` は、投影の 1 つ以上の要素を受け取り、結果はフィールドを持つデータ レコードになります。次のように指定します。  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>左の相関関係と別名定義  
 Transact sql で指定されたスコープ内の式 (ような単一句`select`または`from`)、同じスコープで既に定義済みの式を参照することはできません。 SQL (Transact SQL を含む) のいくつかの言語仕様は、これらの制限付きのフォームをサポートして、`from`句。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 左の相関関係を一般化、`from`句、およびこれらを取り扱います。 `from` 句内の式は、追加の構文を使用せずに、同じ句内で先に作成された定義 (左側の定義) を参照できます。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、`group by` 句を伴うクエリにも制限を課しています。 内の式、`select`句と`having`のようなクエリ句しか参照、`group by`別名を使用してキー。 次の構造は TRANSACT-SQL が含まれないのは有効な[!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 これを [!INCLUDE[esql](../../../../../../includes/esql-md.md)] で実行するには、次のように指定します。  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>テーブル (コレクション) の列 (プロパティ) の参照  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 内の列の参照は、すべてテーブルの別名を使用して修飾する必要があります。 次の構成体 (仮定`a`テーブルの有効な列は、 `T`) が有効では TRANSACT-SQL ではなく[!INCLUDE[esql](../../../../../../includes/esql-md.md)]。  
  
```  
select a from T  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の形式は次のとおりです。  
  
```  
select t.a as A from T as t  
```  
  
 テーブルの別名は `from` 句では省略できます。 テーブル名は暗黙的な別名として使用されます。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では次の形式も使用できます。  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>オブジェクト間の移動  
 TRANSACT-SQL を使用して、"."表記 (の行) の列を参照するテーブル。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ではこの表記法を拡張し (プログラミング言語から借用)、オブジェクトのプロパティ間の移動をサポートしています。  
  
 たとえば、`p` が Person 型の式である場合、この人の住所の市区町村を参照するには次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 構文が使用されます。  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>* のサポートなし  
 Transact SQL をサポートしています、修飾されていない * 構文全体の行と、修飾のエイリアスとして\*構文 (t.\*)、テーブルのフィールドのショートカットとして。 TRANSACT-SQL で特別な数は、さらに、(\*) 集計で、null 値が含まれています。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、* 構造をサポートしていません。 フォームの TRANSACT-SQL クエリ`select * from T`と`select T1.* from T1, T2...`で表現できる[!INCLUDE[esql](../../../../../../includes/esql-md.md)]として`select value t from T as t`と`select value t1 from T1 as t1, T2 as t2...`、それぞれします。 また、これらの構造は継承 (値の置換可能性) に対応していますが、`select *` Variant 型では宣言された型の最上位レベルのプロパティに限定されています。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は `count(*)` 集計をサポートしていません。 代わりに、`count(0)` を使用してください。  
  
## <a name="changes-to-group-by"></a>Group By への変更  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では `group by` キーの別名定義をサポートしています。 内の式、`select`句と`having`句を参照する必要があります、`group by`これらの別名を使用してキー。 たとえば、次のような [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 構文があるとします。  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 ...次の TRANSACT-SQL に相当します。  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>コレクションベースの集計  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、2 種類の集計をサポートしています。  
  
 コレクションベースの集計は、コレクションに対して演算を行い、集計結果を生成します。 これらはクエリ内の任意の場所で使用でき、`group by` 句を必要としません。 次に例を示します。  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、SQL スタイルの集計もサポートしています。 次に例を示します。  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY 句の使用法  
 Transact SQL では ORDER BY 句を最上位でのみ指定する. FROM .. WHERE ブロックでのみ指定できます。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、入れ子になった ORDER BY 式を使用でき、それをクエリ内の任意の場所に配置できますが、入れ子になったクエリ内の順序は保持されません。  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>識別子  
 Transact sql では、識別子の比較は、現在のデータベースの照合順序に基づいています。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の識別子では、常に大文字と小文字は区別されず、アクセントは区別されます (つまり、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] ではアクセントのある文字とアクセントのない文字が区別されます。たとえば、'a' と 'ấ' は等しくありません)。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、同じように表示されても別のコード ページに由来する文字の複数のバージョンを別々の文字として扱います。 詳細については、次を参照してください。[入力文字セット](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)します。  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Entity SQL では使用できない Transact-SQL 機能  
 次の TRANSACT-SQL 機能が記載されていない[!INCLUDE[esql](../../../../../../includes/esql-md.md)]します。  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] DML ステートメントのサポートは現在ありません (挿入、更新、削除) します。  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の現在のバージョンでは DDL はサポートされていません。  
  
 命令型プログラミング  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Transact SQL とは異なり、命令型プログラミングのサポートを提供しません。 代わりにプログラミング言語を使用します。  
  
 グループ化関数  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ではグループ化関数 (CUBE, ROLLUP、GROUPING_SET など) はサポートしていません。  
  
 分析関数  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では分析関数はまだサポートしていません。  
  
 組み込み関数、演算子  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 関数と演算子で構築されていますの TRANSACT-SQL のサブセットをサポートしています。 これらの演算子と関数の多くは、主要なストア プロバイダーによりサポートされています。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] プロバイダー マニフェストで宣言されたストア固有の関数を使用します。 さらに、[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]組み込みを宣言することができ、既存のユーザー定義ストア関数を[!INCLUDE[esql](../../../../../../includes/esql-md.md)]を使用します。  
  
 ヒント  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ではクエリ ヒントのメカニズムは提供していません。  
  
 クエリ結果のバッチ処理  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、クエリ結果のバッチ処理はサポートされていません。 たとえば、有効な TRANSACT-SQL (バッチとして送信) は、次のように。  
  
```  
select * from products;  
select * from catagories;  
```  
  
 ただし、同等の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] はサポートされていません。  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、コマンドごとに 1 つの結果生成クエリ ステートメントのみをサポートします。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [サポートされていない式](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
