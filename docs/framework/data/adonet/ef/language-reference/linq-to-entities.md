---
title: LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
ms.openlocfilehash: 8a69d74966b99d78b4a7addaa4323d61d82ce8d5
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539770"
---
# <a name="linq-to-entities"></a>LINQ to Entities
LINQ to Entities は、開発者が Visual Basic または Visual C# を使用して Entity Framework 概念モデルに対するクエリを作成するための統合言語クエリ (LINQ) のサポートを提供します。 Entity Framework に対するクエリで代表的なものが、コマンド ツリー クエリです。これはオブジェクト コンテキストに対して実行されます。 LINQ to Entities では、統合言語クエリ (LINQ) クエリをコマンド ツリー クエリに変換し、そのクエリを Entity Framework に対して実行します。返されたオブジェクトは、Entity Framework でも LINQ でも使用できます。 次に、LINQ to Entities クエリを作成して実行する手順を示します。  
  
1. <xref:System.Data.Objects.ObjectQuery%601> から <xref:System.Data.Objects.ObjectContext> インスタンスを作成します。  
  
2. <xref:System.Data.Objects.ObjectQuery%601> インスタンスを使用して、C# または Visual Basic で LINQ to Entities クエリを作成します。  
  
3. LINQ 標準クエリ演算子および標準クエリ式をコマンド ツリーに変換します。  
  
4. コマンド ツリーで表されたクエリをデータ ソースに対して実行します。 実行中にデータ ソースに対してスローされた例外は、クライアントに直接渡されます。  
  
5. クエリの結果をクライアントに返します。  
  
## <a name="constructing-an-objectquery-instance"></a>ObjectQuery インスタンスの構築  
 <xref:System.Data.Objects.ObjectQuery%601> ジェネリック クラスは、0 個以上の型指定されたエンティティのコレクションを返すクエリを表します。 通常、オブジェクト クエリは手作業で構築されるのではなく、既存のオブジェクト コンテキストから構築され、常にそのオブジェクト コンテキストに属しています。 このコンテキストにより、クエリの作成と実行に必要な接続情報とメタデータ情報が取得されます。 <xref:System.Data.Objects.ObjectQuery%601> ジェネリック クラスでは、<xref:System.Linq.IQueryable%601> ジェネリック インターフェイスが実装されます。このインターフェイスのビルダー メソッドにより、LINQ クエリを段階的に構築できます。 C# `var` キーワード (Visual Basic の場合は `Dim`、ローカル型推論を有効にする) を使用することで、コンパイラでエンティティの型を推論することもできます。  
  
## <a name="composing-the-queries"></a>クエリの作成  
 <xref:System.Data.Objects.ObjectQuery%601> ジェネリック インターフェイスを実装する <xref:System.Linq.IQueryable%601> ジェネリック クラスのインスタンスは、LINQ to Entities クエリのデータ ソースとして動作します。 クエリでは、データ ソースから取得する情報を正確に指定できます。 また、並べ替え、グループ化、整形方法を指定して情報を取得することもできます。 LINQ では、クエリが変数に格納されます。 このクエリ変数は、クエリの情報を保存するだけで、なんらかのアクションを実行したり、データを返したりすることはありません。 クエリを作成した後、データを取得するには、そのクエリを実行する必要があります。  
  
 LINQ to Entities クエリは、クエリ式の構文とメソッド ベースのクエリ構文という 2 とおりの構文を使って作成できます。 クエリ式の構文とメソッド ベースのクエリ構文は、C# 3.0 と Visual Basic 9.0 で新たに導入された機能です。  
  
 詳細については、次を参照してください。[で LINQ to Entities クエリ](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)します。  
  
