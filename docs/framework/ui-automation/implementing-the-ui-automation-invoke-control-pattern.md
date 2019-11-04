---
title: UI オートメーション Invoke コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
ms.openlocfilehash: 616bbab4d659cf00b1f730492e73ad6b847e3926
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458001"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a><span data-ttu-id="e46d7-102">UI オートメーション Invoke コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="e46d7-102">Implementing the UI Automation Invoke Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="e46d7-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="e46d7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e46d7-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](https://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e46d7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>

<span data-ttu-id="e46d7-105">このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IInvokeProvider>の実装のためのガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="e46d7-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IInvokeProvider>, including information about events and properties.</span></span> <span data-ttu-id="e46d7-106">その他のリファレンスへのリンクは、トピックの最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="e46d7-106">Links to additional references are listed at the end of the topic.</span></span>

<span data-ttu-id="e46d7-107"><xref:System.Windows.Automation.InvokePattern> コントロール パターンは、アクティブになったときに状態を保持せずに単一の明確なアクションを開始または実行するコントロールをサポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e46d7-107">The <xref:System.Windows.Automation.InvokePattern> control pattern is used to support controls that do not maintain state when activated but rather initiate or perform a single, unambiguous action.</span></span> <span data-ttu-id="e46d7-108">チェック ボックスやオプション ボタンなどの状態を保持するコントロールは、代わりに <xref:System.Windows.Automation.Provider.IToggleProvider> と <xref:System.Windows.Automation.Provider.ISelectionItemProvider> をそれぞれ実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-108">Controls that do maintain state, such as check boxes and radio buttons, must instead implement <xref:System.Windows.Automation.Provider.IToggleProvider> and <xref:System.Windows.Automation.Provider.ISelectionItemProvider> respectively.</span></span> <span data-ttu-id="e46d7-109">Invoke コントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e46d7-109">For examples of controls that implement the Invoke control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="e46d7-110">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="e46d7-110">Implementation Guidelines and Conventions</span></span>

<span data-ttu-id="e46d7-111">Invoke コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。</span><span class="sxs-lookup"><span data-stu-id="e46d7-111">When implementing the Invoke control pattern, note the following guidelines and conventions:</span></span>

- <span data-ttu-id="e46d7-112">別のコントロール パターン プロバイダーを通じて同じ動作が公開されていない場合、コントロールは <xref:System.Windows.Automation.Provider.IInvokeProvider> を実装します。</span><span class="sxs-lookup"><span data-stu-id="e46d7-112">Controls implement <xref:System.Windows.Automation.Provider.IInvokeProvider> if the same behavior is not exposed through another control pattern provider.</span></span> <span data-ttu-id="e46d7-113">たとえば、コントロールの <xref:System.Windows.Automation.InvokePattern.Invoke%2A> メソッドが <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> メソッドまたは <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> メソッドと同じ処理を実行する場合、コントロールに <xref:System.Windows.Automation.Provider.IInvokeProvider>を実装しないようにします。</span><span class="sxs-lookup"><span data-stu-id="e46d7-113">For example, if the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method on a control performs the same action as the <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> method, the control should not implement <xref:System.Windows.Automation.Provider.IInvokeProvider>.</span></span>

- <span data-ttu-id="e46d7-114">通常、コントロールの呼び出しは、クリックまたはダブルクリックするか、Enter キー、定義済みのキーボード ショートカット、または何らかの代替的なキーの組み合わせを押すことによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="e46d7-114">Invoking a control is generally performed by clicking or double-clicking or pressing ENTER, a predefined keyboard shortcut, or some alternate combination of keystrokes.</span></span>

