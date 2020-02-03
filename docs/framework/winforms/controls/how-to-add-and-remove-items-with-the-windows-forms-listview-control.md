---
title: ListView コントロールを使用して項目を追加および削除する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: bbfe99db857ebe3a80bf99926f3ce0bec38a1f3f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743136"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="78ddf-102">方法 : Windows フォーム ListView コントロールで項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="78ddf-102">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="78ddf-103">項目を Windows フォーム <xref:System.Windows.Forms.ListView> コントロールに追加するプロセスは、主に項目を指定し、プロパティを割り当てることによって構成されます。</span><span class="sxs-lookup"><span data-stu-id="78ddf-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="78ddf-104">リスト項目の追加または削除は、いつでも行うことができます。</span><span class="sxs-lookup"><span data-stu-id="78ddf-104">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="78ddf-105">プログラムによって項目を追加するには</span><span class="sxs-lookup"><span data-stu-id="78ddf-105">To add items programmatically</span></span>  
  
1. <span data-ttu-id="78ddf-106"><xref:System.Windows.Forms.ListView.Items%2A> プロパティの <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="78ddf-106">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="78ddf-107">プログラムによって項目を削除するには</span><span class="sxs-lookup"><span data-stu-id="78ddf-107">To remove items programmatically</span></span>  
  
1. <span data-ttu-id="78ddf-108"><xref:System.Windows.Forms.ListView.Items%2A> プロパティの <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> または <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="78ddf-108">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="78ddf-109"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> メソッドは、1つの項目を削除します。<xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> メソッドは、リストからすべての項目を削除します。</span><span class="sxs-lookup"><span data-stu-id="78ddf-109">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="78ddf-110">参照</span><span class="sxs-lookup"><span data-stu-id="78ddf-110">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="78ddf-111">ListView コントロール</span><span class="sxs-lookup"><span data-stu-id="78ddf-111">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="78ddf-112">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="78ddf-112">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
