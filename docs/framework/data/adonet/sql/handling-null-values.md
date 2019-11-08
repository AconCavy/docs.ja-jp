---
title: null 値の処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 091fde9a6149f72577e0cf38c8ebf1536abdf6ea
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738204"
---
# <a name="handling-null-values"></a><span data-ttu-id="68c53-102">null 値の処理</span><span class="sxs-lookup"><span data-stu-id="68c53-102">Handling Null Values</span></span>
<span data-ttu-id="68c53-103">列の値が不明または欠落している場合は、リレーショナル データベースの NULL 値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-103">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="68c53-104">NULL は空文字列 (文字または日付時刻データ型) でもゼロ値 (数値データ型) でもありません。</span><span class="sxs-lookup"><span data-stu-id="68c53-104">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="68c53-105">ANSI SQL-92 の規格では、すべてのデータ型について NULL は同一でなければならないと規定されているため、すべての NULL が一貫して処理されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-105">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="68c53-106"><xref:System.Data.SqlTypes> 名前空間では、<xref:System.Data.SqlTypes.INullable> インターフェイスを実装することで NULL セマンティクスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-106">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="68c53-107"><xref:System.Data.SqlTypes> 内の各データ型には、それぞれ独自に `IsNull` プロパティと `Null` 値があり、データ型のインスタンスに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="68c53-107">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68c53-108">.NET Framework version 2.0 では、NULL 許容型がサポートされました。この型を使用することで、値型を拡張して基になる型のすべての値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="68c53-108">The .NET Framework version 2.0 introduced support for nullable types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="68c53-109">これらの CLR NULL 許容型は、<xref:System.Nullable> 構造体のインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="68c53-109">These CLR nullable types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="68c53-110">この機能は、値の型がボックスまたはアンボックスされるときに特に有効であり、オブジェクト型との互換性が強化されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-110">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="68c53-111">ANSI SQL の NULL は `null` 参照 (Visual Basic では `Nothing`) と動作が異なるため、CLR NULL 許容型は NULL のデータベースへの格納を意図したものではありません。</span><span class="sxs-lookup"><span data-stu-id="68c53-111">CLR nullable types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="68c53-112">データベースの ANSI SQL NULL 値を操作するには、<xref:System.Data.SqlTypes> ではなく <xref:System.Nullable> NULL を使用します。</span><span class="sxs-lookup"><span data-stu-id="68c53-112">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="68c53-113">での CLR null 許容型の使用の詳細については[Visual Basic 「null 許容値型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)」および「」 C# [を参照してください。](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="68c53-113">For more information on working with CLR nullable types in Visual Basic see [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Nullable value types](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="68c53-114">NULL および 3 つの値を持つロジック</span><span class="sxs-lookup"><span data-stu-id="68c53-114">Nulls and Three-Valued Logic</span></span>  
 <span data-ttu-id="68c53-115">列定義に NULL 値を許可することで、3 つの値を持つロジックをアプリケーションに定義できます。</span><span class="sxs-lookup"><span data-stu-id="68c53-115">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="68c53-116">比較によって、次の 3 つの条件のうちの 1 つを評価できます。</span><span class="sxs-lookup"><span data-stu-id="68c53-116">A comparison can evaluate to one of three conditions:</span></span>  
  
- <span data-ttu-id="68c53-117">True</span><span class="sxs-lookup"><span data-stu-id="68c53-117">True</span></span>  
  
- <span data-ttu-id="68c53-118">False</span><span class="sxs-lookup"><span data-stu-id="68c53-118">False</span></span>  
  
