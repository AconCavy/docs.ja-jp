---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937005"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="be566-101">Windows フォームからの重複する API の削除</span><span class="sxs-lookup"><span data-stu-id="be566-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="be566-102">.NET Core 3.0 Preview 4 以降、<xref:System.Windows.Forms?displayProperty=fullName> 名前空間で誤って重複していた多数の API が .NET Core 3.0 RC1 で削除されました。</span><span class="sxs-lookup"><span data-stu-id="be566-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="be566-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="be566-103">Change description</span></span>

<span data-ttu-id="be566-104">.NET Core 3.0 Preview 4 には、<xref:System.ComponentModel.Design?displayProperty=fullName> 名前空間に既にある <xref:System.Windows.Forms?displayProperty=fullName> 名前空間の複数の型が、誤って重複しています。</span><span class="sxs-lookup"><span data-stu-id="be566-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="be566-105">.NET Core 3.0 RC1 以降、重複するこれらの型はなくなります。</span><span class="sxs-lookup"><span data-stu-id="be566-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="be566-106">次の表に、元の型とその重複する型の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="be566-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="be566-107">元の型</span><span class="sxs-lookup"><span data-stu-id="be566-107">Original type</span></span>|<span data-ttu-id="be566-108">重複する型</span><span class="sxs-lookup"><span data-stu-id="be566-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="be566-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="be566-109">Version introduced</span></span>

<span data-ttu-id="be566-110">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="be566-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="be566-111">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="be566-111">Recommended action</span></span>

<span data-ttu-id="be566-112">元の型を参照するように、表の「**元の型**」列のとおりコードを更新してください。</span><span class="sxs-lookup"><span data-stu-id="be566-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="be566-113">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="be566-113">Category</span></span>

<span data-ttu-id="be566-114">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="be566-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="be566-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="be566-115">Affected APIs</span></span>

- <span data-ttu-id="be566-116">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="be566-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
