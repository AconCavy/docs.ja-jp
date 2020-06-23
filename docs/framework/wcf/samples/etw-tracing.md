---
title: ETW トレース
description: このサンプルでは、Windows イベントトレーシング (ETW) と ETWTraceListener を使用して、エンドツーエンド (E2E) のトレースを実装する方法を示します。
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 210186285ed749a5d1567becd6738939b0bd9d03
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244427"
---
# <a name="etw-tracing"></a><span data-ttu-id="eafec-103">ETW トレース</span><span class="sxs-lookup"><span data-stu-id="eafec-103">ETW Tracing</span></span>
<span data-ttu-id="eafec-104">このサンプルでは、Event Tracing for Windows (ETW) と、このサンプルに用意されている `ETWTraceListener` を使用して、エンドツーエンド (E2E) のトレースを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eafec-104">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="eafec-105">このサンプルは[はじめに](getting-started-sample.md)に基づいており、ETW トレースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="eafec-105">The sample is based on the [Getting Started](getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eafec-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafec-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="eafec-107">このサンプルでは、[トレースとメッセージログ](tracing-and-message-logging.md)について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="eafec-107">This sample assumes that you are familiar with [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="eafec-108"><xref:System.Diagnostics> トレース モデル内の各トレース ソースでは、データのトレース場所とトレース方法を決定するトレース リスナーを複数設定できます。</span><span class="sxs-lookup"><span data-stu-id="eafec-108">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="eafec-109">リスナの種類では、トレース データの記録形式が定義されます。</span><span class="sxs-lookup"><span data-stu-id="eafec-109">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="eafec-110">リスナを構成に追加する方法を、次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="eafec-110">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="eafec-111">このリスナを使用する前に、ETW トレース セッションを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eafec-111">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="eafec-112">このセッションは、Logman.exe または Tracelog.exe を使用して開始できます。</span><span class="sxs-lookup"><span data-stu-id="eafec-112">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="eafec-113">このサンプルには、ETW トレース セッションをセットアップするための SetupETW.bat ファイルと、セッションを閉じてログ ファイルを完了するための CleanupETW.bat ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="eafec-113">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eafec-114">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eafec-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="eafec-115">これらのツールの詳細については、「」を参照してください。<https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="eafec-115">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="eafec-116">ETWTraceListener を使用する場合、トレースはバイナリの .etl ファイルにログ記録されます。</span><span class="sxs-lookup"><span data-stu-id="eafec-116">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="eafec-117">ServiceModel トレースが有効な場合、生成されるすべてのトレースは同じファイルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="eafec-117">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="eafec-118">.Etl と .svclog のログファイルを表示するには、[サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="eafec-118">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="eafec-119">このビューアでは、メッセージを送信側から受信側や使用地点までトレースできる、システムのエンドツーエンドのビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="eafec-119">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="eafec-120">ETW トレース リスナは、循環ログをサポートします。</span><span class="sxs-lookup"><span data-stu-id="eafec-120">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="eafec-121">この機能を有効にするには、[**スタート**]、[**実行**] の各ページにアクセスして、 `cmd` コマンドコンソールを起動します。</span><span class="sxs-lookup"><span data-stu-id="eafec-121">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="eafec-122">次のコマンドでは、`<logfilename>` パラメータを使用するログ ファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="eafec-122">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="eafec-123">`-f` スイッチと `-max` スイッチは省略できます。</span><span class="sxs-lookup"><span data-stu-id="eafec-123">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="eafec-124">これらのスイッチでは、それぞれバイナリの循環形式と 1000 MB の最大ログ サイズが指定されます。</span><span class="sxs-lookup"><span data-stu-id="eafec-124">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="eafec-125">`-p` スイッチは、トレース プロバイダーを指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="eafec-125">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="eafec-126">この例では、`"{411a0819-c24b-428c-83e2-26b41091702e}"` は "XML ETW サンプル プロバイダー" の GUID です。</span><span class="sxs-lookup"><span data-stu-id="eafec-126">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="eafec-127">セッションを開始するには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="eafec-127">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="eafec-128">ログ記録を完了したら、次のコマンドを使用してセッションを停止できます。</span><span class="sxs-lookup"><span data-stu-id="eafec-128">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="eafec-129">このプロセスでは、[サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)や Tracerpt など、選択したツールで処理できるバイナリ循環ログが生成されます。</span><span class="sxs-lookup"><span data-stu-id="eafec-129">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="eafec-130">循環[トレース](circular-tracing.md)のサンプルを参照して、循環ログを実行する代替リスナーの詳細情報を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="eafec-130">You can also review the [Circular Tracing](circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eafec-131">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="eafec-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="eafec-132">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="eafec-132">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="eafec-133">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="eafec-133">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="eafec-134">RegisterProvider.bat、SetupETW.bat、および CleanupETW.bat コマンドを使用するには、ローカル管理者アカウントで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eafec-134">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="eafec-135">Windows Vista 以降を使用している場合は、管理者特権でコマンドプロンプトを実行する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="eafec-135">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="eafec-136">これを行うには、コマンドプロンプトのアイコンを右クリックし、[**管理者として実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eafec-136">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="eafec-137">サンプルを実行する前に、クライアントとサーバーで RegisterProvider.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="eafec-137">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="eafec-138">この結果、トレースを生成する ETWTracingSampleLog.etl ファイルがセットアップされます。このトレースはサービス トレース ビューアで読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="eafec-138">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="eafec-139">このファイルは、C:\logs フォルダにあります。</span><span class="sxs-lookup"><span data-stu-id="eafec-139">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="eafec-140">このフォルダーが存在しない場合はフォルダーを作成する必要があります。作成しない場合、トレースは生成されません。</span><span class="sxs-lookup"><span data-stu-id="eafec-140">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="eafec-141">次に、クライアント コンピューターとサーバー コンピューターで SetupETW.bat を実行し、ETW トレース セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="eafec-141">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="eafec-142">SetupETW.bat ファイルは、CS\Client フォルダーの下にあります。</span><span class="sxs-lookup"><span data-stu-id="eafec-142">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="eafec-143">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="eafec-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="eafec-144">サンプルの使用が終わったら、CleanupETW.bat を実行して ETWTracingSampleLog.etl ファイルの作成を完了します。</span><span class="sxs-lookup"><span data-stu-id="eafec-144">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="eafec-145">サービス トレース ビューア内で ETWTracingSampleLog.etl ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="eafec-145">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="eafec-146">このバイナリ形式のファイルを .svclog ファイルとして保存するかどうかを尋ねるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eafec-146">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="eafec-147">新しく作成された .svclog ファイルをサービス トレース ビューアー内で開き、ETW トレースと ServiceModel トレースを表示します。</span><span class="sxs-lookup"><span data-stu-id="eafec-147">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eafec-148">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="eafec-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="eafec-149">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="eafec-149">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="eafec-150">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="eafec-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eafec-151">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="eafec-151">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="eafec-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="eafec-152">See also</span></span>

- <span data-ttu-id="eafec-153">[AppFabric の監視のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="eafec-153">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
