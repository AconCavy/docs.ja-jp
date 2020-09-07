---
ms.openlocfilehash: bca76daca6e9c424377a80aa56e1a5ff191be5ca
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497454"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="130fd-101">カスタム DataTemplate を使用しているとき、断続的に、ItemsControl (ListBox や DataGrid など) 内の最後の項目までスクロールできない</span><span class="sxs-lookup"><span data-stu-id="130fd-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

#### <a name="details"></a><span data-ttu-id="130fd-102">説明</span><span class="sxs-lookup"><span data-stu-id="130fd-102">Details</span></span>

<span data-ttu-id="130fd-103">場合によっては、.NET Framework 4.5 のバグにより、カスタム DataTemplate を使用していると、ItemsControl (<xref:System.Windows.Controls.ListBox?displayProperty=fullName>、<xref:System.Windows.Controls.ComboBox?displayProperty=fullName>、<xref:System.Windows.Controls.DataGrid?displayProperty=fullName> など) の最後の項目までスクロールできません。</span><span class="sxs-lookup"><span data-stu-id="130fd-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="130fd-104">(上へスクロールした後で) もう一度スクロールを試みると、今度はスクロールできます。</span><span class="sxs-lookup"><span data-stu-id="130fd-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="130fd-105">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="130fd-105">Suggestion</span></span>

<span data-ttu-id="130fd-106">この問題は .NET Framework 4.5.2 で修正されたため、このバージョン (またはそれ以降のバージョン) の .NET Framework にアップグレードすることによって対処できます。</span><span class="sxs-lookup"><span data-stu-id="130fd-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="130fd-107">または、ユーザーは、スクロール バーをこれらのコレクションの最後の項目までドラッグできますが、2 回試みなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="130fd-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>

| <span data-ttu-id="130fd-108">名前</span><span class="sxs-lookup"><span data-stu-id="130fd-108">Name</span></span>    | <span data-ttu-id="130fd-109">[値]</span><span class="sxs-lookup"><span data-stu-id="130fd-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="130fd-110">スコープ</span><span class="sxs-lookup"><span data-stu-id="130fd-110">Scope</span></span>   |<span data-ttu-id="130fd-111">マイナー</span><span class="sxs-lookup"><span data-stu-id="130fd-111">Minor</span></span>|
|<span data-ttu-id="130fd-112">バージョン</span><span class="sxs-lookup"><span data-stu-id="130fd-112">Version</span></span>|<span data-ttu-id="130fd-113">4.5</span><span class="sxs-lookup"><span data-stu-id="130fd-113">4.5</span></span>|
|<span data-ttu-id="130fd-114">種類</span><span class="sxs-lookup"><span data-stu-id="130fd-114">Type</span></span>|<span data-ttu-id="130fd-115">ランタイム</span><span class="sxs-lookup"><span data-stu-id="130fd-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="130fd-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="130fd-116">Affected APIs</span></span>

<span data-ttu-id="130fd-117">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="130fd-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
