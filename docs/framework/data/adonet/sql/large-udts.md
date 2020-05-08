---
title: 大きな UDT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: f55f6eccf3566a2391204e1ca4349ae5dff01954
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148557"
---
# <a name="large-udts"></a><span data-ttu-id="7ab85-102">大きな UDT</span><span class="sxs-lookup"><span data-stu-id="7ab85-102">Large UDTs</span></span>
<span data-ttu-id="7ab85-103">開発者は、ユーザー定義型 (UDT) を使用すると、SQL Server データベースに共通言語ランタイム (CLR) オブジェクトを格納して、サーバーのスカラー型システムを拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="7ab85-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="7ab85-104">UDT は複数の要素を持つことができ、動作を定義できます。この点は、1 つの SQL Server システム データ型から構成される従来の別名データ型と異なります。</span><span class="sxs-lookup"><span data-stu-id="7ab85-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ab85-105">大きな UDT に対する SqlClient のサポート強化を利用するには、.NET Framework 3.5 SP1 以降をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ab85-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="7ab85-106">従来は、UDT の最大サイズが 8 KB に制限されていました。</span><span class="sxs-lookup"><span data-stu-id="7ab85-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="7ab85-107">SQL Server 2008 では、<xref:Microsoft.SqlServer.Server.Format.UserDefined> 形式の UDT に対するこの制限が廃止されています。</span><span class="sxs-lookup"><span data-stu-id="7ab85-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="7ab85-108">ユーザー定義型の完全な説明については、使用している SQL Server のバージョンに対応する SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ab85-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="7ab85-109">**SQL Server のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="7ab85-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="7ab85-110">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="7ab85-110">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="7ab85-111">GetSchema による UDT スキーマの取得</span><span class="sxs-lookup"><span data-stu-id="7ab85-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="7ab85-112"><xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> の <xref:System.Data.SqlClient.SqlConnection> メソッドは、データベース スキーマ情報を <xref:System.Data.DataTable> に返します。</span><span class="sxs-lookup"><span data-stu-id="7ab85-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="7ab85-113">詳しくは、「[SQL Server スキーマ コレクション](../sql-server-schema-collections.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7ab85-113">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="7ab85-114">UDT の GetSchemaTable 列値</span><span class="sxs-lookup"><span data-stu-id="7ab85-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="7ab85-115"><xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> の <xref:System.Data.SqlClient.SqlDataReader> メソッドは、列メタデータを記述する <xref:System.Data.DataTable> を返します。</span><span class="sxs-lookup"><span data-stu-id="7ab85-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="7ab85-116">次の表では、SQL Server 2005 と SQL Server 2008 の間の大きな UDT に対する列メタデータの違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7ab85-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="7ab85-117">SqlDataReader 列</span><span class="sxs-lookup"><span data-stu-id="7ab85-117">SqlDataReader column</span></span>|<span data-ttu-id="7ab85-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="7ab85-118">SQL Server 2005</span></span>|<span data-ttu-id="7ab85-119">SQL Server 2008 以降</span><span class="sxs-lookup"><span data-stu-id="7ab85-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="7ab85-120">可変</span><span class="sxs-lookup"><span data-stu-id="7ab85-120">Varies</span></span>|<span data-ttu-id="7ab85-121">可変</span><span class="sxs-lookup"><span data-stu-id="7ab85-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="7ab85-122">255</span><span class="sxs-lookup"><span data-stu-id="7ab85-122">255</span></span>|<span data-ttu-id="7ab85-123">255</span><span class="sxs-lookup"><span data-stu-id="7ab85-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="7ab85-124">255</span><span class="sxs-lookup"><span data-stu-id="7ab85-124">255</span></span>|<span data-ttu-id="7ab85-125">255</span><span class="sxs-lookup"><span data-stu-id="7ab85-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="7ab85-126">UDT インスタンス</span><span class="sxs-lookup"><span data-stu-id="7ab85-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="7ab85-127">UDT インスタンス</span><span class="sxs-lookup"><span data-stu-id="7ab85-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="7ab85-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="7ab85-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="7ab85-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="7ab85-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="7ab85-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="7ab85-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="7ab85-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="7ab85-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="7ab85-132">3 つの部分から成る名前 (*Database.SchemaName.TypeName* として指定)</span><span class="sxs-lookup"><span data-stu-id="7ab85-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="7ab85-133">可変</span><span class="sxs-lookup"><span data-stu-id="7ab85-133">Varies</span></span>|<span data-ttu-id="7ab85-134">可変</span><span class="sxs-lookup"><span data-stu-id="7ab85-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="7ab85-135">SqlDataReader に関する注意点</span><span class="sxs-lookup"><span data-stu-id="7ab85-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="7ab85-136">SQL Server 2008 以降、<xref:System.Data.SqlClient.SqlDataReader> は大きな UDT 値を取得できるように拡張されました。</span><span class="sxs-lookup"><span data-stu-id="7ab85-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="7ab85-137"><xref:System.Data.SqlClient.SqlDataReader> によって処理される UDT 値の大きさは、使用している SQL Server のバージョンと、接続文字列で指定されている `Type System Version` によって異なります。</span><span class="sxs-lookup"><span data-stu-id="7ab85-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="7ab85-138">詳細については、「<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ab85-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="7ab85-139"><xref:System.Data.SqlClient.SqlDataReader> の次のメソッドは、`Type System Version` が SQL Server 2005 に設定されている場合、UDT ではなく <xref:System.Data.SqlTypes.SqlBinary> を返します。</span><span class="sxs-lookup"><span data-stu-id="7ab85-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="7ab85-140">次のメソッドは、`Type System Version` が SQL Server 2005 に設定されている場合、UDT ではなく `Byte[]` の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="7ab85-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="7ab85-141">現在のバージョンの ADO.NET については、変換が行われないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7ab85-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="7ab85-142">SqlParameters パラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="7ab85-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="7ab85-143">次の <xref:System.Data.SqlClient.SqlParameter> プロパティは、大きな UDT で動作するように拡張されています。</span><span class="sxs-lookup"><span data-stu-id="7ab85-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="7ab85-144">SqlParameter プロパティ</span><span class="sxs-lookup"><span data-stu-id="7ab85-144">SqlParameter Property</span></span>|<span data-ttu-id="7ab85-145">説明</span><span class="sxs-lookup"><span data-stu-id="7ab85-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="7ab85-146">パラメーターの値を表すオブジェクトを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="7ab85-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="7ab85-147">既定値は null です。</span><span class="sxs-lookup"><span data-stu-id="7ab85-147">The default is null.</span></span> <span data-ttu-id="7ab85-148">このプロパティは、`SqlBinary`、`Byte[]`、またはマネージド オブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="7ab85-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="7ab85-149">パラメーターの値を表すオブジェクトを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="7ab85-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="7ab85-150">既定値は null です。</span><span class="sxs-lookup"><span data-stu-id="7ab85-150">The default is null.</span></span> <span data-ttu-id="7ab85-151">このプロパティは、`SqlBinary`、`Byte[]`、またはマネージド オブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="7ab85-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="7ab85-152">解決するパラメーター値のサイズを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="7ab85-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="7ab85-153">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="7ab85-153">The default value is 0.</span></span> <span data-ttu-id="7ab85-154">プロパティには、パラメーター値のサイズを表す整数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7ab85-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="7ab85-155">大きな UDT の場合は UDT の実際のサイズに、不明な場合は -1 になります。</span><span class="sxs-lookup"><span data-stu-id="7ab85-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="7ab85-156">データの取得例</span><span class="sxs-lookup"><span data-stu-id="7ab85-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="7ab85-157">次のコード フラグメントは、大きな UDT を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7ab85-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="7ab85-158">`connectionString` 変数は SQL Server データベースへの有効な接続を前提とし、`commandString` 変数は有効な SELECT ステートメントで主キー列が最初に記載されていることを前提とします。</span><span class="sxs-lookup"><span data-stu-id="7ab85-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
```csharp  
using (SqlConnection connection = new SqlConnection(
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ab85-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ab85-159">See also</span></span>

- [<span data-ttu-id="7ab85-160">パラメーターおよびパラメーター データ型の構成</span><span class="sxs-lookup"><span data-stu-id="7ab85-160">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="7ab85-161">データベース スキーマ情報の取得</span><span class="sxs-lookup"><span data-stu-id="7ab85-161">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="7ab85-162">SQL Server データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="7ab85-162">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="7ab85-163">SQL Server のバイナリ データと大きな値のデータ</span><span class="sxs-lookup"><span data-stu-id="7ab85-163">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="7ab85-164">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="7ab85-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
