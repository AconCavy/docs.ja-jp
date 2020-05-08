---
title: System.String メソッド
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 583c0d58562c1605f24b61489d481e19248ebed4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792496"
---
# <a name="systemstring-methods"></a><span data-ttu-id="5dab7-102">System.String メソッド</span><span class="sxs-lookup"><span data-stu-id="5dab7-102">System.String Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="5dab7-103">は、次の <xref:System.String> メソッドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5dab7-103">does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="5dab7-104">サポートされていない一般的な System.String メソッド</span><span class="sxs-lookup"><span data-stu-id="5dab7-104">Unsupported System.String Methods in General</span></span>  
 <span data-ttu-id="5dab7-105">サポートされていない一般的な <xref:System.String> メソッドは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5dab7-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
- <span data-ttu-id="5dab7-106">カルチャを認識するオーバーロード (`CultureInfo`、`StringComparison`、`IFormatProvider` を受け取るメソッド)</span><span class="sxs-lookup"><span data-stu-id="5dab7-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
- <span data-ttu-id="5dab7-107">`char` 配列を受け取るまたは生成するメソッド</span><span class="sxs-lookup"><span data-stu-id="5dab7-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="5dab7-108">サポートされていない System.String 静的メソッド</span><span class="sxs-lookup"><span data-stu-id="5dab7-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="5dab7-109">サポートされていない System.String 静的メソッド</span><span class="sxs-lookup"><span data-stu-id="5dab7-109">Unsupported System.String Static Methods</span></span>|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="5dab7-110">サポートされていない System.String 非静的メソッド</span><span class="sxs-lookup"><span data-stu-id="5dab7-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="5dab7-111">サポートされていない System.String 非静的メソッド</span><span class="sxs-lookup"><span data-stu-id="5dab7-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="5dab7-112">.NET との相違</span><span class="sxs-lookup"><span data-stu-id="5dab7-112">Differences from .NET</span></span>  
  
- <span data-ttu-id="5dab7-113">SQL Server で有効にされている照合順序があっても、クエリには適用されません。したがって、既定では、カルチャ依存で大文字と小文字を区別しない比較が行われます。</span><span class="sxs-lookup"><span data-stu-id="5dab7-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="5dab7-114">この動作は、大文字と小文字を区別する .NET Framework の既定の動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="5dab7-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
- <span data-ttu-id="5dab7-115">`LastIndexOf` から 0 が返された場合は、文字列が `NULL` であるか、または見つかった位置が 0 であることを示します。</span><span class="sxs-lookup"><span data-stu-id="5dab7-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
- <span data-ttu-id="5dab7-116">固定長文字列 (`CHAR`、`NCHAR`) では、データベースにおいて自動的に埋め込みが適用されるため、連結やその他の操作で予期しない結果が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="5dab7-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
- <span data-ttu-id="5dab7-117">`Replace` 列、`ToLower` 列、および XML では、`ToUpper`、`TEXT`、`NTEXT` などの多くのメソッドや文字インデクサーで有効な変換が用意されていないため、通常の変換を行おうとすると `SqlExceptions` が発生します。</span><span class="sxs-lookup"><span data-stu-id="5dab7-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="5dab7-118">これらの型については、これが適切な動作と見なされます。</span><span class="sxs-lookup"><span data-stu-id="5dab7-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="5dab7-119">ただし、`VARCHAR`、`NVARCHAR`、`VARCHAR(max)`、および `NVARCHAR(max)` については、すべての文字列操作が共通言語ランタイム (CLR: Common Language Runtime) のセマンティクと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5dab7-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dab7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5dab7-120">See also</span></span>

- [<span data-ttu-id="5dab7-121">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="5dab7-121">Data Types and Functions</span></span>](data-types-and-functions.md)
