---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: c4069ef760877935c4ce194144d131d0dc58b4d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504357"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
LINQ to DataSet と簡単にキャッシュされているデータに対するクエリを高速化、<xref:System.Data.DataSet>オブジェクト。 具体的には、LINQ to DataSet は、個別のクエリ言語を使用して、クエリの代わりに、プログラミング言語そのものを記述できるので、クエリを簡略化します。 これは、コンパイル時の構文チェック、静的な型指定、およびそのクエリで Visual Studio によって提供される IntelliSense サポートのメリットを得ることができます、Visual Studio 開発者に特に便利です。  
  
 LINQ to DataSet も使用できますを 1 つまたは複数のデータ ソースから統合されているデータに対してクエリを実行します。 これにより、ローカルに集計されたデータのクエリや Web アプリケーションでの中間層のキャッシュなど、データの表現方法や扱いに柔軟性が要求されるさまざまなシナリオが実現します。 特に、汎用のレポート作成、分析、ビジネス インテリジェンスを行うアプリケーションでは、この手法を用いたデータ操作が欠かせません。  
  
 LINQ to DataSet 機能は、拡張メソッドによって主に公開される、<xref:System.Data.DataRowExtensions>と<xref:System.Data.DataTableExtensions>クラス。 LINQ to DataSet は、に基づいておよび既存の ADO.NET アーキテクチャを使用して、アプリケーション コードで ADO.NET を置換するものではありません。 既存の ADO.NET コードでは、引き続き、LINQ to DataSet のアプリケーションで機能します。 LINQ to DataSet ADO.NET とデータ ストアへのリレーションシップは、次の図に示します。  
  
 ![LINQ to DataSet が ADO.NET プロバイダーに基づくされていることを示す図。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [プログラミング ガイド](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>参照  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>関連項目

- [統合言語クエリ (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [統合言語クエリ (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ と ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
