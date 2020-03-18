---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857535"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="6a7b7-101">Unicode 標準バージョン 8.0 のカテゴリのサポート開始</span><span class="sxs-lookup"><span data-stu-id="6a7b7-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6a7b7-102">説明</span><span class="sxs-lookup"><span data-stu-id="6a7b7-102">Details</span></span>|<span data-ttu-id="6a7b7-103">.NET Framework 4.6.2 で、Unicode データが Unicode 標準バージョン 6.3 からバージョン 8.0 にアップグレードされました。</span><span class="sxs-lookup"><span data-stu-id="6a7b7-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="6a7b7-104">.NET Framework 4.6.2 で Unicode 文字カテゴリを要求すると、いくつかの結果が以前の .NET Framework バージョンの結果と一致しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6a7b7-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="6a7b7-105">この変更は、主にチェロキーの音節、新タイ ロ文字の母音記号および声調記号に影響します。</span><span class="sxs-lookup"><span data-stu-id="6a7b7-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="6a7b7-106">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="6a7b7-106">Suggestion</span></span>|<span data-ttu-id="6a7b7-107">コードを確認し、ハードコーディングされた Unicode 文字カテゴリに依存するロジックを削除/変更します。</span><span class="sxs-lookup"><span data-stu-id="6a7b7-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="6a7b7-108">スコープ</span><span class="sxs-lookup"><span data-stu-id="6a7b7-108">Scope</span></span>|<span data-ttu-id="6a7b7-109">Minor</span><span class="sxs-lookup"><span data-stu-id="6a7b7-109">Minor</span></span>|
|<span data-ttu-id="6a7b7-110">バージョン</span><span class="sxs-lookup"><span data-stu-id="6a7b7-110">Version</span></span>|<span data-ttu-id="6a7b7-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="6a7b7-111">4.6.2</span></span>|
|<span data-ttu-id="6a7b7-112">[種類]</span><span class="sxs-lookup"><span data-stu-id="6a7b7-112">Type</span></span>|<span data-ttu-id="6a7b7-113">ランタイム</span><span class="sxs-lookup"><span data-stu-id="6a7b7-113">Runtime</span></span>|
|<span data-ttu-id="6a7b7-114">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="6a7b7-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
