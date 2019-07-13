---
title: Entity Data Model:プリミティブ データ型
ms.date: 03/30/2017
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
ms.openlocfilehash: 044a0ed981bb9cda3550fb3a3a9f1cb9bff96f25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667133"
---
# <a name="entity-data-model-primitive-data-types"></a>Entity Data Model:プリミティブ データ型
Entity Data Model (EDM) は、一連の定義に使用される抽象プリミティブ データ型 (文字列、ブール値、Int32 など) をサポートしている[プロパティ](../../../../docs/framework/data/adonet/property.md)概念モデル。 これらのプリミティブ データ型は、SQL Server データベースや共通言語ランタイム (CLR) などのストレージ環境またはホスト環境でサポートされる、実際のプリミティブ データ型のプロキシです。 EDM では、プリミティブ データ型に対する演算や変換のセマンティクスを定義していません。これらのセマンティクスは、ストレージ環境またはホスト環境で定義されます。 通常、EDM のプリミティブ データ型は、ストレージ環境またはホスト環境の対応プリミティブ データ型にマップされます。 Entity Framework が EDM のプリミティブ型を SQL Server データ型にマップする方法については、次を参照してください。[エンティティ FrameworkTypes 用 SqlClient](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)します。  
  
> [!NOTE]
>  EDM では、プリミティブ データ型のコレクションをサポートしていません。  
  
 EDM の構造化されたデータ型については、次を参照してください。[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)と[複合型](../../../../docs/framework/data/adonet/complex-type.md)します。  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Entity Data Model でサポートされるプリミティブ データ型  
 下の表は、EDM でサポートされるプリミティブ データ型の一覧を示します。 テーブルの一覧も、[ファセット](../../../../docs/framework/data/adonet/facet.md)各プリミティブ データ型に適用できます。  
  
|プリミティブ データ型|説明|使用できるファセット|  
|-------------------------|-----------------|-----------------------|  
|2 項|バイナリ データを格納します。|MaxLength、FixedLength、Nullable、Default|  
|Boolean|`true` または `false` の値を格納します。|Nullable、Default|  
|Byte|符号なし 8 ビット整数値を格納します。|Precision、Nullable、Default|  
|DateTime|日時を表します。|Precision、Nullable、Default|  
|DateTimeOffset|GMT からのオフセット (分単位) としての日時を格納します。|Precision、Nullable、Default|  
|Decimal (10 進数型)|有効桁数と小数点以下桁数が固定長の数値を格納します。|Precision、Nullable、Default|  
|Double (倍精度浮動小数点型)|15 桁の有効桁数を持つ浮動小数点数を格納します。|Precision、Nullable、Default|  
|Float|7 桁の有効桁数を持つ浮動小数点数を格納します。|Precision、Nullable、Default|  
|Guid|16 バイトの一意識別子を格納します。|Precision、Nullable、Default|  
|Int16|符号付き 16 ビット整数値を格納します。|Precision、Nullable、Default|  
|Int32|符号付き 32 ビット整数値を格納します。|Precision、Nullable、Default|  
|Int64|符号付き 64 ビット整数値を格納します。|Precision、Nullable、Default|  
|SByte|符号付き 8 ビット整数値を格納します。|Precision、Nullable、Default|  
|String|文字データを格納します。|Unicode、FixedLength、MaxLength、Collation、Precision、Nullable、Default|  
|時刻|時刻を格納します。|Precision、Nullable、Default|  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
