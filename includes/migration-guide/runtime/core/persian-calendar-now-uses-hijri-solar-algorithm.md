---
ms.openlocfilehash: 14581b193fc000c7f805a0602e191cad688c014a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497592"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a><span data-ttu-id="f1044-101">ペルシャ暦でイスラム暦の太陽アルゴリズムが使用されるようになった</span><span class="sxs-lookup"><span data-stu-id="f1044-101">Persian calendar now uses the Hijri solar algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="f1044-102">説明</span><span class="sxs-lookup"><span data-stu-id="f1044-102">Details</span></span>

<span data-ttu-id="f1044-103">.NET Framework 4.6 以降では、<xref:System.Globalization.PersianCalendar?displayProperty=fullName> クラスでイスラム暦の太陽アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f1044-103">Starting with the .NET Framework 4.6, the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> class uses the Hijri solar algorithm.</span></span> <span data-ttu-id="f1044-104"><xref:System.Globalization.PersianCalendar?displayProperty=fullName> と他のカレンダーの間で日付を変換すると、.NET Framework 4.6 以降では、1800 年より前か 2023 年 (グレゴリオ暦) よりも後の日付について、わずかに異なる結果になることがあります。また、<xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> は <code>March 21, 0622</code> ではなく <code>March 22, 0622</code> になります。</span><span class="sxs-lookup"><span data-stu-id="f1044-104">Converting dates between the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> and other calendars may produce a slightly different result beginning with the .NET Framework 4.6 for dates earlier than 1800 or later than 2023 (Gregorian).Also, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> is now <code>March 22, 0622</code> instead of <code>March 21, 0622</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f1044-105">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="f1044-105">Suggestion</span></span>

<span data-ttu-id="f1044-106">.NET Framework 4.6 で PersianCalendar を使用するときには、一部の早い日付または遅い日付に若干の差が生じる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f1044-106">Be aware that some early or late dates may be slightly different when using the PersianCalendar in .NET Framework 4.6.</span></span> <span data-ttu-id="f1044-107">また、異なるバージョンの .NET Framework で実行する可能性のあるプロセス間で日付をシリアル化するときには、PersianCalendar の日付文字列として格納しないでください (これらの値が異なる場合があるため)。</span><span class="sxs-lookup"><span data-stu-id="f1044-107">Also, when serializing dates between processes which may run on different .NET Framework versions, do not store them as PersianCalendar date strings (since those values may be different).</span></span>

| <span data-ttu-id="f1044-108">名前</span><span class="sxs-lookup"><span data-stu-id="f1044-108">Name</span></span>    | <span data-ttu-id="f1044-109">値</span><span class="sxs-lookup"><span data-stu-id="f1044-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f1044-110">スコープ</span><span class="sxs-lookup"><span data-stu-id="f1044-110">Scope</span></span>   |<span data-ttu-id="f1044-111">マイナー</span><span class="sxs-lookup"><span data-stu-id="f1044-111">Minor</span></span>|
|<span data-ttu-id="f1044-112">バージョン</span><span class="sxs-lookup"><span data-stu-id="f1044-112">Version</span></span>|<span data-ttu-id="f1044-113">4.6</span><span class="sxs-lookup"><span data-stu-id="f1044-113">4.6</span></span>|
|<span data-ttu-id="f1044-114">種類</span><span class="sxs-lookup"><span data-stu-id="f1044-114">Type</span></span>|<span data-ttu-id="f1044-115">ランタイム</span><span class="sxs-lookup"><span data-stu-id="f1044-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="f1044-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f1044-116">Affected APIs</span></span>

- <xref:System.Globalization.PersianCalendar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Globalization.PersianCalendar`

-->
