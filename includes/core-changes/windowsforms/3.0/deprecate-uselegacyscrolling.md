---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643863"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="aa317-101">Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling 互換性スイッチはサポートされていません</span><span class="sxs-lookup"><span data-stu-id="aa317-101">Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="aa317-102">.NET Framework 4.7.1 で導入された `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 互換スイッチは、.NET Core 3.0 上の Windows フォームではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="aa317-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="aa317-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="aa317-103">Change description</span></span>

<span data-ttu-id="aa317-104">.NET Framework 4.7.1 以降では、`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 互換スイッチを使用して、開発者が独立した <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> および <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> アクションをオプトアウトできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="aa317-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="aa317-105">このスイッチによって、コンテキスト テキストが存在する場合は <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> が無視されるという従来の動作が復元されました。開発者は、コントロールに対して <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> アクションの前に <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> アクションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa317-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="aa317-106">詳細については、「[\<AppContextSwitchOverrides> 要素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa317-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="aa317-107">.NET Core では、`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` スイッチはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="aa317-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aa317-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="aa317-108">Version introduced</span></span>

<span data-ttu-id="aa317-109">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="aa317-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aa317-110">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="aa317-110">Recommended action</span></span>

<span data-ttu-id="aa317-111">スイッチを削除します。</span><span class="sxs-lookup"><span data-stu-id="aa317-111">Remove the switch.</span></span> <span data-ttu-id="aa317-112">そのスイッチはサポートされておらず、代替機能はありません。</span><span class="sxs-lookup"><span data-stu-id="aa317-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="aa317-113">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="aa317-113">Category</span></span>

<span data-ttu-id="aa317-114">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="aa317-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aa317-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="aa317-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
