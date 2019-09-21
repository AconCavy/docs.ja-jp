---
title: '方法: Visual Basic または C# でオブジェクト モデルを生成する'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 07df915b5c826c7b82f2aaf16fcc22da0361d5f6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781914"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>方法: Visual Basic または C でオブジェクトモデルを生成する\#
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、使用しているプログラミング言語のオブジェクト モデルが、リレーショナル データベースに対応付けられています。 既存のデータベースのメタデータから Visual Basic またはC#モデルを自動的に生成するために、2つのツールを使用できます。  
  
- Visual Studio を使用している場合は、オブジェクトリレーショナルデザイナーを使用してオブジェクトモデルを生成できます。 O/R デザイナーには、オブジェクトモデルを[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]生成するのに役立つ豊富なユーザーインターフェイスが用意されています。 詳細については、「 [Visual Studio の Linq TO SQL ツール](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)」を参照してください。
  
- SQLMetal コマンド ライン ツール。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
    > [!NOTE]
    > 既存のデータベースがなく、オブジェクト モデルからデータベースを作成する場合は、コード エディターと <xref:System.Data.Linq.DataContext.CreateDatabase%2A> を使用してオブジェクト モデルを作成できます。 詳細については、「[方法 :データベース](how-to-dynamically-create-a-database.md)を動的に作成します。  
  
 O/R デザイナーのドキュメントでは、O/R デザイナーを使用しC#て Visual Basic またはオブジェクトモデルを生成する方法の例を示します。 以下の情報は、SQLMetal コマンド ライン ツールの使用方法の例です。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例に示す SQLMetal コマンドラインでは、Northwind サンプルデータベースの属性ベースのオブジェクトモデルとして Visual Basic コードが生成されます。 ストアド プロシージャと関数も含まれます。  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>例  
 次の例に示す SQLMetal コマンド ラインでは、Northwind サンプル データベースの属性ベースのオブジェクト モデルとして C# コードが生成されます。 ストアド プロシージャと関数も含まれ、テーブル名は自動的に複数化されます。  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>関連項目

- [プログラミング ガイド](programming-guide.md)
- [LINQ to SQL オブジェクト モデル](the-linq-to-sql-object-model.md)
- [チュートリアルによる学習](learning-by-walkthroughs.md)
- [方法: コードエディターを使用してエンティティクラスをカスタマイズする](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [属性ベースの対応付け](attribute-based-mapping.md)
- [SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [外部マップ](external-mapping.md)
- [サンプル データベースのダウンロード](downloading-sample-databases.md)
- [オブジェクト モデルの作成](creating-the-object-model.md)
