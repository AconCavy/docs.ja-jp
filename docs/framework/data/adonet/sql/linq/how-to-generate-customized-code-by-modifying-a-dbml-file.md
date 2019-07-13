---
title: '方法: DBML ファイルを変更してカスタマイズ コードを生成する'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: c3fa4d9db4076309ab7d6066cc7072797eaead54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877345"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>方法: DBML ファイルを変更してカスタマイズ コードを生成する
Visual Basic を生成するか、C#データベース マークアップ言語 (.dbml) メタデータ ファイルからソース コード。 この方法を使用すると、アプリケーション マッピング コードを生成する前に、既定の .dbml ファイルをカスタマイズできます。 これは高度な機能です。  
  
 実行手順は次のとおりです。  
  
1. .dbml ファイルを生成します。  
  
2. エディターを使用して .dbml ファイルを変更します。 .Dbml ファイルは、用のスキーマ定義 (.xsd) ファイルに対して検証する必要がありますので注意[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].dbml ファイル。 詳細については、次を参照してください。 [LINQ to SQL でのコード生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)します。  
  
3. Visual Basic を生成またはC#ソース コード。  
  
 次の例では、SQLMetal コマンド ライン ツールを使用します。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次のコードでは、Northwind サンプル データベースから .dbml ファイルを生成します。 データベース メタデータのソースとして、データベースの名前または .mdf ファイルの名前を使用します。  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>例  
 次のコードは Visual Basic またはC#.dbml ファイルからソース コード ファイル。  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL でのコード生成](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [オブジェクト モデルの作成](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
