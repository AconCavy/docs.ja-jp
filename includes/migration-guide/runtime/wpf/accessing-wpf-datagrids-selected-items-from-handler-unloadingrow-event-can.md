---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858513"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="bbd38-101">DataGrid の UnloadingRow イベントのハンドラーから WPF DataGrid の選択された項目にアクセスすると、NullReferenceException が発生する可能性がある</span><span class="sxs-lookup"><span data-stu-id="bbd38-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bbd38-102">説明</span><span class="sxs-lookup"><span data-stu-id="bbd38-102">Details</span></span>|<span data-ttu-id="bbd38-103">.NET Framework 4.5 のバグが原因で、行の削除に関連する <xref:System.Windows.Controls.DataGrid> イベントのイベント ハンドラーにより、<xref:System.NullReferenceException?displayProperty=name> の <xref:System.Windows.Controls.DataGrid> または <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> プロパティにアクセスする場合に <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbd38-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="bbd38-104">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="bbd38-104">Suggestion</span></span>|<span data-ttu-id="bbd38-105">この問題は .NET Framework 4.6 で修正されたため、このバージョンの .NET Framework にアップグレードすることによって対処できます。</span><span class="sxs-lookup"><span data-stu-id="bbd38-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="bbd38-106">スコープ</span><span class="sxs-lookup"><span data-stu-id="bbd38-106">Scope</span></span>|<span data-ttu-id="bbd38-107">Minor</span><span class="sxs-lookup"><span data-stu-id="bbd38-107">Minor</span></span>|
|<span data-ttu-id="bbd38-108">バージョン</span><span class="sxs-lookup"><span data-stu-id="bbd38-108">Version</span></span>|<span data-ttu-id="bbd38-109">4.5</span><span class="sxs-lookup"><span data-stu-id="bbd38-109">4.5</span></span>|
|<span data-ttu-id="bbd38-110">[種類]</span><span class="sxs-lookup"><span data-stu-id="bbd38-110">Type</span></span>|<span data-ttu-id="bbd38-111">ランタイム</span><span class="sxs-lookup"><span data-stu-id="bbd38-111">Runtime</span></span>|
|<span data-ttu-id="bbd38-112">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="bbd38-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
