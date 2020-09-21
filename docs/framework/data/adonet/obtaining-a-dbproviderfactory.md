---
title: DbProviderFactory の取得
description: DbProviderFactories クラスから DbProviderFactory を取得して、.NET Framework の特定のデータ ソースを操作する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: 0c7c89a9104ac72bf03f2900e7ca474b709be40c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554463"
---
# <a name="obtaining-a-dbproviderfactory"></a><span data-ttu-id="29fec-103">DbProviderFactory の取得</span><span class="sxs-lookup"><span data-stu-id="29fec-103">Obtaining a DbProviderFactory</span></span>
<span data-ttu-id="29fec-104"><xref:System.Data.Common.DbProviderFactory> を取得する過程では、データ プロバイダーに関する情報が <xref:System.Data.Common.DbProviderFactories> クラスに渡されます。</span><span class="sxs-lookup"><span data-stu-id="29fec-104">The process of obtaining a <xref:System.Data.Common.DbProviderFactory> involves passing information about a data provider to the <xref:System.Data.Common.DbProviderFactories> class.</span></span> <span data-ttu-id="29fec-105"><xref:System.Data.Common.DbProviderFactories.GetFactory%2A> メソッドはこの情報に基づいて、厳密に型指定されたプロバイダー ファクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="29fec-105">Based on this information, the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method creates a strongly typed provider factory.</span></span> <span data-ttu-id="29fec-106">たとえば、<xref:System.Data.SqlClient.SqlClientFactory> を作成するには、`GetFactory` の引数にプロバイダー名 System.Data.SqlClient を文字列として指定します。</span><span class="sxs-lookup"><span data-stu-id="29fec-106">For example, to create a <xref:System.Data.SqlClient.SqlClientFactory>, you can pass `GetFactory` a string with the provider name specified as "System.Data.SqlClient".</span></span> <span data-ttu-id="29fec-107">`GetFactory` には、<xref:System.Data.DataRow> を引数として受け取るオーバーロードも存在します。</span><span class="sxs-lookup"><span data-stu-id="29fec-107">The other overload of `GetFactory` takes a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="29fec-108">プロバイダー ファクトリを作成すると、対応するメソッドを使って他のオブジェクトを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="29fec-108">Once you create the provider factory, you can then use its methods to create additional objects.</span></span> <span data-ttu-id="29fec-109">`SqlClientFactory` のメソッドには、<xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>、<xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>、<xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A> などがあります。</span><span class="sxs-lookup"><span data-stu-id="29fec-109">Some of the methods of a `SqlClientFactory` include <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, and <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29fec-110">同様の機能は、.NET Framework の <xref:System.Data.OracleClient.OracleClientFactory> クラス、<xref:System.Data.Odbc.OdbcFactory> クラス、および <xref:System.Data.OleDb.OleDbFactory> クラスにも用意されています。</span><span class="sxs-lookup"><span data-stu-id="29fec-110">The .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, and <xref:System.Data.OleDb.OleDbFactory> classes also provide similar functionality.</span></span>  
  
## <a name="registering-dbproviderfactories"></a><span data-ttu-id="29fec-111">DbProviderFactory の登録</span><span class="sxs-lookup"><span data-stu-id="29fec-111">Registering DbProviderFactories</span></span>  
 <span data-ttu-id="29fec-112">ファクトリ ベースのクラスをサポートする各 .NET Framework データ プロバイダーは、ローカル コンピューターの **machine.config** ファイルの **DbProviderFactories** セクションに構成情報を登録します。</span><span class="sxs-lookup"><span data-stu-id="29fec-112">Each .NET Framework data provider that supports a factory-based class registers configuration information in the **DbProviderFactories** section of the **machine.config** file on the local computer.</span></span> <span data-ttu-id="29fec-113">次の構成ファイル フラグメントは、<xref:System.Data.SqlClient> の構文と形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="29fec-113">The following configuration file fragment shows the syntax and format for <xref:System.Data.SqlClient>.</span></span>  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"
     description=".Net Framework Data Provider for SqlServer"
     type="System.Data.SqlClient.SqlClientFactory, System.Data,
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 <span data-ttu-id="29fec-114">基になるデータ プロバイダーは **invariant** 属性によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="29fec-114">The **invariant** attribute identifies the underlying data provider.</span></span> <span data-ttu-id="29fec-115">この 3 つの部分から成る命名構文は、新しいファクトリを作成するときのほか、プロバイダー名とそれに関連付けられた接続文字列を実行時に取得できるようにするために、アプリケーションの構成ファイルでプロバイダーを指定するときにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="29fec-115">This three-part naming syntax is also used when creating a new factory and for identifying the provider in an application configuration file so that the provider name, along with its associated connection string, can be retrieved at run time.</span></span>  
  
