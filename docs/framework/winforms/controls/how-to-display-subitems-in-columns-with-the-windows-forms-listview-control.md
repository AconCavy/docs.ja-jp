---
title: ListView コントロールを使用して列にサブ項目を表示する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745545"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="6e489-102">方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する</span><span class="sxs-lookup"><span data-stu-id="6e489-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="6e489-103">Windows フォーム <xref:System.Windows.Forms.ListView> コントロールでは、詳細ビューの各項目に対して追加のテキスト (サブ項目) を表示できます。</span><span class="sxs-lookup"><span data-stu-id="6e489-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="6e489-104">最初の列には、従業員番号などの項目のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6e489-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="6e489-105">2番目、3番目、およびそれ以降の列には、最初、2番目、およびそれ以降の関連するサブ項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6e489-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="6e489-106">リスト項目にサブ項目を追加するには</span><span class="sxs-lookup"><span data-stu-id="6e489-106">To add subitems to a list item</span></span>  
  
1. <span data-ttu-id="6e489-107">必要な列を追加します。</span><span class="sxs-lookup"><span data-stu-id="6e489-107">Add any columns needed.</span></span> <span data-ttu-id="6e489-108">最初の列には項目の <xref:System.Windows.Forms.ListView.Text%2A> プロパティが表示されるので、サブ項目の数よりも1つ多い列が必要です。</span><span class="sxs-lookup"><span data-stu-id="6e489-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="6e489-109">列の追加の詳細については、「[方法: Windows フォーム ListView コントロールに列を追加](how-to-add-columns-to-the-windows-forms-listview-control.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e489-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2. <span data-ttu-id="6e489-110">項目の <xref:System.Windows.Forms.ListViewItem.SubItems%2A> プロパティによって返されるコレクションの <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6e489-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="6e489-111">次のコード例では、リストアイテムの従業員名と部署を設定します。</span><span class="sxs-lookup"><span data-stu-id="6e489-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="6e489-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e489-112">See also</span></span>

- [<span data-ttu-id="6e489-113">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="6e489-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="6e489-114">方法: Windows フォーム ListView コントロールで項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="6e489-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="6e489-115">方法: Windows フォーム ListView コントロールに列を追加する</span><span class="sxs-lookup"><span data-stu-id="6e489-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="6e489-116">方法: Windows フォーム ListView コントロールのアイコンを表示する</span><span class="sxs-lookup"><span data-stu-id="6e489-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="6e489-117">方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する</span><span class="sxs-lookup"><span data-stu-id="6e489-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
