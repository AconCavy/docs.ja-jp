---
title: UI オートメーション プロバイダーでのコントロール パターンのサポート
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: 1200ebd42884220d2611729b87f4bf51e7a903a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446821"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="0e581-102">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="0e581-102">Support Control Patterns in a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="0e581-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="0e581-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0e581-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](/windows/win32/winauto/entry-uiauto-win32)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e581-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="0e581-105">このトピックでは、クライアント アプリケーションがコントロールを操作して、それらからデータを取得できるように、UI オートメーション プロバイダーに 1 つ以上のコントロール パターンを実装する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="0e581-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>

## <a name="support-control-patterns"></a><span data-ttu-id="0e581-106">コントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="0e581-106">Support Control Patterns</span></span>

1. <span data-ttu-id="0e581-107"><xref:System.Windows.Automation.Provider.IInvokeProvider> の <xref:System.Windows.Automation.InvokePattern>など、要素がサポートする必要のあるコントロール パターンの適切なインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="0e581-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>

2. <span data-ttu-id="0e581-108"><xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0e581-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>

## <a name="example"></a><span data-ttu-id="0e581-109">例</span><span class="sxs-lookup"><span data-stu-id="0e581-109">Example</span></span>

<span data-ttu-id="0e581-110">単一選択のカスタム リスト ボックスの <xref:System.Windows.Automation.Provider.ISelectionProvider> の実装例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0e581-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="0e581-111">3 つのプロパティを返し、現在選択されている項目を取得します。</span><span class="sxs-lookup"><span data-stu-id="0e581-111">It returns three properties and gets the currently selected item.</span></span>

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a><span data-ttu-id="0e581-112">例</span><span class="sxs-lookup"><span data-stu-id="0e581-112">Example</span></span>

<span data-ttu-id="0e581-113"><xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> を実装するクラスを返す <xref:System.Windows.Automation.Provider.ISelectionProvider>の実装例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0e581-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="0e581-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span><span class="sxs-lookup"><span data-stu-id="0e581-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in Microsoft Visual Basic .NET) is returned for all other pattern identifiers.</span></span>

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a><span data-ttu-id="0e581-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e581-115">See also</span></span>

- [<span data-ttu-id="0e581-116">UI オートメーション プロバイダーの概要</span><span class="sxs-lookup"><span data-stu-id="0e581-116">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="0e581-117">サーバー側 UI オートメーション プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="0e581-117">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