## <a name="retrieving-provider-information"></a><span data-ttu-id="29fec-116">プロバイダー情報の取得</span><span class="sxs-lookup"><span data-stu-id="29fec-116">Retrieving Provider Information</span></span>  
 <span data-ttu-id="29fec-117"><xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> メソッドを使用すると、ローカル コンピューターにインストールされているすべてのデータ プロバイダーに関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="29fec-117">You can retrieve information about all of the data providers installed on the local computer by using the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method.</span></span> <span data-ttu-id="29fec-118">このメソッドでは、**DbProviderFactories** という名前の <xref:System.Data.DataTable> が返されます。このテーブルに含まれる列を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="29fec-118">It returns a <xref:System.Data.DataTable> named **DbProviderFactories** that contains the columns described in the following table.</span></span>  
  
|<span data-ttu-id="29fec-119">列の序数</span><span class="sxs-lookup"><span data-stu-id="29fec-119">Column ordinal</span></span>|<span data-ttu-id="29fec-120">列名</span><span class="sxs-lookup"><span data-stu-id="29fec-120">Column name</span></span>|<span data-ttu-id="29fec-121">サンプルの出力</span><span class="sxs-lookup"><span data-stu-id="29fec-121">Example output</span></span>|<span data-ttu-id="29fec-122">説明</span><span class="sxs-lookup"><span data-stu-id="29fec-122">Description</span></span>|  
|--------------------|-----------------|--------------------|-----------------|  
|<span data-ttu-id="29fec-123">0</span><span class="sxs-lookup"><span data-stu-id="29fec-123">0</span></span>|<span data-ttu-id="29fec-124">**Name**</span><span class="sxs-lookup"><span data-stu-id="29fec-124">**Name**</span></span>|<span data-ttu-id="29fec-125">SqlClient Data Provider</span><span class="sxs-lookup"><span data-stu-id="29fec-125">SqlClient Data Provider</span></span>|<span data-ttu-id="29fec-126">データ プロバイダーの読み取り可能な名前</span><span class="sxs-lookup"><span data-stu-id="29fec-126">Readable name for the data provider</span></span>|  
|<span data-ttu-id="29fec-127">1</span><span class="sxs-lookup"><span data-stu-id="29fec-127">1</span></span>|<span data-ttu-id="29fec-128">**説明**</span><span class="sxs-lookup"><span data-stu-id="29fec-128">**Description**</span></span>|<span data-ttu-id="29fec-129">.Net Framework Data Provider for SqlServer</span><span class="sxs-lookup"><span data-stu-id="29fec-129">.Net Framework Data Provider for SqlServer</span></span>|<span data-ttu-id="29fec-130">データ プロバイダーの読み取り可能な説明</span><span class="sxs-lookup"><span data-stu-id="29fec-130">Readable description of the data provider</span></span>|  
|<span data-ttu-id="29fec-131">2</span><span class="sxs-lookup"><span data-stu-id="29fec-131">2</span></span>|<span data-ttu-id="29fec-132">**InvariantName**</span><span class="sxs-lookup"><span data-stu-id="29fec-132">**InvariantName**</span></span>|<span data-ttu-id="29fec-133">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="29fec-133">System.Data.SqlClient</span></span>|<span data-ttu-id="29fec-134">プログラムでデータ プロバイダーの参照に使用できる名前</span><span class="sxs-lookup"><span data-stu-id="29fec-134">Name that can be used programmatically to refer to the data provider</span></span>|  
|<span data-ttu-id="29fec-135">3</span><span class="sxs-lookup"><span data-stu-id="29fec-135">3</span></span>|<span data-ttu-id="29fec-136">**AssemblyQualifiedName**</span><span class="sxs-lookup"><span data-stu-id="29fec-136">**AssemblyQualifiedName**</span></span>|<span data-ttu-id="29fec-137">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="29fec-137">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span></span>|<span data-ttu-id="29fec-138">オブジェクトをインスタンス化するための十分な情報を保持している、ファクトリ クラスの完全修飾名</span><span class="sxs-lookup"><span data-stu-id="29fec-138">Fully qualified name of the factory class, which contains enough information to instantiate the object</span></span>|  
  
 <span data-ttu-id="29fec-139">この `DataTable` を使用して、ユーザーに実行時に <xref:System.Data.DataRow> を選択してもらうことができます。</span><span class="sxs-lookup"><span data-stu-id="29fec-139">This `DataTable` can be used to enable a user to select a <xref:System.Data.DataRow> at run time.</span></span> <span data-ttu-id="29fec-140">次に、選択された `DataRow` を <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> メソッドに渡すことで、厳密に型指定された <xref:System.Data.Common.DbProviderFactory> を作成できます。</span><span class="sxs-lookup"><span data-stu-id="29fec-140">The selected `DataRow` can then be passed to the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method to create a strongly typed <xref:System.Data.Common.DbProviderFactory>.</span></span> <span data-ttu-id="29fec-141">選択された <xref:System.Data.DataRow> を `GetFactory` メソッドに渡すことによって、目的の `DbProviderFactory` オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="29fec-141">A selected <xref:System.Data.DataRow> can be passed to the `GetFactory` method to create the desired `DbProviderFactory` object.</span></span>  
  
