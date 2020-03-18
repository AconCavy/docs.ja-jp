---
title: アプリケーション ログの使用
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 617b940d2cf15779ae3c10e4663b63c9771d44b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345897"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="3dba4-102">Visual Basic でのアプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="3dba4-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="3dba4-103">`My.Application.Log` オブジェクトと `My.Log` オブジェクトを使用すると、ログおよびトレース情報をログに簡単に書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="3dba4-104">メッセージをログに記録する方法</span><span class="sxs-lookup"><span data-stu-id="3dba4-104">How Messages are Logged</span></span>

<span data-ttu-id="3dba4-105">最初に、ログの <xref:System.Diagnostics.TraceSource.Switch%2A> プロパティの <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> プロパティを使用してメッセージの重大度がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="3dba4-106">既定では、重大度が "情報" 以上のメッセージのみ、ログの `TraceListener` コレクションで指定されたトレース リスナーに渡されます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="3dba4-107">次に各リスナーは、メッセージの重大度をリスナーの <xref:System.Diagnostics.TraceSource.Switch%2A> プロパティと比較します。</span><span class="sxs-lookup"><span data-stu-id="3dba4-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="3dba4-108">メッセージの重大度が十分に高い場合に、リスナーはメッセージを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="3dba4-109">次の図は、 `WriteEntry` メソッドに書き込まれたメッセージが、ログのトレース リスナーの `WriteLine` メソッドにどのように渡されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="3dba4-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![My ログの呼び出しを示す図。](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="3dba4-111">アプリケーションの構成ファイルを変更すると、ログおよびトレース リスナーの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="3dba4-112">次の図は、ログと構成ファイルの各部分の対応を示します。</span><span class="sxs-lookup"><span data-stu-id="3dba4-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![My ログの構成を示す図。](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="3dba4-114">メッセージがログに記録される場所</span><span class="sxs-lookup"><span data-stu-id="3dba4-114">Where Messages are Logged</span></span>

<span data-ttu-id="3dba4-115">アセンブリに構成ファイルがない場合、 `My.Application.Log` オブジェクトと `My.Log` オブジェクトは <xref:System.Diagnostics.DefaultTraceListener> クラスを介してアプリケーションのデバッグ出力への書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="3dba4-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="3dba4-116">また、`My.Application.Log` オブジェクトは <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> クラスを介してアセンブリのログ ファイルへの書き込みを行い、`My.Log` オブジェクトは、<xref:System.Web.WebPageTraceListener> クラスを介して ASP.NET Web ページの出力への書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="3dba4-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="3dba4-117">デバッグ出力は、アプリケーションをデバッグ モードで実行中のときに Visual Studio **[出力]** ウィンドウで参照できます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="3dba4-118">**[出力]** ウィンドウを開くには、 **[デバッグ]** メニュー項目をクリックし、 **[ウィンドウ]** をポイントして、 **[出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dba4-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="3dba4-119">**[出力]** ウィンドウで **[出力元の表示]** ボックスの **[デバッグ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dba4-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="3dba4-120">既定では、 `My.Application.Log` がログ ファイルを書き込む先は、ユーザーのアプリケーション データ用のパスです。</span><span class="sxs-lookup"><span data-stu-id="3dba4-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="3dba4-121">このパスは、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> オブジェクトの <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> プロパティから取得できます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="3dba4-122">このパスの形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3dba4-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="3dba4-123">`BasePath` の一般的な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3dba4-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="3dba4-124">C:\Documents and Settings\\`username`\Application Data</span><span class="sxs-lookup"><span data-stu-id="3dba4-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="3dba4-125">`CompanyName`、 `ProductName`、 `ProductVersion` の値は、アプリケーションのアセンブリ情報から取得されます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="3dba4-126">ログ ファイル名の形式は *AssemblyName*.log です。 *AssemblyName* は、アセンブリのファイル名から拡張子を取り除いたものです。</span><span class="sxs-lookup"><span data-stu-id="3dba4-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="3dba4-127">複数のログ ファイルが必要な場合 (たとえば、アプリケーションがログに書き込もうとしているときで、元のログが利用できない場合) には、ログ ファイル名の形式は *AssemblyName*-*iteration*.log です。 `iteration` は正の `Integer`をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dba4-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="3dba4-128">コンピューターおよびアプリケーションの構成ファイルを追加または変更すると、既定の動作をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="3dba4-129">詳細については、「[チュートリアル:My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dba4-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="3dba4-130">ログ設定を構成する</span><span class="sxs-lookup"><span data-stu-id="3dba4-130">Configuring Log Settings</span></span>

<span data-ttu-id="3dba4-131">`Log` オブジェクトの既定の実装では、アプリケーション構成ファイル app.config がなくても動作するようになっています。既定の動作を変更するには、新しい設定を記述した構成ファイルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba4-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="3dba4-132">詳細については、「[チュートリアル:My.Application.Log の出力をフィルター処理する](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dba4-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="3dba4-133">app.config ファイルでは、ログの構成セクションは、メインの `<system.diagnostics>` ノードの `<configuration>` ノードにあります。</span><span class="sxs-lookup"><span data-stu-id="3dba4-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="3dba4-134">ログ情報は、以下のノードに定義されています。</span><span class="sxs-lookup"><span data-stu-id="3dba4-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="3dba4-135">`Log` オブジェクトのリスナーは、DefaultSource という名前の `<sources>` ノードで定義されています。</span><span class="sxs-lookup"><span data-stu-id="3dba4-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="3dba4-136">`Log` オブジェクトの重大度フィルターは、DefaultSwitch という名前の `<switches>` ノードで定義されています。</span><span class="sxs-lookup"><span data-stu-id="3dba4-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="3dba4-137">ログ リスナーは `<sharedListeners>` ノードで定義されています。</span><span class="sxs-lookup"><span data-stu-id="3dba4-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="3dba4-138">次のコードに、 `<sources>`、 `<switches>`、 `<sharedListeners>` の各ノードの例を示します。</span><span class="sxs-lookup"><span data-stu-id="3dba4-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="DefaultSource" switchName="DefaultSwitch">
        <listeners>
          <add name="FileLog"/>
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="DefaultSwitch" value="Information" />
    </switches>
    <sharedListeners>
      <add name="FileLog"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"
        initializeData="FileLogWriter"
      />
    </sharedListeners>
  </system.diagnostics>
</configuration>
```

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="3dba4-139">配置後のログ設定の変更</span><span class="sxs-lookup"><span data-stu-id="3dba4-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="3dba4-140">アプリケーションを開発すると、その構成の設定は、上記の例のように、app.config ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="3dba4-141">アプリケーションを配置した後でも、構成ファイルを編集することで、ログを構成できます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="3dba4-142">Windows ベースのアプリケーションでは、このファイルの名前は *applicationName*.exe.config で、実行可能ファイルと同じフォルダーに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba4-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="3dba4-143">Web アプリケーションでは、これは、プロジェクトに関連付けられた Web.config ファイルです。</span><span class="sxs-lookup"><span data-stu-id="3dba4-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="3dba4-144">アプリケーションは、クラスのインスタンスを作成するコードを初めて実行するときに、そのオブジェクトについての情報を構成ファイルでチェックします。</span><span class="sxs-lookup"><span data-stu-id="3dba4-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="3dba4-145">`Log` オブジェクトの場合は、 `Log` オブジェクトに初めてアクセスするときにそれを行います。</span><span class="sxs-lookup"><span data-stu-id="3dba4-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="3dba4-146">各オブジェクトについて、システムが構成ファイルをチェックするのは、アプリケーションがそのオブジェクトを最初に作成するときの 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="3dba4-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="3dba4-147">したがって、変更を有効にするためには、アプリケーションの再起動が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3dba4-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="3dba4-148">配置されたアプリケーションでは、アプリケーションの起動前にスイッチ オブジェクトを再設定することで、トレース コードを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="3dba4-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="3dba4-149">通常この作業では、スイッチ オブジェクトのオンとオフを切り替えるか、またはトレース レベルを変更し、その後アプリケーションを再起動します。</span><span class="sxs-lookup"><span data-stu-id="3dba4-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="3dba4-150">セキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="3dba4-150">Security Considerations</span></span>

<span data-ttu-id="3dba4-151">ログにデータを書き込むときには、次の点を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba4-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="3dba4-152">**ユーザー情報を漏らさないようにします。**</span><span class="sxs-lookup"><span data-stu-id="3dba4-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="3dba4-153">アプリケーションでは、認められた情報のみをログに書き込むようにします。</span><span class="sxs-lookup"><span data-stu-id="3dba4-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="3dba4-154">たとえば、アプリケーション ログにユーザー名を書き込んでも問題ないとしても、ユーザーのパスワードを書き込むのは問題です。</span><span class="sxs-lookup"><span data-stu-id="3dba4-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="3dba4-155">**ログは安全な場所に配置します。**</span><span class="sxs-lookup"><span data-stu-id="3dba4-155">**Make log locations secure.**</span></span> <span data-ttu-id="3dba4-156">機密性の高い情報を含む可能性のあるログは、安全な場所に格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba4-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="3dba4-157">**不正な情報は避けます。**</span><span class="sxs-lookup"><span data-stu-id="3dba4-157">**Avoid misleading information.**</span></span> <span data-ttu-id="3dba4-158">一般にアプリケーションでは、ユーザーが入力したデータは、使用する前にすべて検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba4-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="3dba4-159">これは、アプリケーション ログにデータを書き込むときも同じです。</span><span class="sxs-lookup"><span data-stu-id="3dba4-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="3dba4-160">**サービス拒否を避けます。**</span><span class="sxs-lookup"><span data-stu-id="3dba4-160">**Avoid denial of service.**</span></span> <span data-ttu-id="3dba4-161">アプリケーションがログに書き込む情報が多すぎると、ログが満杯になったり、重要な情報を見つけにくくなったりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3dba4-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="3dba4-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dba4-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="3dba4-163">アプリケーションからの情報のログ記録</span><span class="sxs-lookup"><span data-stu-id="3dba4-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
