---
title: '方法: ルーティング イベントを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: edb3d6724af89b7e85986c50b579084e3c4e5070
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001508"
---
# <a name="how-to-handle-a-routed-event"></a><span data-ttu-id="361f2-102">方法: ルーティング イベントを処理する</span><span class="sxs-lookup"><span data-stu-id="361f2-102">How to: Handle a Routed Event</span></span>
<span data-ttu-id="361f2-103">バブル イベントの動作と、ルーティング イベント データを処理できるハンドラーを作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="361f2-103">This example shows how bubbling events work and how to write a handler that can process the routed event data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="361f2-104">例</span><span class="sxs-lookup"><span data-stu-id="361f2-104">Example</span></span>  
 <span data-ttu-id="361f2-105">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、要素は、要素ツリー構造体に配置されます。</span><span class="sxs-lookup"><span data-stu-id="361f2-105">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elements are arranged in an element tree structure.</span></span> <span data-ttu-id="361f2-106">親要素は、要素ツリー内で最初に子要素が発生させたイベントの処理に参加できます。</span><span class="sxs-lookup"><span data-stu-id="361f2-106">The parent element can participate in the handling of events that are initially raised by child elements in the element tree.</span></span> <span data-ttu-id="361f2-107">これは、イベント ルーティングにより可能です。</span><span class="sxs-lookup"><span data-stu-id="361f2-107">This is possible because of event routing.</span></span>  
  
 <span data-ttu-id="361f2-108">ルーティング イベントは通常、バブルまたはトンネルの 2 つのルーティング方法のいずれかに従います。</span><span class="sxs-lookup"><span data-stu-id="361f2-108">Routed events typically follow one of two routing strategies, bubbling or tunneling.</span></span> <span data-ttu-id="361f2-109">この例では、バブル イベントに焦点を当て、<xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> イベントを使用して、ルーティングの動作を示します。</span><span class="sxs-lookup"><span data-stu-id="361f2-109">This example focuses on the bubbling event and uses the <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> event to show how routing works.</span></span>  
  
 <span data-ttu-id="361f2-110">次の例では、2 つの <xref:System.Windows.Controls.Button> コントロールを作成し、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 属性構文を使用して、イベント ハンドラーを共通の親要素 (この例では <xref:System.Windows.Controls.StackPanel>) にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="361f2-110">The following example creates two <xref:System.Windows.Controls.Button> controls and uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax to attach an event handler to a common parent element, which in this example is <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="361f2-111">この例では、各 <xref:System.Windows.Controls.Button> 子要素の個々のイベント ハンドラーをアタッチするのではなく、属性構文を使用してイベント ハンドラーを <xref:System.Windows.Controls.StackPanel> 親要素にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="361f2-111">Instead of attaching individual event handlers for each <xref:System.Windows.Controls.Button> child element, the example uses attribute syntax to attach the event handler to the <xref:System.Windows.Controls.StackPanel> parent element.</span></span> <span data-ttu-id="361f2-112">このイベント処理パターンは、ハンドラーがアタッチされる要素の数を減らすための手法としてイベント ルーティングを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="361f2-112">This event-handling pattern shows how to use event routing as a technique for reducing the number of elements where a handler is attached.</span></span> <span data-ttu-id="361f2-113">各 <xref:System.Windows.Controls.Button> のすべてのバブル イベントが親要素を通じてルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="361f2-113">All the bubbling events for each <xref:System.Windows.Controls.Button> route through the parent element.</span></span>  
  
 <span data-ttu-id="361f2-114">親 <xref:System.Windows.Controls.StackPanel> 要素では、属性として指定された <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント名が <xref:System.Windows.Controls.Button> クラスに名前を付けることによって部分的に修飾されていることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="361f2-114">Note that on the parent <xref:System.Windows.Controls.StackPanel> element, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event name specified as the attribute is partially qualified by naming the <xref:System.Windows.Controls.Button> class.</span></span> <span data-ttu-id="361f2-115"><xref:System.Windows.Controls.Button> クラスは、メンバーの一覧に <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントが含まれる <xref:System.Windows.Controls.Primitives.ButtonBase> 派生クラスです。</span><span class="sxs-lookup"><span data-stu-id="361f2-115">The <xref:System.Windows.Controls.Button> class is a <xref:System.Windows.Controls.Primitives.ButtonBase> derived class that has the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in its members listing.</span></span> <span data-ttu-id="361f2-116">イベント ハンドラーをアタッチするためのこの部分修飾手法が必要になるのは、ルーティング イベント ハンドラーがアタッチされる要素のメンバー一覧に、処理されているイベントが存在しない場合です。</span><span class="sxs-lookup"><span data-stu-id="361f2-116">This partial qualification technique for attaching an event handler is necessary if the event that is being handled does not exist in the members listing of the element where the routed event handler is attached.</span></span>  
  
 [!code-xaml[RoutedEventHandle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 <span data-ttu-id="361f2-117">次の例では、<xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="361f2-117">The following example handles the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  <span data-ttu-id="361f2-118">この例では、イベントを処理する要素とイベントを発生させる要素を報告します。</span><span class="sxs-lookup"><span data-stu-id="361f2-118">The example reports which element handles the event and which element raises the event.</span></span> <span data-ttu-id="361f2-119">ユーザーがいずれかのボタンをクリックすると、イベント ハンドラーが実行されます。</span><span class="sxs-lookup"><span data-stu-id="361f2-119">The event handler is executed when the user clicks either button.</span></span>  
  
 [!code-csharp[RoutedEventHandle#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="361f2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="361f2-120">See also</span></span>

- <xref:System.Windows.RoutedEvent>
- [<span data-ttu-id="361f2-121">入力の概要</span><span class="sxs-lookup"><span data-stu-id="361f2-121">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="361f2-122">ルーティング イベントの概要</span><span class="sxs-lookup"><span data-stu-id="361f2-122">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="361f2-123">方法トピック</span><span class="sxs-lookup"><span data-stu-id="361f2-123">How-to Topics</span></span>](events-how-to-topics.md)
- [<span data-ttu-id="361f2-124">XAML 構文の詳細</span><span class="sxs-lookup"><span data-stu-id="361f2-124">XAML Syntax In Detail</span></span>](xaml-syntax-in-detail.md)
