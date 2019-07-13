---
title: データ メンバーの既定値
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
ms.openlocfilehash: af8fff9d034f8dea4ce9f24a2bda042b5b9708a9
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881267"
---
# <a name="data-member-default-values"></a>データ メンバーの既定値
.NET framework では、型がの概念をある*既定値*します。 たとえば、参照型の既定値は `null` で、整数型の既定値は 0 です。 しかし、データ メンバーが既定値に設定されている場合は、シリアル化されたデータからそのデータ メンバーを省略することが望ましいことがあります。 それは、メンバーが既定値に設定されているために実際の値をシリアル化する必要がなく、パフォーマンスの点で有利だからです。  
  
 シリアル化されたデータからデータ メンバーを省略するには、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティを `false` に設定します (既定値は `true`)。  
  
> [!NOTE]
>  相互運用性の維持やデータ サイズの縮小のような特別なニーズがある場合は、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> プロパティを `false` に設定する必要があります。  
  
## <a name="example"></a>例  
 次のコードには、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> が `false` に設定された複数のメンバーが含まれています。  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 このクラスのインスタンスをシリアル化すると、次に示すように `employeeName` と `employeeID` がシリアル化されます。 `employeeName` の null 値と `employeeID` の値 0 は、シリアル化されるデータに明示的に含められます。 ただし、`position`、`salary`、および `bonus` のメンバーはシリアル化されません。 また、`targetSalary` プロパティは <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> に設定されていますが、57800 が .NET の整数の既定値 (0) と一致しないため、`false` が通常どおりにシリアル化されます。  
  
### <a name="xml-representation"></a>XML 表現  
 前の例を XML にシリアル化すると、生成される XML 表現は次のようになります。  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil` 属性は W3C (World Wide Web Consortium) XML スキーマ インスタンス名前空間の特別な属性であり、null 値を明示的に表すための相互運用可能な方法を提供します。 この XML には、地位、給与、ボーナスの各データ メンバーに関する情報がまったく含まれていないことに注目してください。 これらのデータ メンバーは、受信エンドポイントで、それぞれ `null`、0、および `null` として解釈します。 これらをサードパーティ製のデシリアライザーで正しく解釈できる保証はないため、このパターンはお勧めしません。 <xref:System.Runtime.Serialization.DataContractSerializer> クラスを使用すると、値が指定されていない場合でも、常に正しい解釈が選択されます。  
  
### <a name="interaction-with-isrequired"></a>IsRequired との対話  
 説明したよう[データ コントラクトのバージョン管理](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)、<xref:System.Runtime.Serialization.DataMemberAttribute>属性が、<xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>プロパティ (既定値は`false`)。 このプロパティは、シリアル化されたデータを逆シリアル化する際に、指定されたデータ メンバーが存在する必要があるかどうかを示します。 `IsRequired` が `true` (値が存在する必要がある) に設定され、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> が `false` (既定値に設定されている場合は、値が存在する必要がない) に設定されている場合は、結果が矛盾するため、このデータ メンバーの既定値をシリアル化できません。 このようなデータ メンバーを既定値 (通常は `null` または 0) に設定してシリアル化を実行すると、<xref:System.Runtime.Serialization.SerializationException> がスローされます。  
  
### <a name="schema-representation"></a>スキーマ表現  
 データ メンバーの XML スキーマ定義言語 (XSD) スキーマ表現の詳細と、`EmitDefaultValue`プロパティに設定されて`false`は、後ほど[Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)します。 以下に、その概要を簡単に説明します。  
  
- ときに、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>に設定されている`false`、Windows Communication Foundation (WCF) に固有の注釈としてスキーマで表されます。 この情報を表すための相互運用可能な方法はありません。 特に、スキーマにおける "default" 属性はこの目的では使用されません。また、`minOccurs` 属性は <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 設定だけに影響され、`nillable` 属性はデータ メンバーの型だけに影響されます。  
  
- 使用される実際の既定値は、スキーマには存在しません。 指定されていない要素が適切に解釈されるかどうかは、受信エンドポイントに依存します。  
  
 スキーマのインポート、<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>プロパティが自動的に設定`false`たびに説明したように WCF 固有の注釈が検出されます。 設定されている`false`が参照型の場合、`nillable`プロパティに設定`false`ASP.NET Web サービスを使用する場合によく発生する特定の相互運用シナリオをサポートします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
