---
title: '方法: ScrollViewer のコンテンツ スクロール メソッドを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: e81c63de16d09de8435d5ec49a013bf8dc5927cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697306"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a><span data-ttu-id="423ea-102">方法: ScrollViewer のコンテンツ スクロール メソッドを使用する</span><span class="sxs-lookup"><span data-stu-id="423ea-102">How to: Use the Content-Scrolling Methods of ScrollViewer</span></span>
<span data-ttu-id="423ea-103">この例は、<xref:System.Windows.Controls.ScrollViewer> 要素のスクロール メソッドを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="423ea-103">This example shows how to use the scrolling methods of the <xref:System.Windows.Controls.ScrollViewer> element.</span></span> <span data-ttu-id="423ea-104">これらのメソッドにより、<xref:System.Windows.Controls.ScrollViewer> での、行またはページごとのコンテンツの増分スクロールが可能になります。</span><span class="sxs-lookup"><span data-stu-id="423ea-104">These methods provide incremental scrolling of content, either by line or by page, in a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="423ea-105">例</span><span class="sxs-lookup"><span data-stu-id="423ea-105">Example</span></span>  
 <span data-ttu-id="423ea-106">次の例は、子 <xref:System.Windows.Controls.TextBlock> 要素をホストする `sv1` という名前の <xref:System.Windows.Controls.ScrollViewer> を作成しています。</span><span class="sxs-lookup"><span data-stu-id="423ea-106">The following example creates a <xref:System.Windows.Controls.ScrollViewer> named `sv1`, which hosts a child <xref:System.Windows.Controls.TextBlock> element.</span></span> <span data-ttu-id="423ea-107"><xref:System.Windows.Controls.TextBlock> が親 <xref:System.Windows.Controls.ScrollViewer> より大きいため、スクロールを有効にするためのスクロール バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="423ea-107">Because the <xref:System.Windows.Controls.TextBlock> is larger than the parent <xref:System.Windows.Controls.ScrollViewer>, scroll bars appear in order to enable scrolling.</span></span> <span data-ttu-id="423ea-108">さまざまなスクロール メソッドを表す <xref:System.Windows.Controls.Button> 要素は、左側に個別の <xref:System.Windows.Controls.StackPanel> としてドッキングされます。</span><span class="sxs-lookup"><span data-stu-id="423ea-108"><xref:System.Windows.Controls.Button> elements that represent the various scrolling methods are docked on the left in a separate <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="423ea-109">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル内の各 <xref:System.Windows.Controls.Button> は、<xref:System.Windows.Controls.ScrollViewer> のスクロール動作を制御する、関連のカスタム メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="423ea-109">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file calls a related custom method that controls scrolling behavior in <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 [!code-xaml[ScrollViewerMethods#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="423ea-110">次の例では、<xref:System.Windows.Controls.ScrollViewer.LineUp%2A> メソッドと <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="423ea-110">The following example uses the <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> and <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> methods.</span></span>  
  
 [!code-csharp[ScrollViewerMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="423ea-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="423ea-111">See also</span></span>

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.StackPanel>
