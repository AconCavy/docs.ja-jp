---
title: ETW トレース
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 0bdbf6699a0cfa3dce58abda4c989fb25d764459
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600564"
---
# <a name="etw-tracing"></a><span data-ttu-id="71d27-102">ETW トレース</span><span class="sxs-lookup"><span data-stu-id="71d27-102">ETW Tracing</span></span>
<span data-ttu-id="71d27-103">このサンプルでは、Event Tracing for Windows (ETW) と、このサンプルに用意されている `ETWTraceListener` を使用して、エンドツーエンド (E2E) のトレースを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="71d27-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="71d27-104">このサンプルは[はじめに](getting-started-sample.md)に基づいており、ETW トレースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="71d27-104">The sample is based on the [Getting Started](getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71d27-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71d27-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="71d27-106">このサンプルでは、[トレースとメッセージログ](tracing-and-message-logging.md)について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="71d27-106">This sample assumes that you are familiar with [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="71d27-107"><xref:System.Diagnostics> トレース モデル内の各トレース ソースでは、データのトレース場所とトレース方法を決定するトレース リスナーを複数設定できます。</span><span class="sxs-lookup"><span data-stu-id="71d27-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="71d27-108">リスナの種類では、トレース データの記録形式が定義されます。</span><span class="sxs-lookup"><span data-stu-id="71d27-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="71d27-109">リスナを構成に追加する方法を、次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="71d27-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="71d27-110">このリスナを使用する前に、ETW トレース セッションを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71d27-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="71d27-111">このセッションは、Logman.exe または Tracelog.exe を使用して開始できます。</span><span class="sxs-lookup"><span data-stu-id="71d27-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="71d27-112">このサンプルには、ETW トレース セッションをセットアップするための SetupETW.bat ファイルと、セッションを閉じてログ ファイルを完了するための CleanupETW.bat ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="71d27-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71d27-113">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71d27-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="71d27-114">これらのツールの詳細については、「」を参照してください。<https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="71d27-114">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="71d27-115">ETWTraceListener を使用する場合、トレースはバイナリの .etl ファイルにログ記録されます。</span><span class="sxs-lookup"><span data-stu-id="71d27-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="71d27-116">ServiceModel トレースが有効な場合、生成されるすべてのトレースは同じファイルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="71d27-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="71d27-117">.Etl と .svclog のログファイルを表示するには、[サービストレースビューアーツール (svctraceviewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="71d27-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="71d27-118">このビューアでは、メッセージを送信側から受信側や使用地点までトレースできる、システムのエンドツーエンドのビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="71d27-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="71d27-119">ETW トレース リスナは、循環ログをサポートします。</span><span class="sxs-lookup"><span data-stu-id="71d27-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="71d27-120">この機能を有効にするには、[**スタート**]、[**実行**] の各ページにアクセスして、 `cmd` コマンドコンソールを起動します。</span><span class="sxs-lookup"><span data-stu-id="71d27-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="71d27-121">次のコマンドでは、`<logfilename>` パラメータを使用するログ ファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="71d27-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="71d27-122">`-f` スイッチと `-max` スイッチは省略できます。</span><span class="sxs-lookup"><span data-stu-id="71d27-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="71d27-123">これらのスイッチでは、それぞれバイナリの循環形式と 1000 MB の最大ログ サイズが指定されます。</span><span class="sxs-lookup"><span data-stu-id="71d27-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="71d27-124">`-p` スイッチは、トレース プロバイダーを指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="71d27-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="71d27-125">この例では、`"{411a0819-c24b-428c-83e2-26b41091702e}"` は "XML ETW サンプル プロバイダー" の GUID です。</span><span class="sxs-lookup"><span data-stu-id="71d27-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="71d27-126">セッションを開始するには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="71d27-126">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="71d27-127">ログ記録を完了したら、次のコマンドを使用してセッションを停止できます。</span><span class="sxs-lookup"><span data-stu-id="71d27-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="71d27-128">このプロセスでは、[サービストレースビューアーツール (svctraceviewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)や Tracerpt など、選択したツールで処理できるバイナリ循環ログが生成されます。</span><span class="sxs-lookup"><span data-stu-id="71d27-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="71d27-129">循環[トレース](circular-tracing.md)のサンプルを参照して、循環ログを実行する代替リスナーの詳細情報を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="71d27-129">You can also review the [Circular Tracing](circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="71d27-130">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="71d27-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="71d27-131">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="71d27-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="71d27-132">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="71d27-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="71d27-133">RegisterProvider.bat、SetupETW.bat、および CleanupETW.bat コマンドを使用するには、ローカル管理者アカウントで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71d27-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="71d27-134">Windows Vista 以降を使用している場合は、管理者特権でコマンドプロンプトを実行する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="71d27-134">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="71d27-135">これを行うには、コマンドプロンプトのアイコンを右クリックし、[**管理者として実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71d27-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="71d27-136">サンプルを実行する前に、クライアントとサーバーで RegisterProvider.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="71d27-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="71d27-137">この結果、トレースを生成する ETWTracingSampleLog.etl ファイルがセットアップされます。このトレースはサービス トレース ビューアで読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="71d27-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="71d27-138">このファイルは、C:\logs フォルダにあります。</span><span class="sxs-lookup"><span data-stu-id="71d27-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="71d27-139">このフォルダーが存在しない場合はフォルダーを作成する必要があります。作成しない場合、トレースは生成されません。</span><span class="sxs-lookup"><span data-stu-id="71d27-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="71d27-140">次に、クライアント コンピューターとサーバー コンピューターで SetupETW.bat を実行し、ETW トレース セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="71d27-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="71d27-141">SetupETW.bat ファイルは、CS\Client フォルダーの下にあります。</span><span class="sxs-lookup"><span data-stu-id="71d27-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="71d27-142">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="71d27-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="71d27-143">サンプルの使用が終わったら、CleanupETW.bat を実行して ETWTracingSampleLog.etl ファイルの作成を完了します。</span><span class="sxs-lookup"><span data-stu-id="71d27-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="71d27-144">サービス トレース ビューア内で ETWTracingSampleLog.etl ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="71d27-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="71d27-145">このバイナリ形式のファイルを .svclog ファイルとして保存するかどうかを尋ねるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="71d27-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="71d27-146">新しく作成された .svclog ファイルをサービス トレース ビューアー内で開き、ETW トレースと ServiceModel トレースを表示します。</span><span class="sxs-lookup"><span data-stu-id="71d27-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="71d27-147">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="71d27-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="71d27-148">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="71d27-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="71d27-149">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="71d27-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="71d27-150">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="71d27-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="71d27-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="71d27-151">See also</span></span>

- <span data-ttu-id="71d27-152">[AppFabric の監視のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="71d27-152">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
