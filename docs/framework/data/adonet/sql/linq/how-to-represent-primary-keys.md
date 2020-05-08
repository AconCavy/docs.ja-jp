---
title: '方法: 主キーを表す'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 5df82292f000d7f5e61cab699237b86de30bda70
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793432"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="0fa54-102">方法: 主キーを表す</span><span class="sxs-lookup"><span data-stu-id="0fa54-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="0fa54-103">データベース列の主キーを表すプロパティまたはフィールドを指定するには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性の <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="0fa54-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="0fa54-104">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fa54-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0fa54-105">では、計算列は主キーとしてサポートされません。</span><span class="sxs-lookup"><span data-stu-id="0fa54-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="0fa54-106">プロパティまたはフィールドを主キーとして指定するには</span><span class="sxs-lookup"><span data-stu-id="0fa54-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="0fa54-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="0fa54-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="0fa54-108">値として `true` を指定します。</span><span class="sxs-lookup"><span data-stu-id="0fa54-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fa54-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fa54-109">See also</span></span>

- [<span data-ttu-id="0fa54-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="0fa54-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="0fa54-111">方法: コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="0fa54-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