- <span data-ttu-id="e46d7-115">(関連付けられたアクションを実行したコントロールへの応答として) アクティブ化されたコントロールで<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e46d7-115"><xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> is raised on a control that has been activated (as a response to a control carrying out its associated action).</span></span> <span data-ttu-id="e46d7-116">可能な場合は、コントロールがアクションを完了し、ブロックせずに戻った後に、イベントを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-116">If possible, the event should be raised after the control has completed the action and returned without blocking.</span></span> <span data-ttu-id="e46d7-117">次のシナリオでは、Invoke 要求を処理する前に Invoked イベントを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-117">The Invoked event should be raised before servicing the Invoke request in the following scenarios:</span></span>

  - <span data-ttu-id="e46d7-118">処理が完了するまで待機することが不可能または非現実的である。</span><span class="sxs-lookup"><span data-stu-id="e46d7-118">It is not possible or practical to wait until the action is complete.</span></span>

  - <span data-ttu-id="e46d7-119">処理にユーザー操作が必要になる。</span><span class="sxs-lookup"><span data-stu-id="e46d7-119">The action requires user interaction.</span></span>

  - <span data-ttu-id="e46d7-120">アクションに時間がかかり、呼び出し側のクライアントを長時間ブロックする。</span><span class="sxs-lookup"><span data-stu-id="e46d7-120">The action is time-consuming and will cause the calling client to block for a significant amount of time.</span></span>

- <span data-ttu-id="e46d7-121">コントロールの呼び出しに大きな副作用が伴う場合は、その副作用を、 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> プロパティを介して公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-121">If invoking the control has significant side-effects, those side-effects should be exposed through the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> property.</span></span> <span data-ttu-id="e46d7-122">たとえば、 <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> が選択に関連付けられていない場合でも、 <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> によって別のコントロールが選択された状態になることがあります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-122">For example, even though <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> is not associated with selection, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> may cause another control to become selected.</span></span>

- <span data-ttu-id="e46d7-123">ホバー (マウス オーバー) 効果は、一般に Invoked イベントを発生させません。</span><span class="sxs-lookup"><span data-stu-id="e46d7-123">Hover (or mouse-over) effects generally do not constitute an Invoked event.</span></span> <span data-ttu-id="e46d7-124">ただし、ホバー状態に基づいて (視覚効果を発生させることなく) アクションを実行するコントロールは、 <xref:System.Windows.Automation.InvokePattern> コントロール パターンをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-124">However, controls that perform an action (as opposed to cause a visual effect) based on the hover state should support the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="e46d7-125">マウス関連の副作用の結果として呼び出す以外にコントロールを呼び出す方法がない場合、そのような実装はユーザー補助に問題があるものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="e46d7-125">This implementation is considered an accessibility issue if the control can be invoked only as a result of a mouse-related side effect.</span></span>

- <span data-ttu-id="e46d7-126">コントロールの呼び出しは、項目の選択とは異なります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-126">Invoking a control is different from selecting an item.</span></span> <span data-ttu-id="e46d7-127">ただし、コントロールによっては、その呼び出しの副作用として、項目が選択された状態になることがあります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-127">However, depending on the control, invoking it may cause the item to become selected as a side-effect.</span></span> <span data-ttu-id="e46d7-128">たとえば、[マイドキュメント] フォルダー内の Microsoft Word 文書リスト項目を呼び出すと、両方とも項目が選択され、ドキュメントが開きます。</span><span class="sxs-lookup"><span data-stu-id="e46d7-128">For example, invoking a Microsoft Word document list item in the My Documents folder both selects the item and opens the document.</span></span>

