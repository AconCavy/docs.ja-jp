---
title: GetSchema およびスキーマ コレクション
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: e18c23e9bbec97a64110aba6eb7241761ecece06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149558"
---
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="3df6e-102">GetSchema およびスキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="3df6e-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="3df6e-103">それぞれの .NET Framework マネージド プロバイダーの **Connection** クラスは、**GetSchema** メソッドを実装します。このメソッドは、現在接続されているデータベースに関するスキーマ情報を取得するために使用されます。**GetSchema** メソッドから返されるスキーマ情報は、<xref:System.Data.DataTable> という形式になります。</span><span class="sxs-lookup"><span data-stu-id="3df6e-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="3df6e-104">**GetSchema** メソッドはオーバーロードされたメソッドであり、オプションのパラメーターで、取得するスキーマ コレクションを指定し、返される情報の量を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="3df6e-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="3df6e-105">スキーマ コレクションの指定</span><span class="sxs-lookup"><span data-stu-id="3df6e-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="3df6e-106">**GetSchema** メソッドの最初のオプション パラメーターは、文字列として指定されるコレクションの名前です。</span><span class="sxs-lookup"><span data-stu-id="3df6e-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="3df6e-107">スキーマ コレクションには 2 種類あります。すべてのプロバイダーに共通している一般的なスキーマ コレクションと、各プロバイダーによって固有のスキーマ コレクションです。</span><span class="sxs-lookup"><span data-stu-id="3df6e-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="3df6e-108">.NET Framework マネージド プロバイダーでは、引数を指定しないで、またはスキーマ コレクション名に "MetaDataCollections" を指定して **GetSchema** メソッドを呼び出すことにより、サポートされるスキーマ コレクションの一覧を決定します。</span><span class="sxs-lookup"><span data-stu-id="3df6e-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="3df6e-109">これにより、サポートされるスキーマ コレクションの一覧、それぞれがサポートする制限数、および使用する識別子部分の数と共に、<xref:System.Data.DataTable> が返されます。</span><span class="sxs-lookup"><span data-stu-id="3df6e-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="3df6e-110">スキーマ コレクションの取得例</span><span class="sxs-lookup"><span data-stu-id="3df6e-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="3df6e-111">.NET Framework Data Provider for the SQL Server の <xref:System.Data.SqlClient.SqlConnection> クラスの <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> メソッドを使って、**AdventureWorks** サンプル データベースに含まれるすべてのテーブルに関するスキーマ情報を取得する方法について、いくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3df6e-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
   End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
   Console.WriteLine("Press any key to continue.");  
   Console.ReadKey();  
   }  
 }  
  
  private static string GetConnectionString()  
  {  
   // To avoid storing the connection string in your code,  
   // you can retrieve it from a configuration file.  
   return "Data Source=(local);Database=AdventureWorks;" +  
      "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3df6e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3df6e-112">See also</span></span>

- [<span data-ttu-id="3df6e-113">データベース スキーマ情報の取得</span><span class="sxs-lookup"><span data-stu-id="3df6e-113">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="3df6e-114">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="3df6e-114">ADO.NET Overview</span></span>](ado-net-overview.md)
