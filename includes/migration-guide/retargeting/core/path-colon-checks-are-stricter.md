---
ms.openlocfilehash: a51738fa75ba2dd4574549fce2570df8231c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859255"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="629b3-101">パスのコロン チェックがより厳密になった</span><span class="sxs-lookup"><span data-stu-id="629b3-101">Path colon checks are stricter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="629b3-102">説明</span><span class="sxs-lookup"><span data-stu-id="629b3-102">Details</span></span>|<span data-ttu-id="629b3-103">.NET Framework 4.6.2 では、以前はサポートされていなかったパスをサポートするために (長さと形式の両方で) 数多くの変更が加えられました。</span><span class="sxs-lookup"><span data-stu-id="629b3-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="629b3-104">適切なドライブ区切り (コロン) 構文の確認がより正確に行われました。その結果、それ以前は許容されていた、ごく少数のパス API の一部の URI パスがブロックされました。</span><span class="sxs-lookup"><span data-stu-id="629b3-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they used to be tolerated.</span></span>|
|<span data-ttu-id="629b3-105">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="629b3-105">Suggestion</span></span>|<span data-ttu-id="629b3-106">影響を受ける API に URI を渡す場合、まず、文字列を正規のパスに変更します。</span><span class="sxs-lookup"><span data-stu-id="629b3-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span><ul><li><span data-ttu-id="629b3-107">URL から手動でスキームを削除します (たとえば、URL から <code>file://</code> を削除します)。</span><span class="sxs-lookup"><span data-stu-id="629b3-107">Remove the scheme from URLs manually (e.g. remove <code>file://</code> from URLs)</span></span></li><li><span data-ttu-id="629b3-108"><xref:System.Uri> クラスに URI を渡し、<xref:System.Uri.LocalPath> を使用します。</span><span class="sxs-lookup"><span data-stu-id="629b3-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath></span></span></li></ul><span data-ttu-id="629b3-109">あるいは、<code>Switch.System.IO.UseLegacyPathHandling</code> AppContext スイッチを true に設定し、新しいパス正規化を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="629b3-109">Alternatively, you can opt out of the new path normalization by setting the <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext switch to true.</span></span>|
|<span data-ttu-id="629b3-110">スコープ</span><span class="sxs-lookup"><span data-stu-id="629b3-110">Scope</span></span>|<span data-ttu-id="629b3-111">エッジ</span><span class="sxs-lookup"><span data-stu-id="629b3-111">Edge</span></span>|
|<span data-ttu-id="629b3-112">バージョン</span><span class="sxs-lookup"><span data-stu-id="629b3-112">Version</span></span>|<span data-ttu-id="629b3-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="629b3-113">4.6.2</span></span>|
|<span data-ttu-id="629b3-114">[種類]</span><span class="sxs-lookup"><span data-stu-id="629b3-114">Type</span></span>|<span data-ttu-id="629b3-115">再ターゲット中</span><span class="sxs-lookup"><span data-stu-id="629b3-115">Retargeting</span></span>|
|<span data-ttu-id="629b3-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="629b3-116">Affected APIs</span></span>|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|