## <a name="query-conversion"></a>クエリの変換  
 LINQ to Entities クエリを Entity Framework に対して実行するには、LINQ クエリを Entity Framework に対して実行できるコマンド ツリー表現に変換する必要があります。  
  
 LINQ to Entities クエリは、LINQ 標準クエリ演算子 (<xref:System.Linq.Queryable.Select%2A>、<xref:System.Linq.Queryable.Where%2A>、<xref:System.Linq.Queryable.GroupBy%2A> など) と式 (x > 10 や Contact.LastName など) で構成されます。 LINQ 演算子はクラスで定義されるものではなく、クラスのメソッドです。 LINQ の式には、<xref:System.Linq.Expressions> 名前空間の型で許容される要素だけでなく、ラムダ関数で表される要素であれば何でも使用できます。 これは Entity Framework で許容される式のスーパーセットです。定義により、このような式はデータベースで許容され、<xref:System.Data.Objects.ObjectQuery%601> でサポートされる操作に限定されています。  
  
 Entity Framework では、演算子と式は 1 つの型の階層で表された後、コマンド ツリーに配置されます。 このコマンド ツリーが、Entity Framework でのクエリの実行に使用されます。 LINQ クエリをコマンド ツリーとして表現できない場合、クエリの変換中に例外がスローされます。 LINQ to Entities クエリを変換する際には、標準クエリ演算子の変換と式の変換という 2 つの変換が実行されます。  
  
 LINQ to Entities で正しく変換されない LINQ 標準クエリ演算子は多数あります。 このような演算子を使用すると、クエリの変換時に例外が発生します。 サポートされている LINQ to Entities クエリの一覧は、次を参照してください。[サポートされているとサポートされていない LINQ メソッド (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)します。  
  
 LINQ to Entities で標準クエリ演算子の使用に関する詳細については、次を参照してください。 [LINQ to Entities クエリでの標準クエリ演算子](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md)します。  
  
 一般的に、LINQ to Entities の式はサーバー上で評価されるため、式の動作が CLR セマンティクスに従っているとは限りません。 詳細については、次を参照してください。 [LINQ to Entities クエリ内の式](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)します。  
  
 CLR メソッドの呼び出しをデータ ソースの正規関数にマップする方法については、次を参照してください。 [CLR メソッドと正規関数マッピング](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)します。  
  
 正規の呼び出し、データベース、およびエンティティのクエリを LINQ 内からのカスタム関数をする方法については、次を参照してください。 [LINQ to Entities クエリ内の関数の呼び出し](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)します。  
  
## <a name="query-execution"></a>クエリの実行  
 ユーザーが LINQ クエリを作成すると、Entity Framework と互換性のある表現 (コマンド ツリーの形) に変換された後、データ ソースに対して実行されます。 クエリの実行時に、すべてのクエリ式 (またはクエリの構成要素) がクライアントまたはサーバー上で評価されます。 これには、結果の具体化やエンティティの投影で使用される式も含まれます。 詳細については、次を参照してください。[クエリの実行](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)します。 クエリを 1 回コンパイルしてから、実行する複数回異なるパラメーターを使用してパフォーマンスを向上させる方法については、次を参照してください。[コンパイルされたクエリ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)します。  
  
## <a name="materialization"></a>具体化  
 具体化は、クエリの結果を CLR 型としてクライアントに返すプロセスです。 LINQ to Entities では、クエリの結果のデータ レコードは決して返されません。常に返されるのは、ユーザーまたは Entity Framework で定義された CLR 型、またはコンパイラによって生成される CLR 型 (匿名型) です。 オブジェクトの具体化は、すべて Entity Framework によって実行されます。 Entity Framework と CLR とのマッピングができないことが原因でエラーが発生すると、オブジェクトの具体化中に例外がスローされます。  
  
 通常、クエリの結果は次のいずれかの形で返されます。  
  
- 0 個以上の型指定されたエンティティ オブジェクトのコレクション、または概念モデルで定義されている複合型のプロジェクション。  
  
- [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] でサポートされる CLR 型。  
  
- インライン コレクション。  
  
- 匿名型。  
  
 詳細については、次を参照してください。[クエリ結果](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [LINQ to Entities でのクエリ](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
  
 [LINQ to Entities クエリ内の式](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)  
  
 [LINQ to Entities クエリ内の関数の呼び出し](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
  
 [コンパイル済みクエリ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)  
  
 [クエリの実行](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)  
  
 [クエリ結果](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md)  
  
 [LINQ to Entities クエリの標準クエリ演算子](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md)  
  
 [CLR メソッドと正規関数とのマッピング](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)  
  
 [サポート対象の LINQ メソッドとサポート非対象の LINQ メソッド (LINQ to Entities) ](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
  
 [LINQ to Entities の既知の問題および注意点](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)  
  
## <a name="see-also"></a>関連項目

- [LINQ to Entities の既知の問題および注意点](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
- [統合言語クエリ (LINQ) - C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [統合言語クエリ (LINQ) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ と ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
