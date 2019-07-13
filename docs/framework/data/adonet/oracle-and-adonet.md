---
title: Oracle および ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 012a5b55d052f5f06da5c152da79f4676b2bff4e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877947"
---
# <a name="oracle-and-adonet"></a>Oracle および ADO.NET
> [!NOTE]
>  <xref:System.Data.OracleClient> の型は非推奨とされました。 これらの型は、.NET Framework の現在のバージョンでは引き続きサポートされていますが、今後のリリースでは削除される予定です。 サードパーティの Oracle プロバイダーを使用することをお勧めします。  
  
 このセクションでは、.NET Framework Data Provider for Oracle に固有の機能および動作について説明します。  
  
 .NET Framework Data Provider for Oracle では、Oracle クライアント ソフトウェアによって提供される Oracle Call Interface (OCI) を使用して Oracle データベースへのアクセスを提供します。 データ プロバイダーの機能は、SQL Server、OLE DB および ODBC 用の .NET Framework データ プロバイダーのように設計されています。  
  
 .NET Framework Data Provider for Oracle を使用するアプリケーションを参照する必要があります、<xref:System.Data.OracleClient>次のように名前空間。  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 コードをコンパイルするには、DLL への参照も必要です。 たとえば、C# プログラムをコンパイルする場合、コマンド ラインに以下のコードを含める必要があります。  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
 [システム要件](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Oracle の場合、.NET Framework Data Provider を使用するための要件について説明し、さまざまなことを使用する場合は、注意すべき問題について説明します。  
  
 [Oracle BFILE](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <xref:System.Data.OracleClient.OracleBFile> クラスについて説明します。このクラスは、Oracle BFILE データ型を操作するために使用されます。  
  
 [Oracle LOB](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <xref:System.Data.OracleClient.OracleLob> クラスについて説明します。このクラスは、Oracle LOB データ型を操作するために使用されます。  
  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 Oracle REF CURSOR データ型のサポートについて説明します。  
  
 [OracleTypes](../../../../docs/framework/data/adonet/oracletypes.md)  
 <xref:System.Data.OracleClient.OracleNumber> や <xref:System.Data.OracleClient.OracleString> など、Oracle データ型を操作するために使用する構造体について説明します。  
  
 [Oracle シーケンス](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 サーバーによって生成されたキー値 (Oracle シーケンス) を取得するためのサポートについて説明します。  
  
 [Oracle データ型のマッピング](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Oracle データ型およびその <xref:System.Data.OracleClient.OracleDataReader> へのマップを一覧表示します。  
  
 [Oracle 分散トランザクション](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <xref:System.Data.OracleClient.OracleConnection> オブジェクトが、トランザクションがアクティブであると判断した場合に、既存の分散トランザクションに自動的に参加する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 ADO.NET を使用する場合の安全なコーディング方法について説明します。  
  
 [DataSet、DataTable、および DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 `DataSets`、型指定された `DataSets`、`DataTables`、および `DataViews` の作成方法と使用方法について説明します。  
  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 ADO.NET でのデータの操作方法について説明します。  
  
 [SQL Server と ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 SQL Server 固有の機能の使用方法について説明します。  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 ADO.NET でプロバイダーに依存しないコードを記述するための Generic クラスについて説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
