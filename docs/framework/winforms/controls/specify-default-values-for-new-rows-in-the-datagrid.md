---
title: DataGridView コントロールの新しい行に既定値を指定する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742933"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d91ae-102">方法 : Windows フォーム DataGridView コントロールの新しい行に既定値を指定する</span><span class="sxs-lookup"><span data-stu-id="d91ae-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d91ae-103">新しく追加された行に対してアプリケーションで既定値がいっぱいになったときに、データエントリをより使いやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="d91ae-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="d91ae-104"><xref:System.Windows.Forms.DataGridView> クラスを使用すると、<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> イベントに既定値を入力できます。</span><span class="sxs-lookup"><span data-stu-id="d91ae-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="d91ae-105">このイベントは、ユーザーが新しいレコードの行を入力したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="d91ae-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="d91ae-106">コードでこのイベントを処理する場合は、目的のセルに選択した値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="d91ae-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="d91ae-107">次のコード例では、<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> イベントを使用して、新しい行に既定値を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d91ae-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d91ae-108">使用例</span><span class="sxs-lookup"><span data-stu-id="d91ae-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d91ae-109">コードのコンパイル方法</span><span class="sxs-lookup"><span data-stu-id="d91ae-109">Compiling the Code</span></span>  
 <span data-ttu-id="d91ae-110">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d91ae-110">This example requires:</span></span>  
  
- <span data-ttu-id="d91ae-111">`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="d91ae-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="d91ae-112">一意の `CustomerID` 値を生成するための `NewCustomerId` 関数。</span><span class="sxs-lookup"><span data-stu-id="d91ae-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
- <span data-ttu-id="d91ae-113"><xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="d91ae-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d91ae-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d91ae-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="d91ae-115">Windows フォーム DataGridView コントロールでのデータ入力</span><span class="sxs-lookup"><span data-stu-id="d91ae-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d91ae-116">Windows フォーム DataGridView コントロールにおける新規レコード行の使用</span><span class="sxs-lookup"><span data-stu-id="d91ae-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
