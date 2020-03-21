---
title: WCF トラブルシューティング クイックスタート
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: f85d37fde19767d7fd1e3002776b4816666cc7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183052"
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="a787b-102">WCF トラブルシューティング クイックスタート</span><span class="sxs-lookup"><span data-stu-id="a787b-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="a787b-103">このトピックでは、WCF クライアントと WCF サービスの開発時に生じるさまざまな既知の問題の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a787b-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="a787b-104">発生している問題がこの一覧にない場合は、サービスに対してトレースを構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a787b-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="a787b-105">これにより、トレース ファイル ビューアーで表示し、サービス内で発生することがある例外に関する詳細情報を取得できるトレース ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a787b-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="a787b-106">トレースの構成の詳細については、「 [Configuring Tracing](./diagnostics/tracing/configuring-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787b-106">For more information on configuring tracing, see: [Configuring Tracing](./diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="a787b-107">トレース ファイル ビューアーの詳細については、「 [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787b-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1. [<span data-ttu-id="a787b-108">Windows 7 と IIS のインストール後に WCF サービスを参照しようとすると、"HTTP エラー 404.3 - Not Found" というエラー メッセージが表示されます</span><span class="sxs-lookup"><span data-stu-id="a787b-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](#bkmk_0)  
  
     <span data-ttu-id="a787b-109">HTTP エラー 404.3 - Not Found 拡張構成により、要求しているページは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a787b-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="a787b-110">ページがスクリプトの場合は、ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="a787b-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="a787b-111">ファイルをダウンロードする場合は、MIME マップを追加します。</span><span class="sxs-lookup"><span data-stu-id="a787b-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="a787b-112">エラーの詳細: InformationModule StaticFileModule。</span><span class="sxs-lookup"><span data-stu-id="a787b-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2. [<span data-ttu-id="a787b-113">クライアントが最初の要求の後しばらくアイドル状態にある場合、2 番目の要求で MessageSecurityException を受け取ることがあります。どうしたんですか。</span><span class="sxs-lookup"><span data-stu-id="a787b-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](#BKMK_q1)  
  
3. [<span data-ttu-id="a787b-114">約 10 人のクライアントがやり取りした後、新しいクライアントを拒否するサービスが開始されます。どうしたんですか。</span><span class="sxs-lookup"><span data-stu-id="a787b-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](#BKMK_q2)  
  
4. [<span data-ttu-id="a787b-115">WCF アプリケーションの構成ファイル以外の場所からサービス構成を読み込むことはできますか。</span><span class="sxs-lookup"><span data-stu-id="a787b-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](#BKMK_q3)  
  
5. [<span data-ttu-id="a787b-116">サービスとクライアントは素晴らしい仕事をしていますが、クライアントが別のコンピュータにあるときに動作させることはできませんか?どうしたんですか。</span><span class="sxs-lookup"><span data-stu-id="a787b-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](#BKMK_q4)  
  
6. [<span data-ttu-id="a787b-117">型が例外である場合に\<> FaultException 例外をスローすると、汎用型ではなく、クライアントで常に一般的な FaultException 型が表示されます。どうしたんですか。</span><span class="sxs-lookup"><span data-stu-id="a787b-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](#BKMK_q5)  
  
7. [<span data-ttu-id="a787b-118">一方向および要求応答操作は、応答にデータが含まれなかった場合にほぼ同じ速度で戻るようです。どうしたんですか。</span><span class="sxs-lookup"><span data-stu-id="a787b-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](#BKMK_q6)  
  
8. [<span data-ttu-id="a787b-119">私はサービスでX.509証明書を使用しており、System.Security.Cryptography.CryptographicExceptionを取得します。どうしたんですか。</span><span class="sxs-lookup"><span data-stu-id="a787b-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](#BKMK_q77)  
  
9. [<span data-ttu-id="a787b-120">操作の最初のパラメーターを大文字から小文字に変更しました。今、私のクライアントは例外をスローします。どうしたんですか。</span><span class="sxs-lookup"><span data-stu-id="a787b-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](#BKMK_q88)  
  
10. [<span data-ttu-id="a787b-121">私はトレースツールの1つを使用していて、エンドポイントNotFoundExceptionを取得します。どうしたんですか。</span><span class="sxs-lookup"><span data-stu-id="a787b-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](#BKMK_q99)  
  
11. [<span data-ttu-id="a787b-122">WCF SOAP アプリケーションから WCF Web HTTP アプリケーションを呼び出すと、サービスから "405 メソッドは許可されていません" というエラーが返されます</span><span class="sxs-lookup"><span data-stu-id="a787b-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](#BK_MK99)  
  
 [<span data-ttu-id="a787b-123">ベースアドレスとは何ですか?エンドポイント アドレスとの関係を教えてください。</span><span class="sxs-lookup"><span data-stu-id="a787b-123">What is the base address? How does it relate to an endpoint address?</span></span>](#BKMK_q10)  
  
<a name="bkmk_0"></a>
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="a787b-124">Windows 7 と IIS のインストール後に WCF サービスを参照しようとすると、"HTTP エラー 404.3 - Not Found" というエラー メッセージが表示されます</span><span class="sxs-lookup"><span data-stu-id="a787b-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="a787b-125">エラー メッセージの全文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a787b-125">The full error message is:</span></span>  
  
 <span data-ttu-id="a787b-126">HTTP エラー 404.3 - Not Found 拡張構成により、要求しているページは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a787b-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="a787b-127">ページがスクリプトの場合は、ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="a787b-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="a787b-128">ファイルをダウンロードする場合は、MIME マップを追加します。</span><span class="sxs-lookup"><span data-stu-id="a787b-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="a787b-129">エラーの詳細: InformationModule StaticFileModule。</span><span class="sxs-lookup"><span data-stu-id="a787b-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="a787b-130">このエラー メッセージは、コントロール パネルで [Windows 通信財団の HTTP ライセンス認証] が明示的に設定されていない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a787b-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="a787b-131">これをコントロール パネルに移動するには、ウィンドウの左下隅にある [プログラム] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a787b-131">To set this go to the Control Panel, click Programs in the lower left-hand corner of the window.</span></span> <span data-ttu-id="a787b-132">[Windows の機能の有効化または無効化] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a787b-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="a787b-133">[Microsoft .NET Framework 3.5.1] を展開し、[Windows Communication Foundation HTTP Activation] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a787b-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="a787b-134">最初の要求の後でクライアントがしばらくアイドル状態になった場合、2 番目の要求で MessageSecurityException を受け取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="a787b-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="a787b-135">状況</span><span class="sxs-lookup"><span data-stu-id="a787b-135">What is happening?</span></span>  
 <span data-ttu-id="a787b-136">2 番目の要求は、主に次の 2 つの理由から失敗する可能性があります。(1) セッションがタイムアウトした。(2) サービスをホストしている Web サーバーがリサイクルされている。</span><span class="sxs-lookup"><span data-stu-id="a787b-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="a787b-137">最初のケースでは、セッションはサービスがタイムアウトするまで有効です。サービスのバインディング (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>) で指定された時間内に、サービスがクライアントからの要求を受信しない場合、サービスはセキュリティ セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="a787b-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="a787b-138">それ以降のクライアント メッセージでは、 <xref:System.ServiceModel.Security.MessageSecurityException>が発生します。</span><span class="sxs-lookup"><span data-stu-id="a787b-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="a787b-139">クライアントは、セキュリティで保護されたセッションをサービスとの間に再度確立して、後続のメッセージを送信するか、ステートフルなセキュリティ コンテキスト トークンを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="a787b-140">また、ステートフルなセキュリティ コンテキスト トークンによって、セキュリティで保護されたセッションは、再利用される Web サーバーで存続することができます。</span><span class="sxs-lookup"><span data-stu-id="a787b-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> <span data-ttu-id="a787b-141">セキュリティで保護されたセッションでステートフル セキュリティ コンテキスト トークンを使用する方法の詳細については、「[方法 : セキュリティで保護されたセッションのセキュリティ コンテキスト トークンを作成する](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787b-141">For more information about using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="a787b-142">また、セキュリティで保護されたセッションは無効にできます。</span><span class="sxs-lookup"><span data-stu-id="a787b-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="a787b-143">[ \<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md)バインドを使用する場合は、セキュリティ`establishSecurityContext`で保護`false`されたセッションを無効にするプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="a787b-143">When you use the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="a787b-144">その他のバインディングでセキュリティで保護されたセッションを無効にするには、カスタム バインディングを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="a787b-145">カスタム バインディングの作成の詳細については、「 [How to: Create a Custom Binding Using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787b-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="a787b-146">このオプションを適用する前に、アプリケーションのセキュリティ要件を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="a787b-147">サービスと対話しているクライアントの数が約 10 個になると、サービスが新しいクライアントを拒否し始めます。</span><span class="sxs-lookup"><span data-stu-id="a787b-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="a787b-148">状況</span><span class="sxs-lookup"><span data-stu-id="a787b-148">What is happening?</span></span>  
 <span data-ttu-id="a787b-149">既定では、サービスは、10 個の同時セッションだけをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="a787b-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="a787b-150">したがって、サービス バインディングでセッションを使用する場合、サービスは 10 個に到達するまで新しいクライアント接続を受け入れますが、その数に到達した後は、現在実行中のセッションの 1 つが終了するまで新しいクライアント接続を拒否します。</span><span class="sxs-lookup"><span data-stu-id="a787b-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="a787b-151">いくつかの方法で、より多くのクライアントをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="a787b-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="a787b-152">サービスにセッションが必要ない場合、セッションの多いバインディングを使用しないでください</span><span class="sxs-lookup"><span data-stu-id="a787b-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="a787b-153">(詳細については、「[セッションの使用](using-sessions.md)」を参照してください)。もう 1 つの方法は、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>プロパティの値を自分の状況に応じた数値に変更することで、セッションの制限を増やします。</span><span class="sxs-lookup"><span data-stu-id="a787b-153">(For more information, see [Using Sessions](using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="a787b-154">WCF アプリケーションの構成ファイル以外の場所からサービス構成を読み込むことはできますか。</span><span class="sxs-lookup"><span data-stu-id="a787b-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="a787b-155">できます。ただし、 <xref:System.ServiceModel.ServiceHost> メソッドをオーバーライドするカスタムの <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> クラスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="a787b-156">そのメソッドでは、ベースを呼び出して最初に構成を読み込むことができますが (標準の構成情報も読み込む場合)、構成読み込みシステム全体を置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="a787b-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="a787b-157">アプリケーション構成ファイルとは異なる構成ファイルから構成をロードする場合は、自分で構成ファイルを解析し、構成をロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-157">If you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="a787b-158"><xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> メソッドをオーバーライドし、エンドポイントを直接構成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="a787b-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="a787b-159">サービスとクライアントの動作に問題はないのですが、クライアントが別のコンピューター上にあるときにサービスとクライアントがうまく動作しません。</span><span class="sxs-lookup"><span data-stu-id="a787b-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="a787b-160">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a787b-160">What’s happening?</span></span>  
 <span data-ttu-id="a787b-161">例外によっては、次のようないくつかの問題が存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-161">Depending upon the exception, there may be several issues:</span></span>  
  
- <span data-ttu-id="a787b-162">場合によっては、クライアントのエンドポイント アドレスを "localhost" ではなくホスト名に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
- <span data-ttu-id="a787b-163">場合によっては、アプリケーションに対してポートを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-163">You might need to open the port to the application.</span></span> <span data-ttu-id="a787b-164">詳細については、SDK サンプルから「 [Firewall Instructions](./samples/firewall-instructions.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787b-164">For details, see [Firewall Instructions](./samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
- <span data-ttu-id="a787b-165">その他の問題については、サンプルトピック[「Windows コミュニケーション ファウンデーション のサンプルの実行](./samples/running-the-samples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787b-165">For other possible issues, see the samples topic [Running the Windows Communication Foundation Samples](./samples/running-the-samples.md).</span></span>  
  
- <span data-ttu-id="a787b-166">クライアントが Windows 資格情報を使用し、例外が <xref:System.ServiceModel.Security.SecurityNegotiationException>の場合、次のように Kerberos を設定します。</span><span class="sxs-lookup"><span data-stu-id="a787b-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1. <span data-ttu-id="a787b-167">クライアントの App.config ファイルのエンドポイント要素に ID 資格情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="a787b-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
        ```xml
        <endpoint
          address="http://MyServer:8000/MyService/"
          binding="wsHttpBinding"
          bindingConfiguration="WSHttpBinding_IServiceExample"
          contract="IServiceExample"
          behaviorConfiguration="ClientCredBehavior"
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2. <span data-ttu-id="a787b-168">System または NetworkService アカウントで自己ホスト型サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="a787b-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="a787b-169">次のコマンドを実行すると、System アカウントでコマンド ウィンドウを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a787b-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. <span data-ttu-id="a787b-170">既定でサービス プリンシパル名 (SPN) アカウントを使用するインターネット インフォメーション サービス (IIS) でのサービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="a787b-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4. <span data-ttu-id="a787b-171">SetSPN を使用してドメインに新しい SPN を登録します。</span><span class="sxs-lookup"><span data-stu-id="a787b-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="a787b-172">これを行うには、ドメイン管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-172">You need to be a domain administrator in order to do this.</span></span>  
  
 <span data-ttu-id="a787b-173">Kerberos プロトコルの詳細については[、「WCF で使用されるセキュリティの概念](./feature-details/security-concepts-used-in-wcf.md)」および「次の項目を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787b-173">For more information about the Kerberos protocol, see [Security Concepts Used in WCF](./feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
- [<span data-ttu-id="a787b-174">Windows 認証エラーのデバッグ</span><span class="sxs-lookup"><span data-stu-id="a787b-174">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)  
  
- <span data-ttu-id="a787b-175">[Http.sys を使用した Kerberos サービス プリンシパル名の登録](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="a787b-175">[Registering Kerberos Service Principal Names by Using Http.sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span></span>  
  
- <span data-ttu-id="a787b-176">[Kerberos の説明](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))</span><span class="sxs-lookup"><span data-stu-id="a787b-176">[Kerberos Explained](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))</span></span>  
  
<a name="BKMK_q5"></a>
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="a787b-177">型が例外である場合に\<> FaultException 例外をスローすると、汎用型ではなく、クライアントで常に一般的な FaultException 型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a787b-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="a787b-178">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a787b-178">What’s happening?</span></span>  
 <span data-ttu-id="a787b-179">独自のカスタム エラー データ型を作成し、エラー コントラクトで詳細な型としてその型を宣言することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a787b-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="a787b-180">その理由は、システム指定の例外型を使用すると、次のような状況が起こるためです。</span><span class="sxs-lookup"><span data-stu-id="a787b-180">The reason is that using system-provided exception types:</span></span>  
  
- <span data-ttu-id="a787b-181">サービス指向アプリケーションの長所の 1 つを排除する型依存関係が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a787b-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
- <span data-ttu-id="a787b-182">標準的な方法でシリアル化している例外に依存できません。</span><span class="sxs-lookup"><span data-stu-id="a787b-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="a787b-183"><xref:System.Security.SecurityException>のような例外はまったくシリアル化できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
- <span data-ttu-id="a787b-184">クライアントに内部実装の詳細が公開されます。</span><span class="sxs-lookup"><span data-stu-id="a787b-184">Exposes internal implementation details to clients.</span></span> <span data-ttu-id="a787b-185">詳細については、「[コントラクトおよびサービスでの障害の指定と処理](specifying-and-handling-faults-in-contracts-and-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787b-185">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="a787b-186">ただし、アプリケーションをデバッグしている場合、 <xref:System.ServiceModel.Description.ServiceDebugBehavior> クラスを使用することによって例外情報をシリアル化して、その情報をクライアントに返すことができます。</span><span class="sxs-lookup"><span data-stu-id="a787b-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="a787b-187">応答にデータがない場合、一方向操作と要求/応答操作が戻る速度がほぼ同じになるようです。</span><span class="sxs-lookup"><span data-stu-id="a787b-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="a787b-188">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a787b-188">What's happening?</span></span>  
 <span data-ttu-id="a787b-189">操作を一方向に指定すると、操作コントラクトは入力メッセージを受け入れるだけで、出力メッセージを返しません。</span><span class="sxs-lookup"><span data-stu-id="a787b-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="a787b-190">WCF では、すべてのクライアント呼び出しは、送信データがワイヤに書き込まれたか、例外がスローされたときに返されます。</span><span class="sxs-lookup"><span data-stu-id="a787b-190">In WCF, all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="a787b-191">一方向操作は同様に動作し、この操作では、サービスが見つからない場合は例外をスローし、サービスがネットワークからのデータの受け入れ準備を完了していない場合はブロックできます。</span><span class="sxs-lookup"><span data-stu-id="a787b-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="a787b-192">通常、WCF では、一方向の呼び出しが要求応答よりも迅速にクライアントに返されます。しかし、ネットワーク経由で送信データの送信速度が低下する場合、一方向の操作と要求/応答操作が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="a787b-192">Typically in WCF, this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> <span data-ttu-id="a787b-193">詳細については、「[一方向サービス](./feature-details/one-way-services.md)と[WCF クライアントを使用したサービスへのアクセス](./feature-details/accessing-services-using-a-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787b-193">For more information, see [One-Way Services](./feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](./feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="a787b-194">サービスで X.509 証明書を使用していますが、System.Security.Cryptography.CryptographicException を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a787b-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="a787b-195">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a787b-195">What’s happening?</span></span>  
 <span data-ttu-id="a787b-196">この例外は通常、IIS ワーカー プロセスの実行に使用しているユーザー アカウントを変更すると発生します。</span><span class="sxs-lookup"><span data-stu-id="a787b-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="a787b-197">たとえば、Windows XP で、Aspnet_wp.exe を実行する既定のユーザー アカウントを ASPNET からカスタム ユーザー アカウントに変更すると、このエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a787b-197">For example, in Windows XP, if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="a787b-198">秘密キーを使用している場合、そのキーを使用するプロセスには、そのキーを格納しているファイルにアクセスするためのアクセス許可が必要になります。</span><span class="sxs-lookup"><span data-stu-id="a787b-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="a787b-199">この場合、秘密キーを格納しているファイルについて、プロセスのアカウントに読み取りアクセス権を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="a787b-200">たとえば、IIS ワーカー プロセスを Bob というアカウントで実行している場合、秘密キーを格納しているファイルへの読み取りアクセス権を Bob に与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 <span data-ttu-id="a787b-201">特定の X.509 証明書の秘密キーを含むファイルへの正しいユーザー アカウント アクセスを付与する方法の詳細については、「[方法: X.509 証明書を WCF からアクセス可能にする](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787b-201">For more information about how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="a787b-202">操作の最初のパラメーターを大文字から小文字に変更したら、クライアントが例外をスローするようになりました。</span><span class="sxs-lookup"><span data-stu-id="a787b-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="a787b-203">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a787b-203">What's happening?</span></span>  
 <span data-ttu-id="a787b-204">操作シグネチャのパラメーター名の値はコントラクトの一部であり、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="a787b-204">The values of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="a787b-205">ローカル パラメーター名と、クライアント アプリケーションの操作を記述するメタデータを区別する必要がある場合は、 <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="a787b-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="a787b-206">トレース ツールの 1 つを使用していますが、EndpointNotFoundException を受け取りました。</span><span class="sxs-lookup"><span data-stu-id="a787b-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="a787b-207">どうしてでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a787b-207">What’s happening?</span></span>  
 <span data-ttu-id="a787b-208">システム提供の WCF トレース メカニズムではないトレース ツールを使用していて、アドレス フィルターの<xref:System.ServiceModel.EndpointNotFoundException>不一致があったことを示す を受け取る場合は、<xref:System.ServiceModel.Description.ClientViaBehavior>クラスを使用してトレース ユーティリティにメッセージを送信し、ユーティリティでサービス アドレスにそれらのメッセージをリダイレクトする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787b-208">If you are using a tracing tool that is not the system-provided WCF tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="a787b-209"><xref:System.ServiceModel.Description.ClientViaBehavior> クラスは、 `Via` アドレス指定ヘッダーを変更して、 `To` アドレス指定ヘッダーで示されている最終受信者とは別に、次のネットワーク アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a787b-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="a787b-210">ただし、このとき、エンドポイント アドレスは `To` 値の設定に使用されるので変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="a787b-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="a787b-211">次のコード例は、クライアント構成ファイルの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="a787b-211">The following code example shows an example client configuration file.</span></span>  
  
```xml
<endpoint
  address="http://localhost:8000/MyServer/"  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"
  contract="IMyContract"
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="a787b-212">ベース アドレスについて教えてください。</span><span class="sxs-lookup"><span data-stu-id="a787b-212">What is the base address?</span></span> <span data-ttu-id="a787b-213">エンドポイント アドレスとどのように関連していますか。</span><span class="sxs-lookup"><span data-stu-id="a787b-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="a787b-214">ベース アドレスとは、 <xref:System.ServiceModel.ServiceHost> クラスのルート アドレスです。</span><span class="sxs-lookup"><span data-stu-id="a787b-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="a787b-215">既定では、 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスをサービス構成に追加する場合、ホストが発行するすべてのエンドポイントの Web サービス記述言語 (WSDL) は、HTTP ベース アドレスから取得され、それにメタデータ動作に提供される相対アドレスと "?wsdl" が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a787b-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="a787b-216">ASP.NETと IIS に精通している場合、ベース アドレスは仮想ディレクトリと同じです。</span><span class="sxs-lookup"><span data-stu-id="a787b-216">If you are familiar with ASP.NET and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="a787b-217">NetTcpBinding を使用したサービス エンドポイントと MEX エンドポイント間でのポートの共有</span><span class="sxs-lookup"><span data-stu-id="a787b-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="a787b-218">サービスのベース アドレスとして net.tcp://MyServer:8080/MyService を指定して次のエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="a787b-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="a787b-219">次の構成スニペットに示すように、NetTcpBinding 設定の 1 つを変更するとします。</span><span class="sxs-lookup"><span data-stu-id="a787b-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="a787b-220">"ハンドルされない例外: System.ServiceModel.AddressAlreadyInUseException: IP エンドポイント 0.0.0.0:9000 には既にリスナーがあります。" というエラーが表示されます。このエラーは、次の構成スニペットに示すように、ポートが異なる完全修飾 URL を MEX エンドポイントに対して指定することで回避できます。</span><span class="sxs-lookup"><span data-stu-id="a787b-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="a787b-221">WCF SOAP アプリケーションから WCF Web HTTP アプリケーションを呼び出すと、サービスから "405 メソッドは許可されていません" というエラーが返されます</span><span class="sxs-lookup"><span data-stu-id="a787b-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="a787b-222">WCF <xref:System.ServiceModel.WebHttpBinding> Web HTTP アプリケーション ( および<xref:System.ServiceModel.Description.WebHttpBehavior>を使用するサービス ) を WCF サービス``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.``から呼び出すと、次の例外<xref:System.ServiceModel.OperationContext><xref:System.ServiceModel.OperationContext>が生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a787b-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="a787b-223">この問題を解決するには、WCF <xref:System.ServiceModel.OperationContextScope> Web HTTP サービス操作内で を作成します。</span><span class="sxs-lookup"><span data-stu-id="a787b-223">To solve this problem, create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="a787b-224">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a787b-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a787b-225">関連項目</span><span class="sxs-lookup"><span data-stu-id="a787b-225">See also</span></span>

- [<span data-ttu-id="a787b-226">Windows 認証エラーのデバッグ</span><span class="sxs-lookup"><span data-stu-id="a787b-226">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)
