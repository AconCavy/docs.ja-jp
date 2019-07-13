---
title: LINQ to SQL オブジェクト モデル
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: de3fc8b23bd132179fc7fb67d29010552138e3ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742832"
---
# <a name="the-linq-to-sql-object-model"></a>LINQ to SQL オブジェクト モデル
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]開発者のプログラミング言語で表されるオブジェクト モデルはリレーショナル データベースのデータ モデルにマップされます。 データ操作はオブジェクト モデルに従って行われます。  
  
 このシナリオでは、データベースに対してデータベース コマンド (`INSERT` など) を実行する必要はありません。 代わりに、オブジェクト モデル内で値を変更し、メソッドを実行します。 データベースに対してクエリを実行したり、変更を送信する必要がある場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、要求を正しい SQL コマンドに変換し、そのコマンドをデータベースに送信します。  
  
 ![Linq のオブジェクト モデルを示すスクリーン ショット。](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 内の最も基本的な要素、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクト モデルとリレーショナル データ モデル内の要素との関係は、次の表に集計されます。  
  
|LINQ to SQL オブジェクト モデル|リレーショナル データ モデル|  
|------------------------------|---------------------------|  
|エンティティ クラス|テーブル|  
|クラス メンバー|Column|  
|関連付け|外部キー リレーションシップ|  
|メソッド|ストアド プロシージャまたは関数|  
  
> [!NOTE]
>  次の説明は、リレーショナル データ モデルと規則に関する基本的な知識があることが前提です。  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ to SQL エンティティ クラスおよびデータベース テーブル  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、データベース テーブルで表現され、*エンティティ クラス*します。 エンティティ クラスは、作成する他のクラスに似ていますが、クラスをデータベース テーブルに関連付ける特別な情報を使用して、クラスに注釈を付ける点が異なります。 次の例に示すように、クラス宣言にカスタム属性 (<xref:System.Data.Linq.Mapping.TableAttribute>) を追加することによって、この注釈を付けます。  
  
### <a name="example"></a>例  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 テーブルとして宣言されたクラスのインスタンスのみ (つまり、エンティティ クラス)、データベースに保存できます。  
  
 詳細については、の テーブルの属性」セクションを参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)します。  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>LINQ to SQL クラス メンバーおよびデータベース列  
 クラスとテーブルの関連付けに加えて、フィールドまたはプロパティを設定してデータベース列を表すことができます。 このためには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の例に示すように <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性を定義します。  
  
### <a name="example"></a>例  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 列に対応付けられたフィールドおよびプロパティのみ、データベースに保持したり、データベースから取得できます。 列として宣言されていないものは、アプリケーション ロジックの一時的な部分と見なされます。  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性にはさまざまなプロパティがあり、これを使用することで、列を表すメンバーをカスタマイズできます (たとえば、主キー列を表すメンバーを指定できます)。 詳細については、の 列の属性」セクションを参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)します。  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>LINQ to SQL の関連付けおよびデータベースの外部キー リレーションシップ  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、適用することで (外部キーと主キーのリレーションシップ) などのデータベースの関連付けを表す、<xref:System.Data.Linq.Mapping.AssociationAttribute>属性。 次のコード セグメントで、`Order`クラスが含まれています、`Customer`プロパティを持つ、<xref:System.Data.Linq.Mapping.AssociationAttribute>属性。 このプロパティとその属性が、`Order` クラスおよび `Customer` クラスとのリレーションシップを提供します。  
  
 `Customer` クラスの `Order` プロパティを表示する方法を次の例に示します。  
  
### <a name="example"></a>例  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 詳細については、の「Association Attribute」セクションを参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)します。  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>LINQ to SQL メソッドおよびデータベース ストアド プロシージャ  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、ストアド プロシージャとユーザー定義関数をサポートしています。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、それらをクライアント コードから厳密に型指定された方法でアクセスできるように、クライアント オブジェクトにこれらのデータベースによる抽象化をマップします。 メソッド シグネチャは、データベース内で定義されているプロシージャおよび関数のシグネチャと可能な限りよく似ています。 IntelliSense を使用して、これらのメソッドを見つけることができます。  
  
 呼び出しによって対応するプロシージャに返される結果セットは、厳密に型指定されたコレクションです。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、<xref:System.Data.Linq.Mapping.FunctionAttribute> 属性と <xref:System.Data.Linq.Mapping.ParameterAttribute> 属性を使用して、ストアド プロシージャおよび関数をメソッドに対応付けます。 ストアド プロシージャを表すメソッドは、<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> プロパティによって、ユーザー定義関数を表すメソッドと区別されます。 このプロパティが `false` (既定値) に設定されている場合、メソッドはストアド プロシージャを表します。 `true` に設定されている場合、メソッドはデータベース関数を表します。  
  
> [!NOTE]
>  Visual Studio を使用している場合は、ストアド プロシージャおよびユーザー定義関数にマップされるメソッドを作成するオブジェクト リレーショナル デザイナーを使用できます。  
  
### <a name="example"></a>例  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 詳細については、関数の属性、Stored Procedure Attribute」、およびパラメーターの属性のセクションを参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)と[Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)します。  
  
## <a name="see-also"></a>関連項目

- [属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
