---
title: '方法: 要素に装飾をバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: e8c7eb929042bfe1455bfc9bf459fc466de5c397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923493"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="a5e99-102">方法: 要素に装飾をバインドする</span><span class="sxs-lookup"><span data-stu-id="a5e99-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="a5e99-103">この例では、指定した <xref:System.Windows.UIElement> にプログラムで装飾をバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a5e99-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5e99-104">例</span><span class="sxs-lookup"><span data-stu-id="a5e99-104">Example</span></span>  
 <span data-ttu-id="a5e99-105">特定の <xref:System.Windows.UIElement> に装飾をバインドするには、次の手順を行います。</span><span class="sxs-lookup"><span data-stu-id="a5e99-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="a5e99-106">`static` メソッド <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> を呼び出して、装飾対象となる <xref:System.Windows.UIElement> の <xref:System.Windows.Documents.AdornerLayer> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="a5e99-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="a5e99-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> は、指定した **UIElement** を起点としてビジュアル ツリーを上に探索し、最初に見つかった装飾層を返します。</span><span class="sxs-lookup"><span data-stu-id="a5e99-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="a5e99-108">(装飾層が見つからない場合、メソッドにより null が返されます)。</span><span class="sxs-lookup"><span data-stu-id="a5e99-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="a5e99-109"><xref:System.Windows.Documents.AdornerLayer.Add%2A> メソッドを呼び出して、対象の **UIElement** に装飾をバインドします。</span><span class="sxs-lookup"><span data-stu-id="a5e99-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="a5e99-110">次の例では、SimpleCircleAdorner (上図参照) を *myTextBox* という名前の <xref:System.Windows.Controls.TextBox> にバインドします。</span><span class="sxs-lookup"><span data-stu-id="a5e99-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> <span data-ttu-id="a5e99-111">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a5e99-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e99-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5e99-112">See also</span></span>

- [<span data-ttu-id="a5e99-113">装飾の概要</span><span class="sxs-lookup"><span data-stu-id="a5e99-113">Adorners Overview</span></span>](adorners-overview.md)
