---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621255"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="fdeae-101">StaysOpen=False でポップアップがチェーンされる</span><span class="sxs-lookup"><span data-stu-id="fdeae-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="fdeae-102">説明</span><span class="sxs-lookup"><span data-stu-id="fdeae-102">Details</span></span>

<span data-ttu-id="fdeae-103">ポップアップの外側をクリックすると、StaysOpen=False のポップアップが閉じられることが想定されます。</span><span class="sxs-lookup"><span data-stu-id="fdeae-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="fdeae-104">このような 2 つ以上のポップアップがチェーンされている (つまり、1 つに別のものが含まれている) 場合、次のような、多くの問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="fdeae-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="fdeae-105">2 つのレベルを開き、P2 の外側と、P1 の内側をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fdeae-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="fdeae-106">何も起こりません。</span><span class="sxs-lookup"><span data-stu-id="fdeae-106">Nothing happens.</span></span></li><li><span data-ttu-id="fdeae-107">2 つのレベルを開き、P1 の外側をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fdeae-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="fdeae-108">両方のポップアップが閉じます。</span><span class="sxs-lookup"><span data-stu-id="fdeae-108">Both popups close.</span></span></li><li><span data-ttu-id="fdeae-109">2 つのレベルを開いて閉じます。</span><span class="sxs-lookup"><span data-stu-id="fdeae-109">Open and close two levels.</span></span>  <span data-ttu-id="fdeae-110">次に、P2 をもう一度開いてみます。</span><span class="sxs-lookup"><span data-stu-id="fdeae-110">Then try to open P2 again.</span></span>  <span data-ttu-id="fdeae-111">何も起こりません。</span><span class="sxs-lookup"><span data-stu-id="fdeae-111">Nothing happens.</span></span></li><li><span data-ttu-id="fdeae-112">3 つのレベルを開いてみます。</span><span class="sxs-lookup"><span data-stu-id="fdeae-112">Try to open three levels.</span></span>  <span data-ttu-id="fdeae-113">この操作を行うことはできません</span><span class="sxs-lookup"><span data-stu-id="fdeae-113">You can't.</span></span>  <span data-ttu-id="fdeae-114">(クリックする場所に応じて、何も起こらないか、最初の 2 つのレベルが閉じます)。このような場合 (および他のバリアント) は、予期したとおり動作します。</span><span class="sxs-lookup"><span data-stu-id="fdeae-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="fdeae-115">名前</span><span class="sxs-lookup"><span data-stu-id="fdeae-115">Name</span></span>    | <span data-ttu-id="fdeae-116">値</span><span class="sxs-lookup"><span data-stu-id="fdeae-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fdeae-117">スコープ</span><span class="sxs-lookup"><span data-stu-id="fdeae-117">Scope</span></span>   |<span data-ttu-id="fdeae-118">エッジ</span><span class="sxs-lookup"><span data-stu-id="fdeae-118">Edge</span></span>|
|<span data-ttu-id="fdeae-119">バージョン</span><span class="sxs-lookup"><span data-stu-id="fdeae-119">Version</span></span>|<span data-ttu-id="fdeae-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="fdeae-120">4.7.1</span></span>|
|<span data-ttu-id="fdeae-121">種類</span><span class="sxs-lookup"><span data-stu-id="fdeae-121">Type</span></span>|<span data-ttu-id="fdeae-122">ランタイム</span><span class="sxs-lookup"><span data-stu-id="fdeae-122">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fdeae-123">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="fdeae-123">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
