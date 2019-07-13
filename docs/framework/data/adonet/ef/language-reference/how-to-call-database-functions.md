---
title: '方法: データベース関数を呼び出す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: 5990e9f4c08eafeae6bed18d3d8af0617b84ff54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774596"
---
# <a name="how-to-call-database-functions"></a>方法: データベース関数を呼び出す
<xref:System.Data.Objects.SqlClient.SqlFunctions> クラスには、LINQ to Entities クエリで使用する SQL Server 関数を公開するメソッドが含まれています。 LINQ to Entities クエリで <xref:System.Data.Objects.SqlClient.SqlFunctions> メソッドを使用すると、対応するデータベース関数がデータベースで実行されます。  
  
> [!NOTE]
>  値のセットに対して計算を実行して 1 つの値を返すデータベース関数 (集計データベース関数とも呼ばれる) は、直接呼び出すことができます。 他の正規関数は、LINQ to Entities クエリの一部としてしか呼び出すことができません。 集計関数を直接呼び出すには、その関数に <xref:System.Data.Objects.ObjectQuery%601> を渡す必要があります。 詳細については、以下の 2 番目の例を参照してください。  
  
> [!NOTE]
>  <xref:System.Data.Objects.SqlClient.SqlFunctions> クラスのメソッドは、SQL Server 関数に固有です。 他のプロバイダーから、データベース関数を公開する同様のクラスを入手できることがあります。  
  
## <a name="example"></a>例  
 次の例では、 [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)します。 この例では、<xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> メソッドを使用する LINQ to Entities クエリを実行して、姓が "Si" で始まる連絡先をすべて返します。  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>例  
 次の例では、 [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)します。 この例では、集計 <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> メソッドを直接呼び出します。 <xref:System.Data.Objects.ObjectQuery%601> は関数に渡されているため、LINQ to Entities クエリに含まれていなくても呼び出すことができる点に注意してください。  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [LINQ to Entities クエリ内の関数の呼び出し](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [LINQ to Entities でのクエリ](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
