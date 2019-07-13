---
title: 基本データ型
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: 6e1e48b3d390cf7c8ec81735b9637f706ad3a0ad
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306263"
---
# <a name="basic-data-types"></a>基本データ型
LINQ to SQL クエリは、Microsoft SQL Server で実行される前に Transact-SQL に変換されるため、 LINQ to SQL は、SQL Server が基本データ型に対してサポートするのと同じ組み込み機能の多くをサポートします。  
  
## <a name="casting"></a>キャスト  
 SQL Server 内に同様の有効な変換が存在する場合は、変換元の CLR 型から変換先の CLR 型への暗黙的または明示的なキャストが有効になります。 CLR キャストの詳細については、次を参照してください。 [CType Function](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) と[型検査および変換演算子](~/docs/csharp/language-reference/operators/type-testing-and-conversion-operators.md)します。 変換後、CLR 式に対して実行される操作の動作は、変換先の型に通常割り当てられる他の CLR 式の動作と一致するように、キャストによって変更されます。 継承の割り当てのコンテキストにおいてもキャストは変換可能です。 より厳密なエンティティ サブタイプにオブジェクトを変換して、そのサブタイプに固有のデータへのアクセスを可能にすることができます。  
  
## <a name="equality-operators"></a>等値演算子  
 LINQ to SQL は、LINQ to SQL クエリ内の基本データ型で次の等値演算子をサポートします。  
  
- 等しいと非等値演算子。数値、等値演算子および非等値演算子がサポートされている<xref:System.Boolean>、 <xref:System.DateTime>、および<xref:System.TimeSpan>型。 詳細については、Visual Basic の演算子は`=`と`<>`を参照してください[比較演算子](~/docs/visual-basic/language-reference/operators/comparison-operators.md)します。 詳細についてはC#比較演算子`==`と`!=`を参照してください[等値演算子](~/docs/csharp/language-reference/operators/equality-operators.md)します。
  
- 演算子を示します。`IS`継承のマッピングが使用されているときに、演算子がサポートされている変換します。 これは、オブジェクトが特定の種類のエンティティであるかどうかを検査する場合に、判別列を直接調べる代わりとして使用でき、判別列のチェックに変換されます。 Visual Basic の詳細については、 C# Is 演算子を参照してください[Is 演算子](~/docs/visual-basic/language-reference/operators/is-operator.md)と[は](~/docs/csharp/language-reference/operators/type-testing-and-conversion-operators.md#is-operator)します。  
  
## <a name="see-also"></a>関連項目

- [SQL と CLR の型マッピング](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [データ型と関数](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
