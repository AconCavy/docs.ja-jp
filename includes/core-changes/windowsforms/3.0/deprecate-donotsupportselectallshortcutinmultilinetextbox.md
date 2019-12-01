---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643881"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="01e5e-101">Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox 互換性スイッチはサポートされていません</span><span class="sxs-lookup"><span data-stu-id="01e5e-101">Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="01e5e-102">.NET Framework 4.6.1 で導入された `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 互換スイッチは、.NET Core 3.0 上の Windows フォームではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="01e5e-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="01e5e-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="01e5e-103">Change description</span></span>

<span data-ttu-id="01e5e-104">.NET Framework 4.6.1 以降、<xref:System.Windows.Forms.TextBox> コントロールで <kbd>Ctrl</kbd> + <kbd>A</kbd> ショートカット キーを押すと、すべてのテキストが選択されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="01e5e-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="01e5e-105">.NET Framework 4.6 およびそれ以前のバージョンでは、[Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) および <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> プロパティが `true` に選択されていた場合、<kbd>Ctrl</kbd> + <kbd>A</kbd> ショートカット キーを選択してもすべてのテキストが選択されませんでした。</span><span class="sxs-lookup"><span data-stu-id="01e5e-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="01e5e-106">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 互換性スイッチは、元の動作を保持するために .NET Framework 4.6.1 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="01e5e-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="01e5e-107">詳細については、「<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01e5e-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="01e5e-108">.NET Core では、`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` スイッチはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="01e5e-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="01e5e-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="01e5e-109">Version introduced</span></span>

<span data-ttu-id="01e5e-110">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="01e5e-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01e5e-111">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="01e5e-111">Recommended action</span></span>

<span data-ttu-id="01e5e-112">スイッチを削除します。</span><span class="sxs-lookup"><span data-stu-id="01e5e-112">Remove the switch.</span></span> <span data-ttu-id="01e5e-113">そのスイッチはサポートされておらず、代替機能はありません。</span><span class="sxs-lookup"><span data-stu-id="01e5e-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="01e5e-114">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="01e5e-114">Category</span></span>

<span data-ttu-id="01e5e-115">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="01e5e-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01e5e-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="01e5e-116">Affected APIs</span></span>

- <span data-ttu-id="01e5e-117">なし</span><span class="sxs-lookup"><span data-stu-id="01e5e-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
