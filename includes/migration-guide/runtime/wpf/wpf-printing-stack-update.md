---
ms.openlocfilehash: 5e2e8d1ec5d698d1c1649c2a0a1b4b77dbdf4022
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621279"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="6de21-101">WPF での印刷スタックの更新</span><span class="sxs-lookup"><span data-stu-id="6de21-101">WPF Printing Stack Update</span></span>

#### <a name="details"></a><span data-ttu-id="6de21-102">説明</span><span class="sxs-lookup"><span data-stu-id="6de21-102">Details</span></span>

<span data-ttu-id="6de21-103"><xref:System.Printing.PrintQueue?displayProperty=fullName> を使う WPF の印刷 API は、非推奨になった XPS 印刷 API ではなく Windows ドキュメント印刷パッケージ API を呼び出すようになりました。</span><span class="sxs-lookup"><span data-stu-id="6de21-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=fullName> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="6de21-104">この変更はサービス性を考慮して行われたもので、ユーザーも開発者も、動作または API の使用の変化を目にすることはありません。</span><span class="sxs-lookup"><span data-stu-id="6de21-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="6de21-105">Windows 10 Creators Update で実行すると、新しい印刷スタックは既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="6de21-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="6de21-106">以前のバージョンの Windows では、以前の印刷スタックが引き続き同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="6de21-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6de21-107">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="6de21-107">Suggestion</span></span>

<span data-ttu-id="6de21-108">Windows 10 Creators Update で以前のスタックを使用するには、<code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> レジストリ キーの <code>UseXpsOMPrinting</code> REG_DWORD 値を <code>1</code> に設定します。</span><span class="sxs-lookup"><span data-stu-id="6de21-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>

| <span data-ttu-id="6de21-109">名前</span><span class="sxs-lookup"><span data-stu-id="6de21-109">Name</span></span>    | <span data-ttu-id="6de21-110">値</span><span class="sxs-lookup"><span data-stu-id="6de21-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6de21-111">スコープ</span><span class="sxs-lookup"><span data-stu-id="6de21-111">Scope</span></span>   |<span data-ttu-id="6de21-112">エッジ</span><span class="sxs-lookup"><span data-stu-id="6de21-112">Edge</span></span>|
|<span data-ttu-id="6de21-113">バージョン</span><span class="sxs-lookup"><span data-stu-id="6de21-113">Version</span></span>|<span data-ttu-id="6de21-114">4.7</span><span class="sxs-lookup"><span data-stu-id="6de21-114">4.7</span></span>|
|<span data-ttu-id="6de21-115">種類</span><span class="sxs-lookup"><span data-stu-id="6de21-115">Type</span></span>|<span data-ttu-id="6de21-116">ランタイム</span><span class="sxs-lookup"><span data-stu-id="6de21-116">Runtime</span></span>|
