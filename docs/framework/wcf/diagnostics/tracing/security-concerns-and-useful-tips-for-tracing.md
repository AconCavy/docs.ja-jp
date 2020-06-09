---
title: トレースに関するセキュリティの考慮事項と役立つヒント
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 0a09e387a4f964441f11d07a84bd492345d5b691
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578878"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="f4df4-102">トレースに関するセキュリティの考慮事項と役立つヒント</span><span class="sxs-lookup"><span data-stu-id="f4df4-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="f4df4-103">ここでは、機密情報を漏洩の危険から守る方法と共に、WebHost を使用する場合の便利なヒントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4df4-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="f4df4-104">WebHost でのカスタム トレース リスナーの使用</span><span class="sxs-lookup"><span data-stu-id="f4df4-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="f4df4-105">独自のリスナーを作成している場合、WebHost サービスではトレースが失われる可能性があることを認識する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4df4-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="f4df4-106">WebHost をリサイクルすると、実行中のプロセスがシャットダウンされ、複製されたプロセスに引き継がれます。</span><span class="sxs-lookup"><span data-stu-id="f4df4-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="f4df4-107">この 2 つのプロセスは、しばらくの間、引き続き同じリソースにアクセスできる必要がありますが、これはリスナーの種類に依存します。</span><span class="sxs-lookup"><span data-stu-id="f4df4-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="f4df4-108">この場合、`XmlWriterTraceListener` は、2 番目のプロセスに対して新しいトレース ファイルを作成します。一方、Windows のイベント トレースは、同じセッションの複数のプロセスを管理して、同じファイルへのアクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="f4df4-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="f4df4-109">したがって、独自に作成したリスナーが同様の機能を提供しない場合、この 2 つのプロセスによってファイルがロックされたときにトレースが失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f4df4-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="f4df4-110">カスタム トレース リスナーがネットワーク上で (たとえば、リモート データベースに) トレースとメッセージを送信する場合があることを認識する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="f4df4-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="f4df4-111">アプリケーションを展開するユーザーは、適切なアクセス制御を提供するカスタム リスナーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4df4-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="f4df4-112">また、遠隔地で公開される可能性があるすべての個人情報にセキュリティ制御を適用する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="f4df4-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="f4df4-113">機密情報のログ記録</span><span class="sxs-lookup"><span data-stu-id="f4df4-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="f4df4-114">スコープ内のメッセージに含まれるメッセージ ヘッダーをトレースします。</span><span class="sxs-lookup"><span data-stu-id="f4df4-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="f4df4-115">トレースが有効になっていると、アプリケーション固有のヘッダー内にある個人情報 (クエリ文字列など)、および本文情報 (クレジット カード番号など) をログで確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f4df4-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="f4df4-116">アプリケーションを展開するユーザーは、構成ファイルとトレース ファイルに対するアクセス制御を実施する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4df4-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="f4df4-117">この種の情報を表示しないようにするには、トレースを無効にします。トレース ログを共有する場合は、表示しないデータをフィルターで除外します。</span><span class="sxs-lookup"><span data-stu-id="f4df4-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="f4df4-118">トレース ファイルの内容が意図せず公開されることを防ぐために、次のヒントに従ってください。</span><span class="sxs-lookup"><span data-stu-id="f4df4-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
- <span data-ttu-id="f4df4-119">WebHost および自己ホストの両方のシナリオにおいて、ログ ファイルがアクセス制御リスト (ACL) によって保護されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f4df4-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
- <span data-ttu-id="f4df4-120">Web 要求を使用して簡単に処理できないファイル拡張子を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4df4-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="f4df4-121">たとえば、.xml ファイルの拡張子を選ぶのは安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="f4df4-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="f4df4-122">IIS の管理ガイドを参照して、処理できる拡張子のリストを確認します。</span><span class="sxs-lookup"><span data-stu-id="f4df4-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
- <span data-ttu-id="f4df4-123">ログ ファイルのある場所への絶対パスを指定します。この場所は、部外者が Web ブラウザーを使用してアクセスできないように、WebHost の vroot パブリック ディレクトリの外にします。</span><span class="sxs-lookup"><span data-stu-id="f4df4-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="f4df4-124">既定では、キーおよびユーザー名やパスワードなどの個人を特定できる情報 (PII) は、トレースおよびログに記録するメッセージではありません。</span><span class="sxs-lookup"><span data-stu-id="f4df4-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="f4df4-125">しかし、コンピューターの管理者は、Machine.config ファイルの `enableLoggingKnownPII` 要素にある `machineSettings` 属性を使用して、コンピューター上で実行されているアプリケーションに対し、既知の PII (個人を特定できる情報) のログ記録を許可できます。次のコード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4df4-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 <span data-ttu-id="f4df4-126">アプリケーションを配置するユーザーが App.config ファイルか Web.config ファイルのいずれかで `logKnownPii` 属性を使用することで 、PII ログを可能にする方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f4df4-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="f4df4-127">両方の設定が `true` の場合にのみ、PII はログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="f4df4-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="f4df4-128">2 種類のスイッチを組み合わせることで、各アプリケーションで既知の PII のログを柔軟に記録できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f4df4-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="f4df4-129">構成ファイルで 2 種類以上のカスタム ソースを指定しても、最初のソースの属性のみが読み込まれることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f4df4-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="f4df4-130">他の属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="f4df4-130">The others are ignored.</span></span> <span data-ttu-id="f4df4-131">つまり、2 番目以降の App.config ファイルでは、PII はいずれのソースでもログに記録されなくなります。これは 2 番目のソースで PII のログ記録を明示的に有効にした場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="f4df4-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="false">  
        <listeners>  
           <add name="messages"  
                type="System.Diagnostics.XmlWriterTraceListener"  
                initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
      <source name="System.ServiceModel"
         logKnownPii="true">  
         <listeners>  
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="f4df4-132">`<machineSettings enableLoggingKnownPii="Boolean"/>` の要素が Machine.config ファイルに含まれていない場合、システムは <xref:System.Configuration.ConfigurationErrorsException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="f4df4-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="f4df4-133">変更点はアプリケーションが開始されるか、再起動されるまで、反映されません。</span><span class="sxs-lookup"><span data-stu-id="f4df4-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="f4df4-134">両方の属性も `true` に設定されている場合は、イベントは開始時にログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="f4df4-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="f4df4-135">また、`logKnownPii` が `true` に設定され、`enableLoggingKnownPii` が `false` に設定されている場合にも、イベントはログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="f4df4-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="f4df4-136">PII のログ記録の詳細については、「 [Pii Security Lockdown](../../samples/pii-security-lockdown.md) sample」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4df4-136">For more information on PII logging, see [PII Security Lockdown](../../samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="f4df4-137">コンピューターの管理者およびアプリケーションを配置するユーザーは、これらの 2 種類のスイッチを使用する場合に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4df4-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="f4df4-138">PII のログ記録が有効になっている場合は、セキュリティ キーと PII がログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="f4df4-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="f4df4-139">ログ記録を無効にしても、機密情報およびアプリケーション固有のデータは、依然としてメッセージのヘッダーと本体に記録されています。</span><span class="sxs-lookup"><span data-stu-id="f4df4-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="f4df4-140">プライバシーの詳細および PII の公開を防止する方法については、「[ユーザーのプライバシー](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4df4-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="f4df4-141">また、接続が確立されるたび (接続指向トランスポートの場合)、またはメッセージが送信されるたび (それ以外の場合) に、メッセージ送信者の IP アドレスが記録されます。</span><span class="sxs-lookup"><span data-stu-id="f4df4-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="f4df4-142">これは、送信者の同意を得ずに行われます。</span><span class="sxs-lookup"><span data-stu-id="f4df4-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="f4df4-143">ただし、このログ記録は Information レベルまたは Verbose レベルだけで実行されます。これらのトレース レベルは既定ではありません。また、ライブ デバッグを行う場合を除き、運用環境ではお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="f4df4-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4df4-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4df4-144">See also</span></span>

- [<span data-ttu-id="f4df4-145">トレース</span><span class="sxs-lookup"><span data-stu-id="f4df4-145">Tracing</span></span>](index.md)
