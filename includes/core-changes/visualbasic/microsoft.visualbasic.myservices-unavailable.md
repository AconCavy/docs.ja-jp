---
ms.openlocfilehash: 58e65bae1593f23945a971b896a1db4a929b4587
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198477"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="7ea3e-101">Microsoft.VisualBasic.MyServices 名前空間の型は使用できません</span><span class="sxs-lookup"><span data-stu-id="7ea3e-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="7ea3e-102"><xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> 名前空間の型は使用できません。</span><span class="sxs-lookup"><span data-stu-id="7ea3e-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7ea3e-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="7ea3e-103">Version introduced</span></span>

<span data-ttu-id="7ea3e-104">.NET Core 3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="7ea3e-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="7ea3e-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="7ea3e-105">Change description</span></span>

<span data-ttu-id="7ea3e-106"><xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> 名前空間の型は、一部の .NET Core 3.0 プレビュー リリースで使用できました。</span><span class="sxs-lookup"><span data-stu-id="7ea3e-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="7ea3e-107">それらは、.NET Core 3.0 Preview 9 以降では使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="7ea3e-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="7ea3e-108">これらの型は、今後のリリースでの不要なアセンブリの依存関係や破壊的変更を回避するために削除されました。</span><span class="sxs-lookup"><span data-stu-id="7ea3e-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7ea3e-109">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="7ea3e-109">Recommended action</span></span>

<span data-ttu-id="7ea3e-110">コードが **Microsoft.VisualBasic.MyServices** 型とそのメンバーの使用に依存している場合は、.NET クラス ライブラリに、対応する型とメンバーがあります。</span><span class="sxs-lookup"><span data-stu-id="7ea3e-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="7ea3e-111">**Microsoft.VisualBasic.MyServices** の型と、それと同等の .NET クラス ライブラリの型との対応を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7ea3e-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="7ea3e-112">Microsoft.VisualBasic.MyServices の型</span><span class="sxs-lookup"><span data-stu-id="7ea3e-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="7ea3e-113">.NET クラス ライブラリの型</span><span class="sxs-lookup"><span data-stu-id="7ea3e-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="7ea3e-114">WPF アプリケーションの場合は <xref:System.Windows.Clipboard?displayProperty=nameWithType>、Windows フォーム アプリケーションの場合は <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7ea3e-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="7ea3e-115"><xref:System.IO> 名前空間の型</span><span class="sxs-lookup"><span data-stu-id="7ea3e-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="7ea3e-116"><xref:Microsoft.Win32> 名前空間のレジストリ関連の型</span><span class="sxs-lookup"><span data-stu-id="7ea3e-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="7ea3e-117">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="7ea3e-117">Category</span></span>

<span data-ttu-id="7ea3e-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ea3e-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7ea3e-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="7ea3e-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

