---
ms.openlocfilehash: c980b0c0be9f4d6a529baa0743dec9ac16ca0d7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721162"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="e3e40-101">UseLegacyImages 互換性スイッチはサポートされていません</span><span class="sxs-lookup"><span data-stu-id="e3e40-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="e3e40-102">.NET Framework 4.8 で導入された `Switch.System.Windows.Forms.UseLegacyImages` 互換性スイッチは、.NET Core 3.0 上の Windows フォームではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e3e40-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e3e40-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="e3e40-103">Change description</span></span>

<span data-ttu-id="e3e40-104">.NET Framework 4.8 以降、`Switch.System.Windows.Forms.UseLegacyImages` 互換性スイッチでは、高 DPI 環境での ClickOnce シナリオで考えられるイメージ スケーリングの問題に対処しています。</span><span class="sxs-lookup"><span data-stu-id="e3e40-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="e3e40-105">`true` に設定してこのスイッチを使用すると、スケールが 100% より大きく設定されている高 DPI ディスプレイで、レガシ イメージのスケーリングを復元できます。</span><span class="sxs-lookup"><span data-stu-id="e3e40-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="e3e40-106">詳細については、GitHub 上の [.NET Framework 4.8 のリリース ノート](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3e40-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="e3e40-107">.NET Core では、`Switch.System.Windows.Forms.UseLegacyImages` スイッチはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e3e40-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e3e40-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="e3e40-108">Version introduced</span></span>

<span data-ttu-id="e3e40-109">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="e3e40-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e3e40-110">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="e3e40-110">Recommended action</span></span>

<span data-ttu-id="e3e40-111">スイッチを削除します。</span><span class="sxs-lookup"><span data-stu-id="e3e40-111">Remove the switch.</span></span> <span data-ttu-id="e3e40-112">そのスイッチはサポートされておらず、代替機能はありません。</span><span class="sxs-lookup"><span data-stu-id="e3e40-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="e3e40-113">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="e3e40-113">Category</span></span>

<span data-ttu-id="e3e40-114">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="e3e40-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e3e40-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="e3e40-115">Affected APIs</span></span>

- <span data-ttu-id="e3e40-116">なし</span><span class="sxs-lookup"><span data-stu-id="e3e40-116">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
