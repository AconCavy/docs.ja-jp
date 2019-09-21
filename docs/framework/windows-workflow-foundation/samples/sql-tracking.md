---
title: SQL 追跡
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 24cc484bf11d7cedab949d61c63f805a28a9f849
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038058"
---
# <a name="sql-tracking"></a>SQL 追跡
このサンプルでは、カスタム SQL 追跡参加要素を作成し、追跡レコードを SQL データベースに書き込む方法を示します。 Windows Workflow Foundation (WF) は、ワークフローインスタンスの実行の可視性を得るためのワークフロー追跡機能を提供します。 追跡ランタイムでは、ワークフローの実行中にワークフロー追跡レコードが出力されます。 ワークフロー追跡の詳細については、「[ワークフローの追跡とトレース](../workflow-tracking-and-tracing.md)」を参照してください。

#### <a name="to-use-this-sample"></a>このサンプルを使用するには

1. SQL Server 2008、SQL Server 2008 Express、またはそれ以降のバージョンがインストールされていることを確認します。 サンプルと共にパッケージ化されているスクリプトは、SQL Express インスタンスをローカル コンピューターで使用していることが前提になります。 別のインスタンスがある場合は、データベース関連のスクリプトを変更してからサンプルを実行してください。

2. Scripts ディレクトリ (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 内で Trackingsetup.cmd を実行して SQL Server 追跡データベースを作成します。 これによって、TrackingSample という名前のデータベースが作成されます。

    > [!NOTE]
    > このスクリプトでは、SQL Express の既定のインスタンスにデータベースが作成されます。 別のデータベース インスタンスにインストールする場合は、Trackingsetup.cmd スクリプトを編集してください。  
  
3. Visual Studio 2010 で SqlTrackingSample .sln を開きます。  
  
4. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
5. F5 キーを押してアプリケーションを実行します。  
  
     ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。  
  
6. ブラウザーで、StockPriceService.xamlx をクリックします。  
  
7. ブラウザーに、[StockPriceService] ページが表示され、ローカル サービスの WSDL アドレスが示されます。 このアドレスをコピーします。  
  
     ローカルサービスの WSDL アドレスの例は`http://localhost:65193/StockPriceService.xamlx?wsdl`、です。  
  
8. エクスプローラーを使用して、WCF テストクライアント (Wcftestclient.exe) を実行します。 このテスト クライアントは Microsoft Visual Studio 10.0\Common7\IDE ディレクトリにあります。  
  
9. WCF テストクライアントで、 **[ファイル]** メニューをクリックし、 **[サービスの追加]** を選択します。 テキスト ボックスにローカル サービスのアドレスを貼り付けます。 **[OK]** をクリックしてダイアログを閉じます。  
  
10. WCF テストクライアントで、 **[Getstockprice]** をダブルクリックします。 これにより`GetStockPrice` 、1つのパラメーターを受け取る操作が開き`Contoso` 、値を入力して、 **[呼び出し]** をクリックします。  
  
11. 出力された追跡レコードが SQL データベースに書き込まれます。 追跡レコードを表示するには、SQL Management Studio で TrackingSample データベースを開き、テーブルに移動します。 SQL Server Management Studio の詳細については、「 [SQL Server Management Studio の概要](https://go.microsoft.com/fwlink/?LinkId=165645)」を参照してください。 SQL Server 2008 Management Studio Express は[ここ](https://go.microsoft.com/fwlink/?LinkId=180520)からダウンロードできます。 テーブルで選択クエリを実行すると、それぞれのテーブルに格納されている追跡レコード内のデータが表示されます。  
  
#### <a name="to-uninstall-the-sample"></a>サンプルをアンインストールするには  
  
1. サンプル ディレクトリ (\WF\Basic\Tracking\SqlTracking) で Trackingcleanup.cmd スクリプトを実行します。  
  
    > [!NOTE]
    > Trackingcleanup.cmd は、ローカル コンピューターの SQL Express 内にあるデータベースを削除しようとします。 別の SQL Server インスタンスを使用している場合は、Trackingcleanup.cmd を編集します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://go.microsoft.com/fwlink/?LinkId=193959)
