---
title: リレーションシップを介したクエリの実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 2e1cf9efcf47fc70421c64541aead5fb36d8c9d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916774"
---
# <a name="querying-across-relationships"></a>リレーションシップを介したクエリの実行
他のオブジェクトまたは他のオブジェクトのコレクションをクラス定義内で参照することは、データベース内の外部キー リレーションシップに直接対応します。 クエリを実行するときにこのリレーションシップを使用するには、ドット表記を使ってリレーションシップ プロパティにアクセスし、オブジェクト間を移動します。 これらのアクセス操作は、SQL で同等の複雑な結合または相関サブクエリとして変換されます。  
  
 たとえば、次のクエリでは、ロンドン在住の顧客からの注文のみが結果として得られるように注文から顧客へと移動します。  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 これらを記述する必要がありますリレーションシップのプロパティが存在しなかった場合に手動で*結合*と、次のコードのように、SQL クエリでの操作と同様。  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 使用することができます、*リレーションシップ*プロパティを 1 回この特定のリレーションシップを定義します。 こうすると、使いやすいドット構文を使用できるようになります。 しかし、それだけがリレーションシップ プロパティの利点ではありません。なぜなら、通常はドメイン固有のオブジェクト モデルは階層構造またはグラフとして定義されるからです。 プログラムで使用するオブジェクトには他のオブジェクトへの参照が含まれます。 このオブジェクト間リレーションシップがデータベースの外部キー型リレーションシップに相当するのは、単なる幸運な偶然です。 プロパティへのアクセスは、結合を記述するための便利な方法となります。  
  
 この点では、リレーションシップ プロパティは、クエリそのものよりもクエリの結果でより重要です。 クエリによって特定の顧客に関するデータが取得された後で、クラス定義ではその顧客の注文が存在することが示されます。 つまり、特定の顧客の `Orders` プロパティにその顧客のすべての注文が含まれると見なすことができます。 実際には、これはクラスをこのように定義することにより宣言したコントラクトです。 クエリによって注文が要求されなかった場合でも、ここに注文が含まれていると見なすことができます。 オブジェクト モデルに対して期待されるのは、それがデータベースがメモリ内に拡張されたものであり、関連オブジェクトがすぐに使用できる状態にある、という錯覚を維持することです。  
  
 リレーションシップが得られたので、クラスに定義されたリレーションシップ プロパティを参照してクエリを作成できます。 これらのリレーションシップ参照は、データベース内の外部キー リレーションシップに対応します。 これらのリレーションシップを使用する操作は、SQL で同等の複雑な結合として変換されます。 <xref:System.Data.Linq.Mapping.AssociationAttribute> 属性を使用してリレーションシップを定義している限りは、明示的な結合を [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で記述する必要はありません。  
  
 この錯覚を維持するために[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]と呼ばれる手法を実装する*遅延読み込み*します。 詳細については、次を参照してください。[遅延読み込みと即時読み込み](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)します。  
  
 プロジェクトの一覧を次の SQL クエリについて考えてみます`CustomerID` - `OrderID`ペア。  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して同じ結果を得るには、`Orders` クラスに既に存在する `Customer` プロパティ参照を使用します。 `Orders`参照は、クエリとプロジェクトを実行するために必要な情報を提供します。、 `CustomerID` - `OrderID`ペアは、次のコードのようにします。  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 逆の操作も可能です。 つまり、`Orders` にクエリを実行し、その `Customer` リレーションシップ参照を使用して、関連付けられた `Customer` オブジェクトに関する情報にアクセスできます。 次のコード プロジェクトを同じ`CustomerID` - `OrderID`クエリを実行してこの時間が、以前と同様のペアを`Orders`の代わりに`Customers`します。  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