- <span data-ttu-id="e46d7-129">要素は、呼び出されるとすぐに [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーから消える場合があります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-129">An element can disappear from the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree immediately upon being invoked.</span></span> <span data-ttu-id="e46d7-130">そのため、イベント コールバックで提供された要素に情報を要求すると失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-130">Requesting information from the element provided by the event callback may fail as a result.</span></span> <span data-ttu-id="e46d7-131">推奨される回避策は、キャッシュされた情報をプリフェッチすることです。</span><span class="sxs-lookup"><span data-stu-id="e46d7-131">Pre-fetching cached information is the recommended workaround.</span></span>

- <span data-ttu-id="e46d7-132">コントロールは、複数のコントロール パターンを実装できます。</span><span class="sxs-lookup"><span data-stu-id="e46d7-132">Controls can implement multiple control patterns.</span></span> <span data-ttu-id="e46d7-133">たとえば、Microsoft Excel のツールバーの [塗りつぶしの色] コントロールには、<xref:System.Windows.Automation.InvokePattern> と <xref:System.Windows.Automation.ExpandCollapsePattern> の両方のコントロールパターンが実装されています。</span><span class="sxs-lookup"><span data-stu-id="e46d7-133">For example, the Fill Color control on the Microsoft Excel toolbar implements both the <xref:System.Windows.Automation.InvokePattern> and the <xref:System.Windows.Automation.ExpandCollapsePattern> control patterns.</span></span> <span data-ttu-id="e46d7-134"><xref:System.Windows.Automation.ExpandCollapsePattern> はメニューを公開し、 <xref:System.Windows.Automation.InvokePattern> は選択された色でアクティブな選択内容を塗りつぶします。</span><span class="sxs-lookup"><span data-stu-id="e46d7-134"><xref:System.Windows.Automation.ExpandCollapsePattern> exposes the menu and the <xref:System.Windows.Automation.InvokePattern> fills the active selection with the chosen color.</span></span>

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iinvokeprovider"></a><span data-ttu-id="e46d7-135">IInvokeProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="e46d7-135">Required Members for IInvokeProvider</span></span>

<span data-ttu-id="e46d7-136"><xref:System.Windows.Automation.Provider.IInvokeProvider>の実装には、次のプロパティとメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="e46d7-136">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IInvokeProvider>.</span></span>

|<span data-ttu-id="e46d7-137">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="e46d7-137">Required members</span></span>|<span data-ttu-id="e46d7-138">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="e46d7-138">Member type</span></span>|<span data-ttu-id="e46d7-139">ノート</span><span class="sxs-lookup"><span data-stu-id="e46d7-139">Notes</span></span>|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|<span data-ttu-id="e46d7-140">メソッド</span><span class="sxs-lookup"><span data-stu-id="e46d7-140">method</span></span>|<span data-ttu-id="e46d7-141"><xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> は非同期呼び出しであるため、クライアントをブロックせずに即座に戻る必要があります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-141"><xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> is an asynchronous call and must return immediately without blocking.</span></span><br /><br /> <span data-ttu-id="e46d7-142">呼び出されたときにモーダル ダイアログを直接的または間接的に表示するコントロールでは、この動作は特に重要です。</span><span class="sxs-lookup"><span data-stu-id="e46d7-142">This behavior is particularly critical for controls that, directly or indirectly, launch a modal dialog when invoked.</span></span> <span data-ttu-id="e46d7-143">イベントを発生させたすべての UI オートメーション クライアントは、モーダル ダイアログが閉じられるまで、ブロックされたままになります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-143">Any UI Automation client that instigated the event will remain blocked until the modal dialog is closed.</span></span>|

<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="e46d7-144">例外</span><span class="sxs-lookup"><span data-stu-id="e46d7-144">Exceptions</span></span>

<span data-ttu-id="e46d7-145">プロバイダーは、次の例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e46d7-145">Providers must throw the following exceptions.</span></span>

|<span data-ttu-id="e46d7-146">例外の種類</span><span class="sxs-lookup"><span data-stu-id="e46d7-146">Exception Type</span></span>|<span data-ttu-id="e46d7-147">条件</span><span class="sxs-lookup"><span data-stu-id="e46d7-147">Condition</span></span>|
|--------------------|---------------|
|<xref:System.Windows.Automation.ElementNotEnabledException>|<span data-ttu-id="e46d7-148">コントロールが有効ではない。</span><span class="sxs-lookup"><span data-stu-id="e46d7-148">If the control is not enabled.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e46d7-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="e46d7-149">See also</span></span>

- [<span data-ttu-id="e46d7-150">UI Automation コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="e46d7-150">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="e46d7-151">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="e46d7-151">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="e46d7-152">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="e46d7-152">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="e46d7-153">UI オートメーションを使用したコントロールの呼び出し</span><span class="sxs-lookup"><span data-stu-id="e46d7-153">Invoke a Control Using UI Automation</span></span>](invoke-a-control-using-ui-automation.md)
- [<span data-ttu-id="e46d7-154">UI Automation ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="e46d7-154">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="e46d7-155">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="e46d7-155">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
