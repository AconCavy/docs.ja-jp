---
title: '方法: データベース データ型を指定する'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: f070ff718ac10b9681c5ab3c0f4b46547349101b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197236"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="03019-102">方法: データベース データ型を指定する</span><span class="sxs-lookup"><span data-stu-id="03019-102">How to: Specify Database Data Types</span></span>

<span data-ttu-id="03019-103">T-SQL テーブル宣言の列を定義する正確なテキストを指定するには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性の <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="03019-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="03019-104"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> プロパティは、<xref:System.Data.Linq.DataContext.CreateDatabase%2A> を使用してデータベースのインスタンスを作成することを予定している場合のみ指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03019-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="03019-105">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03019-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="03019-106">データ型を T-SQL テーブルに定義するテキストを指定するには</span><span class="sxs-lookup"><span data-stu-id="03019-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="03019-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="03019-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="03019-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> プロパティの値を T-SQL で使用される正確なテキストに設定します。</span><span class="sxs-lookup"><span data-stu-id="03019-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03019-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="03019-109">See also</span></span>

- [<span data-ttu-id="03019-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="03019-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="03019-111">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="03019-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
