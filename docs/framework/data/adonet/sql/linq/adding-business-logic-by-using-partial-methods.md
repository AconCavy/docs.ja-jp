---
title: 部分メソッドによるビジネス ロジックの追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: ed440f3315fc25e82b648f21410acb7a2c2a08f9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743666"
---
# <a name="adding-business-logic-by-using-partial-methods"></a>部分メソッドによるビジネス ロジックの追加
Visual Basic をカスタマイズすることができますとC#でコードを生成、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]を使用してプロジェクト*部分メソッド*します。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] から生成されるコードでは、シグネチャが部分メソッドの一部として定義されています。 このメソッドを実装する場合に、独自の部分メソッドを追加できます。 独自の実装を追加しない場合は、コンパイラで部分メソッドのシグネチャが破棄され、既定のメソッドが [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で呼び出されます。  
  
> [!NOTE]
>  Visual Studio を使用している場合は、エンティティ クラスに検証およびその他のカスタマイズを追加するオブジェクト リレーショナル デザイナーを使用できます。  
  
 たとえば、Northwind サンプル データベースの `Customer` クラスに対する既定の対応付けには次の部分メソッドが含まれます。  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 次のようなコードを独自の部分 `Customer` クラスに追加することで、独自のメソッドを実装できます。  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 このアプローチはで通常使用される[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]の既定のメソッドをオーバーライドする`Insert`、 `Update`、 `Delete`、およびオブジェクトのライフ サイクル イベント時にプロパティを検証します。  
  
 詳細については、次を参照してください。[部分メソッド](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)(Visual Basic) または[partial (メソッド) (C#リファレンス)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#)。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、SQLMetal などのコード生成ツールによって定義される `ExampleClass` を最初に示し、次に 2 つのメソッドの 1 つだけを実装できることを示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、`Shipper` エンティティと `Order` エンティティのリレーションシップを使用します。 メソッドには部分メソッドの `InsertShipper` と `DeleteShipper` が含まれています。 これらのメソッドによって提供される既定の部分メソッドをオーバーライドする[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]マッピングします。  
  
### <a name="code"></a>コード  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [データの変更と変更の送信](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [挿入、更新、および削除の各操作のカスタマイズ](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