## <a name="listing-the-installed-provider-factory-classes"></a><span data-ttu-id="29fec-142">インストールされているプロバイダー ファクトリ クラスの一覧表示</span><span class="sxs-lookup"><span data-stu-id="29fec-142">Listing the Installed Provider Factory Classes</span></span>  
 <span data-ttu-id="29fec-143">次の例では、インストールされているプロバイダーの情報を含んだ <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> を、<xref:System.Data.DataTable> メソッドを使用して取得します。</span><span class="sxs-lookup"><span data-stu-id="29fec-143">This example demonstrates how to use the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method to return a <xref:System.Data.DataTable> containing information about the installed providers.</span></span> <span data-ttu-id="29fec-144">このコードは、`DataTable` 内の各行を反復処理しながら、インストールされている各プロバイダーの情報をコンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="29fec-144">The code iterates through each row in the `DataTable`, displaying information for each installed provider in the console window.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a><span data-ttu-id="29fec-145">アプリケーション構成ファイルを使用したファクトリ情報の保存</span><span class="sxs-lookup"><span data-stu-id="29fec-145">Using Application Configuration Files to Store Factory Information</span></span>  
 <span data-ttu-id="29fec-146">ファクトリを使用したデザイン パターンでは、プロバイダーや接続文字列の情報をアプリケーション構成ファイルに保存する必要があります。たとえば、Windows アプリケーションの場合は **app.config** に、ASP.NET アプリケーションの場合は **web.config** に、これらの情報を保存することになります。</span><span class="sxs-lookup"><span data-stu-id="29fec-146">The design pattern used for working with factories entails storing provider and connection string information in an application configuration file, such as **app.config** for a Windows application, and **web.config** for an ASP.NET application.</span></span>  
  
 <span data-ttu-id="29fec-147">次の構成ファイル フラグメントは、2 つの名前付き接続文字列 (SQL Server の Northwind データベースに接続するための "NorthwindSQL" と、Access/Jet の Northwind データベースに接続するための "NorthwindAccess") を保存する例を示したものです。</span><span class="sxs-lookup"><span data-stu-id="29fec-147">The following configuration file fragment demonstrates how to save two named connection strings, "NorthwindSQL" for a connection to the Northwind database in SQL Server, and "NorthwindAccess" for a connection to the Northwind database in Access/Jet.</span></span> <span data-ttu-id="29fec-148">**providerName** 属性には **invariant** の名前が使用されています。</span><span class="sxs-lookup"><span data-stu-id="29fec-148">The **invariant** name is used for the **providerName** attribute.</span></span>  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"
     providerName="System.Data.SqlClient"
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"
     providerName="System.Data.OleDb"
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a><span data-ttu-id="29fec-149">プロバイダー名による接続文字列の取得</span><span class="sxs-lookup"><span data-stu-id="29fec-149">Retrieving a Connection String by Provider Name</span></span>  
 <span data-ttu-id="29fec-150">プロバイダー ファクトリを作成するには、プロバイダー名だけでなく接続文字列も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29fec-150">In order to create a provider factory, you must supply a connection string as well as the provider name.</span></span> <span data-ttu-id="29fec-151">次の例では、プロバイダー名を "*System.Data.ProviderName*" という不変名で渡すことによってアプリケーション構成ファイルから接続文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="29fec-151">This example demonstrates how to retrieve a connection string from an application configuration file by passing the provider name in the invariant format "*System.Data.ProviderName*".</span></span> <span data-ttu-id="29fec-152">このコードでは、<xref:System.Configuration.ConnectionStringSettingsCollection> を反復処理しています。</span><span class="sxs-lookup"><span data-stu-id="29fec-152">The code iterates through the <xref:System.Configuration.ConnectionStringSettingsCollection>.</span></span> <span data-ttu-id="29fec-153">成功した場合には <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> が、それ以外の場合は `null` (Visual Basic の場合は `Nothing`) が返されます。</span><span class="sxs-lookup"><span data-stu-id="29fec-153">It returns the <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> on success; otherwise `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="29fec-154">プロバイダーに複数のエントリが存在した場合は、最初に見つかったエントリが返されます。</span><span class="sxs-lookup"><span data-stu-id="29fec-154">If there are multiple entries for a provider, the first one found is returned.</span></span> <span data-ttu-id="29fec-155">構成ファイルからの接続文字列の取得およびその例については、「[接続文字列と構成ファイル](connection-strings-and-configuration-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29fec-155">For more information and examples of retrieving connection strings from configuration files, see [Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29fec-156">このコードを実行するには、`System.Configuration.dll` を参照設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29fec-156">A reference to `System.Configuration.dll` is required in order for the code to run.</span></span>  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a><span data-ttu-id="29fec-157">DbProviderFactory および DbConnection の作成</span><span class="sxs-lookup"><span data-stu-id="29fec-157">Creating the DbProviderFactory and DbConnection</span></span>  
 <span data-ttu-id="29fec-158">次の例では、"*System.Data.ProviderName*" 形式のプロバイダー名と接続文字列を引数として渡すことによって、<xref:System.Data.Common.DbProviderFactory> および <xref:System.Data.Common.DbConnection> オブジェクトを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="29fec-158">This example demonstrates how to create a <xref:System.Data.Common.DbProviderFactory> and <xref:System.Data.Common.DbConnection> object by passing it the provider name in the format "*System.Data.ProviderName*" and a connection string.</span></span> <span data-ttu-id="29fec-159">成功した場合には `DbConnection` オブジェクトが返されます。エラーが発生した場合は `null` (Visual Basic の場合は `Nothing`) が返されます。</span><span class="sxs-lookup"><span data-stu-id="29fec-159">A `DbConnection` object is returned on success; `null` (`Nothing` in Visual Basic) on any error.</span></span>  
  
 <span data-ttu-id="29fec-160">このコードでは、`DbProviderFactory` を呼び出すことによって <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> を取得しています。</span><span class="sxs-lookup"><span data-stu-id="29fec-160">The code obtains the `DbProviderFactory` by calling <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span></span> <span data-ttu-id="29fec-161">次に、<xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> メソッドで <xref:System.Data.Common.DbConnection> オブジェクトを作成し、<xref:System.Data.Common.DbConnection.ConnectionString%2A> プロパティに接続文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="29fec-161">Then the <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> method creates the <xref:System.Data.Common.DbConnection> object and the <xref:System.Data.Common.DbConnection.ConnectionString%2A> property is set to the connection string.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="29fec-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="29fec-162">See also</span></span>

- [<span data-ttu-id="29fec-163">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="29fec-163">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="29fec-164">接続文字列</span><span class="sxs-lookup"><span data-stu-id="29fec-164">Connection Strings</span></span>](connection-strings.md)
- <span data-ttu-id="29fec-165">[構成クラスの使用](/previous-versions/aspnet/ms228063(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="29fec-165">[Using the Configuration Classes](/previous-versions/aspnet/ms228063(v=vs.100))</span></span>
- [<span data-ttu-id="29fec-166">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="29fec-166">ADO.NET Overview</span></span>](ado-net-overview.md)
