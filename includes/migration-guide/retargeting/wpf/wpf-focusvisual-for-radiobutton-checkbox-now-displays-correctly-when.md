---
ms.openlocfilehash: 9e70bcd95393a7ff24de43577d26869ce674067b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614962"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a><span data-ttu-id="df19f-101">WPF で、コントロールに内容がないとき、RadioButton と CheckBox のフォーカス ビジュアルが正しく表示されるようになった</span><span class="sxs-lookup"><span data-stu-id="df19f-101">WPF FocusVisual for RadioButton and CheckBox Now Displays Correctly When The Controls Have No Content</span></span>

#### <a name="details"></a><span data-ttu-id="df19f-102">説明</span><span class="sxs-lookup"><span data-stu-id="df19f-102">Details</span></span>

<span data-ttu-id="df19f-103">.NET Framework 4.7.1 およびそれより前のバージョンでは、WPF の <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> と <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> のフォーカス ビジュアルに整合性がなく、クラシック テーマとハイ コントラスト テーマでは正しくありません。</span><span class="sxs-lookup"><span data-stu-id="df19f-103">In the .NET Framework 4.7.1 and earlier versions, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="df19f-104">これらの問題は、コントロールに内容が何も設定されていない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="df19f-104">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="df19f-105">これにより、テーマ間の遷移が混乱し、フォーカス ビジュアルが見にくくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="df19f-105">This can make the transition between themes confusing and the focus visual hard to see.</span></span> <span data-ttu-id="df19f-106">.NET Framework 4.7.2 では、これらのビジュアルのテーマ間の整合性が向上し、クラシック モードとハイ コントラスト テーマでの視認性がよくなっています。</span><span class="sxs-lookup"><span data-stu-id="df19f-106">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="df19f-107">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="df19f-107">Suggestion</span></span>

<span data-ttu-id="df19f-108">.NET Framework 4.7.2 を対象にしている開発者が、.NET 4.7.1 での動作に戻したい場合は、以下の AppContext フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df19f-108">A developer targeting .NET Framework 4.7.2 that wants to revert to the behavior in .NET 4.7.1 will need to set the following AppContext flag.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="df19f-109">.NET 4.7.2 より前のバージョンの Framework を対象にしながらこの変更を利用したい開発者は、次の AppContext フラグを設定する必要があります。すべてのフラグを適切に設定する必要があり、.NET Framework 4.7.2 以降のバージョンがインストールされている必要があることに注意してください。WPF アプリケーションで最新の機能強化を利用するには、以前のすべてのアクセシビリティ機能強化を利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df19f-109">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 must set the following AppContext flags.Note that all the flags must be set appropriately and the installed version of the .NET Framework must be 4.7.2 or greater.WPF applications are required to opt in to all earlier accessibility improvements to get the latest improvements.</span></span> <span data-ttu-id="df19f-110">これを行うには、AppContext スイッチ "Switch.UseLegacyAccessibilityFeatures" と "Switch.UseLegacyAccessibilityFeatures.2" の両方を false に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df19f-110">To do this, ensure that both the AppContext switches 'Switch.UseLegacyAccessibilityFeatures' and 'Switch.UseLegacyAccessibilityFeatures.2' are set to false.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="df19f-111">名前</span><span class="sxs-lookup"><span data-stu-id="df19f-111">Name</span></span>    | <span data-ttu-id="df19f-112">[値]</span><span class="sxs-lookup"><span data-stu-id="df19f-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="df19f-113">スコープ</span><span class="sxs-lookup"><span data-stu-id="df19f-113">Scope</span></span>   | <span data-ttu-id="df19f-114">エッジ</span><span class="sxs-lookup"><span data-stu-id="df19f-114">Edge</span></span>        |
| <span data-ttu-id="df19f-115">バージョン</span><span class="sxs-lookup"><span data-stu-id="df19f-115">Version</span></span> | <span data-ttu-id="df19f-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="df19f-116">4.7.2</span></span>       |
| <span data-ttu-id="df19f-117">種類</span><span class="sxs-lookup"><span data-stu-id="df19f-117">Type</span></span>    | <span data-ttu-id="df19f-118">再ターゲット中</span><span class="sxs-lookup"><span data-stu-id="df19f-118">Retargeting</span></span> |
