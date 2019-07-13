---
title: '方法: コンカレンシーの競合を検査するメンバーを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: 9a1b4ab2dc28c569473eddbf50b96d10298d8d3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902734"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>方法: コンカレンシーの競合を検査するメンバーを指定する
3 つの列挙型のいずれかの適用、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>オプティミスティック同時実行競合の検出の更新プログラムに含まれるメンバーを指定する属性を確認します。  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ (デザイン時に設定) は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の実行時の同時実行機能と一緒に使用されます。 詳細については、次を参照してください。[オプティミスティック同時実行制御。概要](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)します。  
  
> [!NOTE]
>  `IsVersion=true` として指定されているメンバーがない限り、元のメンバーの各値は、データベースの現在の状態と比較されます。 詳細については、「 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 」を参照してください。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>」を参照してください。  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>競合の検出でこのメンバーを常に使用するには  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ値を `Always` に設定します。  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>競合の検出でこのメンバーを使用しないようにするには  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ値を `Never` に設定します。  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>アプリケーションでメンバーの値が変更された場合にのみ、競合の検出でこのメンバーを使用するには  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ値を `WhenChanged` に設定します。  
  
## <a name="example"></a>例  
 次の例では、更新チェックで `HomePage` オブジェクトが検査されないように指定しています。 詳細については、「 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 」を参照してください。  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [方法: 変更の競合を管理します。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [データの変更と変更の送信](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
