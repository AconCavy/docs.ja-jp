---
title: サンプル データベースのダウンロード (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: 340ccd1e0e2d415fe60721775bd39acf9db00f85
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504503"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>サンプル データベースのダウンロード (LINQ to DataSet)
サンプルおよびチュートリアル、LINQ to DataSet のドキュメントでは、AdventureWorks サンプル データベースを使用します。 この製品は、Microsoft のダウンロード サイトから無償でダウンロードできます。 サンプルおよびチュートリアル、LINQ to DataSet のドキュメントでは、データ ストアとして SQL Server を使用します。 SQL Server の代わりに、無償で提供されている SQL Server Express Edition をデータ ストアとして使用することもできます。  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>AdventureWorks データベースのダウンロードとインストール  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>SQL Server の AdventureWorks サンプル データベースをダウンロードおよびインストールするには  
  
1. Internet Explorer を開きます。  
  
2. 移動して、 [SQL Server 2005 サンプルとサンプル データベース](https://go.microsoft.com/fwlink/?linkid=31046)Web サイト。  
  
3. 記載されている手順に従ってプロセッサの種類に応じた AdventureWorks サンプル データベース (AdventureWorksDB.msi など) をダウンロードし、.MSI ファイルをローカル コンピューターに保存します。  
  
4. 以前のバージョンの AdventureWorks は、単体でダウンロードしたか SQL Server のセットアップ時にインストールしたかに関係なく、AdventureWorks.msi の実行前に削除しておく必要があります。  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>単体でダウンロードした以前のバージョンの AdventureWorks サンプル データベースを削除するには  
  
1. AdventureWorks データベースまたは AdventureWorksDW データベースを削除します。  
  
2. **プログラム追加と削除**を選択します**AdventureWorksDB**または **[adventureworksbi]** クリック**削除**します。  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>過去にセットアップ プログラムを使用してインストールした AdventureWorks サンプル データベースを削除するには  
  
1. AdventureWorks データベースまたは AdventureWorksDW データベースを削除します。  
  
2. **プログラム追加と削除**を選択します**Microsoft SQL Server 2005**クリック**変更**します。  
  
3. **コンポーネントの選択**を選択します**ワークステーション コンポーネント**順にクリックします**次**します。  
  
4. **、SQL Server インストール ウィザードへようこそ**、 をクリックして**次**します。  
  
5. **システム構成チェック**、 をクリックして**次**します。  
  
6. **インスタンスの削除の変更または**、 をクリックして**インストール済みコンポーネントの変更**します。  
  
7. **機能の選択**、展開、**ドキュメント、サンプル、およびサンプル データベース**ノード。  
  
8. 選択**サンプル コードおよびアプリケーション**します。 展開**サンプル データベース**、削除して、選択するには、サンプル データベースを選択します。**全体の機能は使用できません**します。 **[次へ]** をクリックします。  
  
9. クリックして**インストール**インストール ウィザードを終了します。  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>AdventureWorks サンプル データベース ファイルを SQL Server のインスタンスにアタッチするには  
  
1. ファイルのサンプル データベースのインストーラー ファイルがダウンロードされたら、ダブルクリック、 **AdventureWorksDB.msi**ファイル (またはダウンロードしたファイル)、データベースをインストールします。 既定では、データベースは c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data にインストールされます。  
  
2. SQLCMD または SQL Server Management Studio で次のスクリプトを実行し、AdventureWorks データベース ファイルを SQL Server のインスタンスにアタッチします。  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     これらのファイルが異なるドライブまたはディレクトリにインストールされている場合は、パスを適宜修正してから、`sp_attach_db` ストアド プロシージャを実行してください。  
  
## <a name="downloading-sql-server-express-edition"></a>SQL Server Express Edition のダウンロード  
 サンプルおよびチュートリアル、LINQ to DataSet のセクションでは、データ ストアとして SQL Server 2005 を使用して、、代わりに SQL Server Express Edition を使用するように変更できます。 SQL Server Express Edition は無料で入手でき、アプリケーションと共に再配布できます。 Visual Studio を使用している場合は、Pro 以上のエディションの SQL Server Express Edition が含まれます。  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>SQL Server Express Edition をダウンロードおよびインストールするには  
  
1. Internet Explorer を開始します。  
  
2. 移動して、 [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070)ページをダウンロードします。  
  
3. Web サイトに記載されているインストールの指示に従います。  
  
## <a name="see-also"></a>関連項目

- [はじめに](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
