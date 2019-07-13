---
title: コンパイル済みクエリ (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: d3f24fb335169c2b38ce945377bc4e64a47fe9d5
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539920"
---
# <a name="compiled-queries--linq-to-entities"></a>コンパイル済みクエリ (LINQ to Entities)
似たような構造のクエリを Entity Framework で何度も実行するアプリケーションがある場合は、クエリを一度コンパイルし、異なるパラメーターを指定して複数回実行することで、パフォーマンスを改善できる場合がよくあります。 たとえば、アプリケーションで特定の市区町村に住む顧客をすべて取得する必要がある場合は、ユーザーが実行時にフォーム内で市区町村を指定します。 LINQ to Entities では、この目的のためにコンパイル済みクエリをサポートしています。  
  
 .NET Framework 4.5 以降では、LINQ クエリは自動的にキャッシュされます。 ただし、引き続きコンパイル済み LINQ クエリを使用して後続の実行でさらにコストを削減できます。コンパイル済みクエリは、自動的にキャッシュされる LINQ クエリよりも効率的である場合があります。 メモリ内コレクションへ `Enumerable.Contains` 演算子を追加する LINQ to Entities クエリは自動的にキャッシュされないことに注意してください。 またコンパイル済み LINQ クエリのメモリ内コレクションをパラメーターで表すことは許可されていません。  
  
 <xref:System.Data.Objects.CompiledQuery> クラスは、クエリをコンパイルおよびキャッシュして、再利用できるようにします。 このクラスには、概念上、<xref:System.Data.Objects.CompiledQuery> の `Compile` メソッドとその複数のオーバーロードが存在します。 `Compile` メソッドを呼び出すと、コンパイル済みクエリを表す新しいデリゲートを作成できます。 `Compile` およびパラメーター値が指定された <xref:System.Data.Objects.ObjectContext> メソッドは、なんらかの結果 (<xref:System.Linq.IQueryable%601> インスタンスなど) をもたらすデリゲートを返します。 クエリは、初回実行時に 1 回だけコンパイルされます。 コンパイル時にクエリに対して設定したマージ オプションは、後から変更できません。 一度クエリがコンパイルされると、プリミティブ型のパラメーターを指定することしかできず、生成された SQL を変更するクエリの部分を置き換えることはできません。 詳細については、次を参照してください[Entity Framework マージ オプションおよびコンパイルされたクエリ。](https://go.microsoft.com/fwlink/?LinkId=199591)  
  
 LINQ to Entities クエリ式を<xref:System.Data.Objects.CompiledQuery>の`Compile`メソッドによってコンパイルは、ジェネリックのいずれかで表される`Func`デリゲートなど<xref:System.Func%605>します。 クエリ式は、最大で、`ObjectContext` パラメーター、戻りパラメーター、および 16 個のクエリ パラメーターをカプセル化できます。 17 個以上のクエリ パラメーターが必要な場合は、クエリ パラメーターを表すプロパティを持つ構造体を作成できます。 次に、その構造体のプロパティを設定した後、それらのプロパティをクエリ式で使用できます。  
  
## <a name="example"></a>例  
 次の例では、入力パラメーターとして <xref:System.Decimal> を受け取り、合計支払額が $200.00 以上である一連の注文を返すクエリをコンパイルして呼び出します。  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Data.Objects.ObjectQuery%601> のインスタンスを返すクエリをコンパイルして呼び出します。  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>例  
 次の例では、製品の定価の平均を <xref:System.Decimal> 値として返すクエリをコンパイルして呼び出します。  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>例  
 次の例は、コンパイルして、受け取るクエリを呼び出します、<xref:System.String>の入力パラメーターとし、返します、`Contact`電子メール アドレスを持つ指定した文字列から始まります。  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>例  
 次の例では、入力パラメーターとして <xref:System.DateTime> および <xref:System.Decimal> を受け取り、注文日が 2003 年 3 月 8 日より遅く合計支払額が $300.00 未満である一連の注文を返すクエリをコンパイルして呼び出します。  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>例  
 次の例では、入力パラメーターとして <xref:System.DateTime> を受け取り、注文日が 2004 年 3 月 8 日より遅い一連の注文を返すクエリをコンパイルして呼び出します。 このクエリは、注文情報を一連の匿名型として返します。 匿名型はコンパイラによって推論されるので、型パラメーターを <xref:System.Data.Objects.CompiledQuery> の `Compile` メソッドに指定することはできず、型はクエリ自体で定義されます。  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>例  
 次の例では、入力パラメーターとしてユーザー定義の構造体を受け取り、一連の注文を返すクエリをコンパイルして呼び出します。 この構造体では開始日、終了日、合計支払額のクエリ パラメーターを定義しており、クエリは、2003 年 3 月 3 日から 3 月 8 日までに出荷された、合計支払額が $700.00 を超える注文を返します。  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 クエリ パラメーターを定義する構造体を次に示します。  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>関連項目

- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [Entity Framework マージ オプションおよびコンパイル済みクエリ](https://go.microsoft.com/fwlink/?LinkId=199591)
