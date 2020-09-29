---
title: System.DateTimeOffset メソッド
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: ae588b88ca592ce422202d5231b34060ccc22024
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203476"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="e8426-102">System.DateTimeOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="e8426-102">System.DateTimeOffset Methods</span></span>

<span data-ttu-id="e8426-103">オブジェクト モデルまたは外部マッピング ファイルにマッピングされると、<xref:System.DateTimeOffset?displayProperty=nameWithType> メソッド、演算子、プロパティのほとんどを LINQ to SQL のクエリ内から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8426-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="e8426-104">サポートされていないメソッドは、<xref:System.Object?displayProperty=nameWithType>、`Finalize`、`GetHashCode`、`GetType` など、LINQ to SQL クエリ内のコンテキストで意味を持たない `MemberwiseClone` から継承されたメソッドだけです。</span><span class="sxs-lookup"><span data-stu-id="e8426-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="e8426-105">これらのメソッドは LINQ to SQL で変換して SQL Server で実行することができないため、サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e8426-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8426-106">共通言語ランタイム (CLR) の <xref:System.DateTimeOffset?displayProperty=nameWithType> 構造体、およびそれを LINQ to SQL で SQL の `DATETIMEOFFSET` 列にマッピングする機能を使用するには、.NET Framework 3.5 SP1 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="e8426-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="e8426-107">SQL の `DATETIMEOFFSET` 列は、Microsoft SQL Server 2008 以降でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8426-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="e8426-108">SQLMethods の日付と時刻のメソッド</span><span class="sxs-lookup"><span data-stu-id="e8426-108">SQLMethods Date and Time Methods</span></span>  

 <span data-ttu-id="e8426-109">LINQ to SQL では、<xref:System.DateTimeOffset> 構造体で提供されるメソッドの他に、次の表に示すように、日付と時刻を操作する <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> クラスのメソッドも提供しています。</span><span class="sxs-lookup"><span data-stu-id="e8426-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="e8426-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8426-110">See also</span></span>

- [<span data-ttu-id="e8426-111">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="e8426-111">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="e8426-112">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="e8426-112">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="e8426-113">SQL と CLR の型マッピング</span><span class="sxs-lookup"><span data-stu-id="e8426-113">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