- <span data-ttu-id="68c53-119">不明</span><span class="sxs-lookup"><span data-stu-id="68c53-119">Unknown</span></span>  
  
 <span data-ttu-id="68c53-120">NULL は不明であるとされるため、2 つの NULL 値を相互に比較した場合、同等であるとは見なされません。</span><span class="sxs-lookup"><span data-stu-id="68c53-120">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="68c53-121">算術演算子を使用する式では、オペランドのいずれかが NULL である場合は結果も NULL になります。</span><span class="sxs-lookup"><span data-stu-id="68c53-121">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="68c53-122">NULL および SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="68c53-122">Nulls and SqlBoolean</span></span>  
 <span data-ttu-id="68c53-123"><xref:System.Data.SqlTypes> 間の比較により、<xref:System.Data.SqlTypes.SqlBoolean> が返されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-123">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="68c53-124">各 `IsNull` の `SqlType` 関数により、<xref:System.Data.SqlTypes.SqlBoolean> が返され、NULL 値の確認に使用できます。</span><span class="sxs-lookup"><span data-stu-id="68c53-124">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="68c53-125">次の truth テーブルは、NULL 値がある場合の AND、OR、および NOT 演算子の機能を示します</span><span class="sxs-lookup"><span data-stu-id="68c53-125">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="68c53-126">(T=true、F=false、U=不明または NULL)。</span><span class="sxs-lookup"><span data-stu-id="68c53-126">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="68c53-127">![真理テーブル](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="68c53-127">![Truth Table](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansi_nulls-option"></a><span data-ttu-id="68c53-128">ANSI_NULLS オプションについて</span><span class="sxs-lookup"><span data-stu-id="68c53-128">Understanding the ANSI_NULLS Option</span></span>  
 <span data-ttu-id="68c53-129"><xref:System.Data.SqlTypes> では、ANSI_NULLS オプションが SQL Server で設定された場合と同じセマンティクスになります。</span><span class="sxs-lookup"><span data-stu-id="68c53-129"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="68c53-130">すべての算術演算子 (+、-、\*、/、%)、ビットごとの演算子 (~、&、\|)、およびほとんどの関数は、プロパティ `IsNull`を除き、オペランドまたは引数のいずれかが null の場合は null を返します。</span><span class="sxs-lookup"><span data-stu-id="68c53-130">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, \|), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="68c53-131">ANSI SQL-92 標準では、WHERE 句で*columnName* = NULL はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="68c53-131">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="68c53-132">SQL Server では、ANSI_NULLS オプションによって、データベース内の既定の NULL 値と、NULL 値に対する比較の評価の両方が制御されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-132">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="68c53-133">ANSI_NULLS がオン (既定) である場合、IS NULL 演算子を NULL 値のテストを行う式で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68c53-133">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="68c53-134">たとえば次の比較では、ANSI_NULLS がオンである場合、常に不明となります。</span><span class="sxs-lookup"><span data-stu-id="68c53-134">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```sql
colname > NULL  
```  
  
 <span data-ttu-id="68c53-135">NULL 値を含む変数との比較でも不明となります。</span><span class="sxs-lookup"><span data-stu-id="68c53-135">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```sql
colname > @MyVariable  
```  
  
 <span data-ttu-id="68c53-136">NULL 値をテストするには、IS NULL または IS NOT NULL 述語を使用します。</span><span class="sxs-lookup"><span data-stu-id="68c53-136">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="68c53-137">これにより WHERE 句が複雑になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="68c53-137">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="68c53-138">たとえば、AdventureWorks Customer テーブル内の TerritoryID 列では、NULL 値が許可されています。</span><span class="sxs-lookup"><span data-stu-id="68c53-138">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="68c53-139">SELECT ステートメントによってその他の値と合わせて NULL 値もテストされる場合は、IS NULL 述語を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="68c53-139">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="68c53-140">SQL Server で ANSI_NULLS をオフに設定すると、等値演算子を使用する式を作成し、NULL 値と比較できます。</span><span class="sxs-lookup"><span data-stu-id="68c53-140">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="68c53-141">ただし、別の接続からその接続に対して NULL オプションを設定することを防ぐことはできません。</span><span class="sxs-lookup"><span data-stu-id="68c53-141">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="68c53-142">IS NULL を使用した NULL 値のテストは、接続の ANSI_NULLS 設定にかかわらず、常に動作します。</span><span class="sxs-lookup"><span data-stu-id="68c53-142">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="68c53-143">`DataSet` では、ANSI_NULLS をオフに設定することはできません。<xref:System.Data.SqlTypes> における NULL 値の処理については、常に ANSI SQL-92 標準に準拠します。</span><span class="sxs-lookup"><span data-stu-id="68c53-143">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="68c53-144">NULL 値の割り当て</span><span class="sxs-lookup"><span data-stu-id="68c53-144">Assigning Null Values</span></span>  
 <span data-ttu-id="68c53-145">NULL 値は特殊であり、ストレージおよび割り当てのセマンティクスは、システムおよびストレージ システムの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="68c53-145">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="68c53-146">`Dataset` は、異なる種類のシステムおよびストレージ システムで使用できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="68c53-146">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="68c53-147">このセクションでは、異なる種類のシステム上にある <xref:System.Data.DataColumn> の <xref:System.Data.DataRow> に NULL 値を割り当てるための NULL セマンティクスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="68c53-147">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="68c53-148">この割り当ては、任意の型の `DataColumn` で有効です。</span><span class="sxs-lookup"><span data-stu-id="68c53-148">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="68c53-149">その型が `INullable` を実装している場合は、`DBNull.Value` が厳密に型指定された適切な NULL 値に強制的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-149">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="68c53-150">すべての <xref:System.Data.SqlTypes> データ型で `INullable` を実装します。</span><span class="sxs-lookup"><span data-stu-id="68c53-150">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="68c53-151">暗黙的なキャスト演算子を使用して、厳密に型指定された NULL 値を列のデータ型に変換できる場合は、割り当てが行われます。</span><span class="sxs-lookup"><span data-stu-id="68c53-151">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="68c53-152">変換できない場合は、無効なキャスト例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="68c53-152">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="68c53-153">特定の `DataColumn` データ型について 'null' が有効であった場合、`DbNull.Value` 型 (`Null`) に関連付けられている、適切な `INullable` または `SqlType.Null` に強制的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-153">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="68c53-154">UDT 列の場合、NULL 値は常に `DataColumn` に関連付けられている型に基づいて格納されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-154">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="68c53-155">`DataColumn` に関連付けられている UDT が `INullable` を実装せず、サブクラスで実装される場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="68c53-155">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="68c53-156">この場合、派生クラスに関連付けられた厳密に型指定された NULL 値が割り当てられていれば、NULL ストレージが常に DataColumn のデータ型と一致するため、型指定されていない `DbNull.Value` として格納されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-156">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68c53-157">`Nullable<T>` または <xref:System.Nullable> 構造体は、現在 `DataSet` ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="68c53-157">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="68c53-158">複数列 (行) の割り当て</span><span class="sxs-lookup"><span data-stu-id="68c53-158">Multiple Column (Row) Assignment</span></span>  
 <span data-ttu-id="68c53-159">`DataTable.Add` を行にマップできる、`DataTable.LoadDataRow` や <xref:System.Data.DataRow.ItemArray%2A> などの API については、DataColumn の既定値に 'null' をマップします。</span><span class="sxs-lookup"><span data-stu-id="68c53-159">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="68c53-160">配列内のオブジェクトに `DbNull.Value` またはその厳密に型指定された値が含まれる場合は、上記と同じ規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-160">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="68c53-161">さらに、`DataRow.["columnName"]` の NULL 値割り当てのインスタンスには、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-161">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1. <span data-ttu-id="68c53-162">*既定の既定値は*、厳密に型指定された null 列を除く、厳密に型指定された適切な null 値であるすべてのに対して `DbNull.Value` です。</span><span class="sxs-lookup"><span data-stu-id="68c53-162">The default *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2. <span data-ttu-id="68c53-163">XML ファイルへのシリアル化中に NULL 値が書き出されることはありません ("xsi:nil" と同じ)。</span><span class="sxs-lookup"><span data-stu-id="68c53-163">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3. <span data-ttu-id="68c53-164">既定値を含む NULL 以外のすべての値は、常に XML へのシリアル化中に書き出されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-164">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="68c53-165">これは、NULL 値 (xsi:nil) が明示的で既定値が暗黙的である、XSD/XML セマンティクスとは異なります (XML にない場合は、検証パーサーが関連付けられた XSD スキーマから取得します)。</span><span class="sxs-lookup"><span data-stu-id="68c53-165">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="68c53-166">逆に `DataTable` では、NULL 値が暗黙的で、既定値が明示的になります。</span><span class="sxs-lookup"><span data-stu-id="68c53-166">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4. <span data-ttu-id="68c53-167">XML 入力から読み取られた各行の欠落している列値にはすべて、NULL が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="68c53-167">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="68c53-168"><xref:System.Data.DataTable.NewRow%2A> または類似のメソッドを使用して作成された行には、DataColumn の既定値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="68c53-168">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5. <span data-ttu-id="68c53-169"><xref:System.Data.DataRow.IsNull%2A> メソッドは、`true` と `DbNull.Value` のどちらに対しても `INullable.Null` を返します。</span><span class="sxs-lookup"><span data-stu-id="68c53-169">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="68c53-170">NULL 値の割り当て</span><span class="sxs-lookup"><span data-stu-id="68c53-170">Assigning Null Values</span></span>  
 <span data-ttu-id="68c53-171">任意の <xref:System.Data.SqlTypes> インスタンスの既定値は NULL です。</span><span class="sxs-lookup"><span data-stu-id="68c53-171">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="68c53-172"><xref:System.Data.SqlTypes> の NULL 値は型固有であり、`DbNull` などの 1 つの値で表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="68c53-172">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="68c53-173">NULL 値の確認には、`IsNull` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="68c53-173">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="68c53-174">NULL 値は、次のコード サンプルに示すように <xref:System.Data.DataColumn> に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="68c53-174">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="68c53-175">NULL 値は、例外をトリガーすることなく `SqlTypes` 変数に直接割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="68c53-175">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="68c53-176">例</span><span class="sxs-lookup"><span data-stu-id="68c53-176">Example</span></span>  
 <span data-ttu-id="68c53-177">次のコード サンプルでは、<xref:System.Data.DataTable> および <xref:System.Data.SqlTypes.SqlInt32> として定義される 2 つの列を持つ <xref:System.Data.SqlTypes.SqlString> が作成されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-177">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="68c53-178">このコードでは既知の値の行が 1 行、NULL 値の行が 1 行追加され、<xref:System.Data.DataTable> を通じて反復処理されます。これにより値が変数に割り当てられ、コンソール ウィンドウに出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-178">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="68c53-179">この例を実行すると、次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-179">This example displays the following results:</span></span>  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="68c53-180">NULL 値と SqlTypes および CLR 型との比較</span><span class="sxs-lookup"><span data-stu-id="68c53-180">Comparing Null Values with SqlTypes and CLR Types</span></span>  
 <span data-ttu-id="68c53-181">NULL 値を比較する場合は、`Equals` メソッドによって <xref:System.Data.SqlTypes> で NULL 値を評価する方法と、CLR 型を使用する方法との違いを理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="68c53-181">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="68c53-182"><xref:System.Data.SqlTypes>`Equals` メソッドではすべて、NULL 値の評価にデータベース セマンティクスが使用されます。一方または両方の値が NULL である場合は、比較によって NULL が得られます。</span><span class="sxs-lookup"><span data-stu-id="68c53-182">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="68c53-183">その一方で、2 つの `Equals` に対して CLR <xref:System.Data.SqlTypes> メソッドを使用した場合は、両方が NULL であれば true が得られます。</span><span class="sxs-lookup"><span data-stu-id="68c53-183">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="68c53-184">これは、CLR `String.Equals` メソッドなどのインスタンス メソッドを使用した場合と、`SqlString.Equals` などの静的/共有メソッドを使用した場合の違いを反映しています。</span><span class="sxs-lookup"><span data-stu-id="68c53-184">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="68c53-185">次のコード サンプルでは、`SqlString.Equals` メソッドと `String.Equals` メソッドにそれぞれ NULL 値のペアを渡し、次に空の文字列のペアを渡した場合の、各メソッドの結果の違いを示します。</span><span class="sxs-lookup"><span data-stu-id="68c53-185">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="68c53-186">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="68c53-186">The code produces the following output:</span></span>  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="see-also"></a><span data-ttu-id="68c53-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="68c53-187">See also</span></span>

- [<span data-ttu-id="68c53-188">SQL Server データ型と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="68c53-188">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="68c53-189">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="68c53-189">ADO.NET Overview</span></span>](../ado-net-overview.md)
