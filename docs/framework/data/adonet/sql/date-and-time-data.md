---
title: 日付と時刻のデータ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: d7a016b8911cee3091dec24bc26d1f1965f54749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148765"
---
# <a name="date-and-time-data"></a><span data-ttu-id="c17ce-102">日付と時刻のデータ</span><span class="sxs-lookup"><span data-stu-id="c17ce-102">Date and Time Data</span></span>
<span data-ttu-id="c17ce-103">SQL Server 2008 では、日付と時刻の情報を扱うための新しいデータ型が導入されました。</span><span class="sxs-lookup"><span data-stu-id="c17ce-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="c17ce-104">新しいデータ型には、日付と時刻の別個のデータ型と、範囲、有効桁数、タイム ゾーン処理が向上した拡張データ型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c17ce-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="c17ce-105">.NET Framework 3.5 Service Pack (SP) 1 以降では、.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) が SQL Server 2008 データベース エンジンの新機能すべてをサポートします。</span><span class="sxs-lookup"><span data-stu-id="c17ce-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="c17ce-106">SqlClient でこれらの新機能を使用するには、.NET Framework 3.5 SP1 以降をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c17ce-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="c17ce-107">SQL Server 2008 より前のバージョンの SQL Server では、日付と時刻に使用できるデータ型には `datetime` と `smalldatetime` の 2 つしかありませんでした。</span><span class="sxs-lookup"><span data-stu-id="c17ce-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="c17ce-108">どちらのデータ型も日付値と時刻値の両方を保持するため、日付と時刻のどちらか一方の値のみを使用するのが困難でした。</span><span class="sxs-lookup"><span data-stu-id="c17ce-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="c17ce-109">さらに、これらのデータ型では、1753 年に英国でグレゴリオ暦が導入された後の日付のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="c17ce-110">もう 1 つの制限事項は、これらの古いデータ型がタイムゾーンに対応していないことです。これにより、複数のタイムゾーンからのデータの操作が困難になります。</span><span class="sxs-lookup"><span data-stu-id="c17ce-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="c17ce-111">SQL Server のデータ型に関する完全な説明は、SQL Server オンライン ブックに記載されています。</span><span class="sxs-lookup"><span data-stu-id="c17ce-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="c17ce-112">次の表は、バージョン別の日付と時刻のデータに関する初歩的なトピックの一覧です。</span><span class="sxs-lookup"><span data-stu-id="c17ce-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="c17ce-113">**SQL Server のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="c17ce-113">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="c17ce-114">[日時データの使用](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="c17ce-114">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="c17ce-115">SQL Server 2008 で導入された日付/時刻データ型</span><span class="sxs-lookup"><span data-stu-id="c17ce-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="c17ce-116">次の表は、新しい日付と時刻のデータ型の説明です。</span><span class="sxs-lookup"><span data-stu-id="c17ce-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="c17ce-117">SQL Server のデータ型</span><span class="sxs-lookup"><span data-stu-id="c17ce-117">SQL Server data type</span></span>|<span data-ttu-id="c17ce-118">説明</span><span class="sxs-lookup"><span data-stu-id="c17ce-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="c17ce-119">データ型 `date` の範囲は 01 年 1 月 1 日から 9999 年 12 月 31 日までで、精度は 1 日です。</span><span class="sxs-lookup"><span data-stu-id="c17ce-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="c17ce-120">既定値は 1900 年 1 月 1 日です。</span><span class="sxs-lookup"><span data-stu-id="c17ce-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="c17ce-121">記憶領域のサイズは 3 バイトです。</span><span class="sxs-lookup"><span data-stu-id="c17ce-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="c17ce-122">`time` データ型は、24 時間形式で時刻値のみを格納します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="c17ce-123">`time` データ型は、00:00:00.0000000 から 23:59:59.9999999 の範囲で、100 ナノ秒の精度です。</span><span class="sxs-lookup"><span data-stu-id="c17ce-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="c17ce-124">既定値は 00:00: 00.0000000 (午前 0 時) です。</span><span class="sxs-lookup"><span data-stu-id="c17ce-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="c17ce-125">`time` データ型はユーザー定義による 1 秒未満の時間の有効桁数をサポートし、記憶領域のサイズは、指定された有効桁数に応じて 3 バイト～ 6 バイトになります。</span><span class="sxs-lookup"><span data-stu-id="c17ce-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="c17ce-126">`datetime2` データ型では、`date` データ型と `time` データ型の範囲と精度が 1 つのデータ型に結合されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="c17ce-127">既定値と文字列リテラルの形式は、`date` データ型および `time` データ型で定義されているものと同じです。</span><span class="sxs-lookup"><span data-stu-id="c17ce-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="c17ce-128">`datetimeoffset` データ型は、`datetime2` のすべての機能に加えて、タイム ゾーン オフセットを持ちます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="c17ce-129">タイム ゾーン オフセットは、[+&#124;-] HH:MM として表されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="c17ce-130">HH は、タイム ゾーン オフセットの時間数を表す 00 ～ 14 の 2 桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="c17ce-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="c17ce-131">MM は、タイム ゾーン オフセットの付加的な分数を表す 0 ～ 59 の 2 桁の数字です。</span><span class="sxs-lookup"><span data-stu-id="c17ce-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="c17ce-132">時刻の精度は 100 ナノ秒までサポートされます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="c17ce-133">必須の + または - 記号は、ローカル時刻を取得するために、UTC (協定世界時またはグリニッジ標準時) からタイム ゾーン オフセットを加算するか減算するかを示します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c17ce-134">`Type System Version` キーワードの使用方法の詳細については、「<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c17ce-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="c17ce-135">日付書式と表記順序</span><span class="sxs-lookup"><span data-stu-id="c17ce-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="c17ce-136">SQL Server が日付と時刻の値をどのように処理するかは、型システムのバージョンとサーバーのバージョンだけでなく、サーバーの既定の言語と書式設定にも左右されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="c17ce-137">ある言語の日付形式に対して機能する日付文字列は、別の言語および日付形式の設定を使用する接続によってクエリが実行された場合に認識されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c17ce-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="c17ce-138">Transact-SQL SET LANGUAGE ステートメントでは、日付部分の順序を決定する DATEFORMAT を暗黙的に設定します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="c17ce-139">接続に対して SET DATEFORMAT Transact-SQL ステートメントを使用して、MDY、DMY、YMD、YDM、MYD、DYM の順序で日付部分を並べ替えることにより、日付値を明確にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="c17ce-140">接続に対して DATEFORMAT を指定しない場合、SQL Server では接続に関連付けられている既定の言語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="c17ce-141">たとえば、' 01/02/03' の日付文字列は、米国英語の言語設定のサーバーでは MDY (2003 年 1 月 2 日) として解釈され、英国英語の言語設定のサーバーでは DMY (2003 年 2 月 1 日) として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="c17ce-142">年は、SQL Server の終了年の規則に従って決定されます。この規則では、世紀の値を割り当てるための終了日が定義されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="c17ce-143">詳しくは、「[two digit year cutoff オプション](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c17ce-143">For more information, see [two digit year cutoff Option](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c17ce-144">YDM 日付書式は、文字列形式から `date`、`time`、`datetime2`、または `datetimeoffset` に変換する場合にはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="c17ce-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="c17ce-145">SQL Server による日付と時刻のデータの解釈方法について詳しくは、「[日時データの使用](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c17ce-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="c17ce-146">Date/Time データ型とパラメーター</span><span class="sxs-lookup"><span data-stu-id="c17ce-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="c17ce-147">新しい日付型と時刻型をサポートするために、<xref:System.Data.SqlDbType> には、次の列挙値が追加されています。</span><span class="sxs-lookup"><span data-stu-id="c17ce-147">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

<span data-ttu-id="c17ce-148"><xref:System.Data.SqlClient.SqlParameter> のデータ型は、前の <xref:System.Data.SqlDbType> 列挙型のいずれかの値を使って指定できます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-148">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the preceding <xref:System.Data.SqlDbType> enumerations.</span></span>

> [!NOTE]
> <span data-ttu-id="c17ce-149">`SqlParameter` の `DbType` プロパティは `SqlDbType.Date` に設定できません。</span><span class="sxs-lookup"><span data-stu-id="c17ce-149">You cannot set the `DbType` property of a `SqlParameter` to `SqlDbType.Date`.</span></span>

 <span data-ttu-id="c17ce-150"><xref:System.Data.SqlClient.SqlParameter> オブジェクトの <xref:System.Data.SqlClient.SqlParameter.DbType%2A> プロパティを特定の `SqlParameter` 列挙値に設定することによって、<xref:System.Data.DbType> の型をジェネリックに指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-150">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="c17ce-151"><xref:System.Data.DbType> データ型と `datetime2` データ型をサポートするために、`datetimeoffset` には、次の列挙値が追加されています。</span><span class="sxs-lookup"><span data-stu-id="c17ce-151">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
- <span data-ttu-id="c17ce-152">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="c17ce-152">DbType.DateTime2</span></span>  
  
- <span data-ttu-id="c17ce-153">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c17ce-153">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="c17ce-154">これらの新しい列挙値は、以前のバージョンの .NET Framework に存在した `Date`、`Time`、および `DateTime` の各列挙値を補います。</span><span class="sxs-lookup"><span data-stu-id="c17ce-154">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="c17ce-155">パラメーター オブジェクトの .NET Framework データ プロバイダー型は、パラメーター オブジェクトの値の .NET Framework 型か、またはパラメーター オブジェクトの `DbType` から推論されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-155">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="c17ce-156">新しい date 型と time 型をサポートするための新しい <xref:System.Data.SqlTypes> データ型は導入されていません。</span><span class="sxs-lookup"><span data-stu-id="c17ce-156">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="c17ce-157">次の表に、SQL Server 2008 の日付と時刻のデータ型と CLR データ型のマッピングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-157">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="c17ce-158">SQL Server のデータ型</span><span class="sxs-lookup"><span data-stu-id="c17ce-158">SQL Server data type</span></span>|<span data-ttu-id="c17ce-159">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="c17ce-159">.NET Framework type</span></span>|<span data-ttu-id="c17ce-160">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="c17ce-160">System.Data.SqlDbType</span></span>|<span data-ttu-id="c17ce-161">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="c17ce-161">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="c17ce-162">date</span><span class="sxs-lookup"><span data-stu-id="c17ce-162">date</span></span>|<span data-ttu-id="c17ce-163">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="c17ce-163">System.DateTime</span></span>|<span data-ttu-id="c17ce-164">Date</span><span class="sxs-lookup"><span data-stu-id="c17ce-164">Date</span></span>|<span data-ttu-id="c17ce-165">Date</span><span class="sxs-lookup"><span data-stu-id="c17ce-165">Date</span></span>|  
|<span data-ttu-id="c17ce-166">時間</span><span class="sxs-lookup"><span data-stu-id="c17ce-166">time</span></span>|<span data-ttu-id="c17ce-167">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="c17ce-167">System.TimeSpan</span></span>|<span data-ttu-id="c17ce-168">時刻</span><span class="sxs-lookup"><span data-stu-id="c17ce-168">Time</span></span>|<span data-ttu-id="c17ce-169">時刻</span><span class="sxs-lookup"><span data-stu-id="c17ce-169">Time</span></span>|  
|<span data-ttu-id="c17ce-170">datetime2</span><span class="sxs-lookup"><span data-stu-id="c17ce-170">datetime2</span></span>|<span data-ttu-id="c17ce-171">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="c17ce-171">System.DateTime</span></span>|<span data-ttu-id="c17ce-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="c17ce-172">DateTime2</span></span>|<span data-ttu-id="c17ce-173">DateTime2</span><span class="sxs-lookup"><span data-stu-id="c17ce-173">DateTime2</span></span>|  
|<span data-ttu-id="c17ce-174">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="c17ce-174">datetimeoffset</span></span>|<span data-ttu-id="c17ce-175">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c17ce-175">System.DateTimeOffset</span></span>|<span data-ttu-id="c17ce-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c17ce-176">DateTimeOffset</span></span>|<span data-ttu-id="c17ce-177">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c17ce-177">DateTimeOffset</span></span>|  
|<span data-ttu-id="c17ce-178">datetime</span><span class="sxs-lookup"><span data-stu-id="c17ce-178">datetime</span></span>|<span data-ttu-id="c17ce-179">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="c17ce-179">System.DateTime</span></span>|<span data-ttu-id="c17ce-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="c17ce-180">DateTime</span></span>|<span data-ttu-id="c17ce-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="c17ce-181">DateTime</span></span>|  
|<span data-ttu-id="c17ce-182">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="c17ce-182">smalldatetime</span></span>|<span data-ttu-id="c17ce-183">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="c17ce-183">System.DateTime</span></span>|<span data-ttu-id="c17ce-184">DateTime</span><span class="sxs-lookup"><span data-stu-id="c17ce-184">DateTime</span></span>|<span data-ttu-id="c17ce-185">DateTime</span><span class="sxs-lookup"><span data-stu-id="c17ce-185">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="c17ce-186">SqlParameter プロパティ</span><span class="sxs-lookup"><span data-stu-id="c17ce-186">SqlParameter Properties</span></span>  
 <span data-ttu-id="c17ce-187">次の表は、日付と時刻のデータ型に関係する `SqlParameter` プロパティの説明です。</span><span class="sxs-lookup"><span data-stu-id="c17ce-187">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="c17ce-188">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c17ce-188">Property</span></span>|<span data-ttu-id="c17ce-189">説明</span><span class="sxs-lookup"><span data-stu-id="c17ce-189">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="c17ce-190">値が null 許容であるかどうかを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-190">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="c17ce-191">サーバーに NULL パラメーター値を送る場合は、<xref:System.DBNull> (Visual Basic の場合は `null`) ではなく、`Nothing` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c17ce-191">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="c17ce-192">データベースの NULL 値の詳細については、「 [Handling Null Values](handling-null-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c17ce-192">For more information about database nulls, see [Handling Null Values](handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="c17ce-193">その値の最大桁数を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-193">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="c17ce-194">この設定は日付と時刻のデータ型では無視されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-194">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="c17ce-195">小数点以下の桁数を取得または設定します。これは `Time`、`DateTime2`、`DateTimeOffset` の時刻部分の値の処理で使用されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-195">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="c17ce-196">既定値は 0 で、これは実際のスケールが値から推論され、サーバーに送信されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-196">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="c17ce-197">日付と時刻のデータ型では無視されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-197">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="c17ce-198">パラメーター値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-198">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="c17ce-199">パラメーター値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-199">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c17ce-200">時刻の値が 0 と 24 の間にない場合は、<xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-200">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="c17ce-201">パラメーターの作成</span><span class="sxs-lookup"><span data-stu-id="c17ce-201">Creating Parameters</span></span>  
 <span data-ttu-id="c17ce-202"><xref:System.Data.SqlClient.SqlParameter> オブジェクトは、そのコンストラクターを使って作成できるほか、<xref:System.Data.SqlClient.SqlCommand> の <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> メソッドを呼び出して、`Add`<xref:System.Data.SqlClient.SqlParameterCollection> コレクションにそれを追加することによって作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-202">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="c17ce-203">`Add` メソッドは、入力としてコンストラクター引数または既存のパラメーター オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c17ce-203">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="c17ce-204">このトピックの次のセクションでは、日付と時刻のパラメーターを指定する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-204">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="c17ce-205">パラメーターの使用に関するその他の例については、「[パラメーターおよびパラメーター データ型の構成](../configuring-parameters-and-parameter-data-types.md)」および「[DataAdapter パラメーター](../dataadapter-parameters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c17ce-205">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="c17ce-206">Date の例</span><span class="sxs-lookup"><span data-stu-id="c17ce-206">Date Example</span></span>  
 <span data-ttu-id="c17ce-207">次のコード フラグメントは、`date` パラメーターの指定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c17ce-207">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a><span data-ttu-id="c17ce-208">Time の例</span><span class="sxs-lookup"><span data-stu-id="c17ce-208">Time Example</span></span>  
 <span data-ttu-id="c17ce-209">次のコード フラグメントは、`time` パラメーターの指定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c17ce-209">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a><span data-ttu-id="c17ce-210">Datetime2 の例</span><span class="sxs-lookup"><span data-stu-id="c17ce-210">Datetime2 Example</span></span>  
 <span data-ttu-id="c17ce-211">次のコード フラグメントは、`datetime2` パラメーターの日付と時刻の指定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c17ce-211">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="c17ce-212">DateTimeOffSet の例</span><span class="sxs-lookup"><span data-stu-id="c17ce-212">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="c17ce-213">次のコード フラグメントは、`DateTimeOffSet` パラメーターの日付と時刻、およびタイム ゾーン オフセット 0 を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c17ce-213">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a><span data-ttu-id="c17ce-214">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="c17ce-214">AddWithValue</span></span>  
 <span data-ttu-id="c17ce-215">次のコード フラグメントに示すように、<xref:System.Data.SqlClient.SqlCommand> の `AddWithValue` メソッドを使用してパラメーターを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-215">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="c17ce-216">ただし、`AddWithValue` メソッドでは、パラメーターの <xref:System.Data.SqlClient.SqlParameter.DbType%2A> または <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="c17ce-216">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="c17ce-217">`@date` パラメーターは、サーバー上の `date`、`datetime`、または `datetime2` データ型にマッピングできます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-217">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="c17ce-218">新しい `datetime` データ型を使用する場合は、パラメーターの <xref:System.Data.SqlDbType> プロパティをインスタンスのデータ型に明示的に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c17ce-218">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="c17ce-219"><xref:System.Data.SqlDbType.Variant> を使用するか、または暗黙的にパラメーター値を指定すると、`datetime` データ型および `smalldatetime` データ型との下位互換性の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c17ce-219">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="c17ce-220">次の表は、どの CLR 型からどの `SqlDbTypes` が推論されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="c17ce-220">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="c17ce-221">CLR 型</span><span class="sxs-lookup"><span data-stu-id="c17ce-221">CLR type</span></span>|<span data-ttu-id="c17ce-222">推定される SqlDbType</span><span class="sxs-lookup"><span data-stu-id="c17ce-222">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="c17ce-223">DateTime</span><span class="sxs-lookup"><span data-stu-id="c17ce-223">DateTime</span></span>|<span data-ttu-id="c17ce-224">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="c17ce-224">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="c17ce-225">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="c17ce-225">TimeSpan</span></span>|<span data-ttu-id="c17ce-226">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="c17ce-226">SqlDbType.Time</span></span>|  
|<span data-ttu-id="c17ce-227">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c17ce-227">DateTimeOffset</span></span>|<span data-ttu-id="c17ce-228">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c17ce-228">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="c17ce-229">日付と時刻データの取得</span><span class="sxs-lookup"><span data-stu-id="c17ce-229">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="c17ce-230">SQL Server 2008 の日付値および時刻値を取得するためのメソッドを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-230">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="c17ce-231">SqlClient のメソッド</span><span class="sxs-lookup"><span data-stu-id="c17ce-231">SqlClient method</span></span>|<span data-ttu-id="c17ce-232">説明</span><span class="sxs-lookup"><span data-stu-id="c17ce-232">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="c17ce-233">指定された列の値を <xref:System.DateTime> 構造体として取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-233">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="c17ce-234">指定された列の値を <xref:System.DateTimeOffset> 構造体として取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-234">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="c17ce-235">そのフィールドの基になるプロバイダー固有の型である型を返します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-235">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="c17ce-236">新しい日付と時刻の型に対して `GetFieldType` と同じ型を返します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-236">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="c17ce-237">指定された列の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-237">Retrieves the value of the specified column.</span></span> <span data-ttu-id="c17ce-238">新しい日付と時刻の型に対して `GetValue` と同じ型を返します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-238">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="c17ce-239">指定した配列内の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-239">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="c17ce-240">列の値を <xref:System.Data.SqlTypes.SqlString> として取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-240">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="c17ce-241">データを `SqlString` として表現できない場合、<xref:System.InvalidCastException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-241">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="c17ce-242">列データをその既定の `SqlDbType` として取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-242">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="c17ce-243">新しい日付と時刻の型に対して `GetValue` と同じ型を返します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-243">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="c17ce-244">指定した配列内の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-244">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="c17ce-245">Type System Version が SQL Server 2005 に設定されている場合、列の値を文字列として取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-245">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="c17ce-246">データを文字列として表現できない場合、<xref:System.InvalidCastException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-246">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="c17ce-247">指定された列の値を <xref:System.TimeSpan> 構造体として取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-247">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="c17ce-248">指定した列の値を、その基になる CLR 型として取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-248">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="c17ce-249">配列内の列の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-249">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="c17ce-250">結果セットのメタデータを記述する <xref:System.Data.DataTable> を返します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-250">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c17ce-251">新しい日付と時刻の `SqlDbTypes` は、SQL Server でインプロセスで実行されているコードではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c17ce-251">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="c17ce-252">そのような型の 1 つがサーバーに渡されると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-252">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="c17ce-253">日付値と時刻値のリテラル指定</span><span class="sxs-lookup"><span data-stu-id="c17ce-253">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="c17ce-254">日付と時刻のデータ型は、さまざまなリテラル文字列形式を使用して指定できます。SQL Server は、実行時にそれらを内部の日付/時刻構造体に変換します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-254">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="c17ce-255">SQL Server では、一重引用符 (') で囲まれた日付と時刻のデータが認識されます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-255">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="c17ce-256">次の例に、いくつかの形式を示します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-256">The following examples demonstrate some formats:</span></span>  
  
- <span data-ttu-id="c17ce-257">アルファベットの日付形式 (`'October 15, 2006'` など)。</span><span class="sxs-lookup"><span data-stu-id="c17ce-257">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
- <span data-ttu-id="c17ce-258">数値の日付形式 (`'10/15/2006'`など)。</span><span class="sxs-lookup"><span data-stu-id="c17ce-258">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
- <span data-ttu-id="c17ce-259">区切られていない文字列形式 (`'20061015'` など。これは ISO 標準日付形式を使用している場合、2006 年 10 月 15 日と解釈される)。</span><span class="sxs-lookup"><span data-stu-id="c17ce-259">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c17ce-260">すべてのリテラル文字列形式と、日付と時刻のデータ型のその他の機能に関する完全なドキュメントについては、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c17ce-260">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="c17ce-261">時刻の値が 0 と 24 の間にない場合は、<xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c17ce-261">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="c17ce-262">SQL Server オンライン ブックの関連トピック</span><span class="sxs-lookup"><span data-stu-id="c17ce-262">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="c17ce-263">SQL Server での日付値と時刻値の使用方法の詳細については、SQL Server オンライン ブックで以下のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c17ce-263">For more information about working with date and time values in SQL Server, see the following resources in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="c17ce-264">トピック</span><span class="sxs-lookup"><span data-stu-id="c17ce-264">Topic</span></span>|<span data-ttu-id="c17ce-265">説明</span><span class="sxs-lookup"><span data-stu-id="c17ce-265">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c17ce-266">日付と時刻のデータ型および関数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c17ce-266">Date and Time Data Types and Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|<span data-ttu-id="c17ce-267">Transact-SQL の日付と時刻のデータ型および関数の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-267">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|<span data-ttu-id="c17ce-268">[日時データの使用](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="c17ce-268">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>|<span data-ttu-id="c17ce-269">日付と時刻のデータ型と関数の情報、および使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-269">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="c17ce-270">データ型 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c17ce-270">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)|<span data-ttu-id="c17ce-271">SQL Server でのシステム データ型について説明します。</span><span class="sxs-lookup"><span data-stu-id="c17ce-271">Describes system data types in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c17ce-272">関連項目</span><span class="sxs-lookup"><span data-stu-id="c17ce-272">See also</span></span>

- [<span data-ttu-id="c17ce-273">SQL Server データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="c17ce-273">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="c17ce-274">パラメーターおよびパラメーター データ型の構成</span><span class="sxs-lookup"><span data-stu-id="c17ce-274">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="c17ce-275">SQL Server データ型と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c17ce-275">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="c17ce-276">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="c17ce-276">ADO.NET Overview</span></span>](../ado-net-overview.md)
